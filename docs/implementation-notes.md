# Implementation notes

These notes describe the preserved final source. Repository organization does not change `Hashirama.mlapp`, `Senju.cpp`, or historical development code.

## Runtime and hardware

- `Hashirama.mlapp` contains its MATLAB class, private methods, UI construction, and callbacks. Its embedded release metadata identifies MATLAB R2023b.
- The app was checked to construct and close in MATLAB R2026a. No serial device was opened during that check.
- The project poster specifies a Seeeduino XIAO. The firmware expects Arduino-style APIs, board-specific analog resolution support, and the external `CircularBuffer.h` library.
- There is no vendored circular-buffer library, board package, `.ino` wrapper, or board-specific build configuration in this repository. Treat `Senju.cpp` as firmware source to integrate with the matching board toolchain.
- The poster and presentation provide circuit diagrams and context, rather than a complete hardware manufacturing package.

| Firmware setting | Value |
| --- | --- |
| Playback/DAC pin | `A0` |
| Record/ADC pin | `A1` |
| Idle / upload / monitor indicators | `A9` / `A8` / `A7` |
| Debug indicator | `A10` |
| ADC / DAC resolution | 12-bit / 10-bit |
| Device voltage scale | 3300 mV |
| Serial baud rate | 9600 |

## Serial interface

The app and firmware use matching 16-bit command values:

| Command | Value | Purpose |
| --- | --- | --- |
| `SIG_IDLE` | `0x4944` | Enter idle state. |
| `SIG_UPLOAD` | `0x554C` | Receive playback waveform samples. |
| `SIG_MONITOR` | `0x4D4E` | Acquire input and produce playback output. |
| `SIG_IMPULSE` | `0x4950` | Generate a finite pulse and collect its response. |
| `SIG_FLUSH` | `0x464C` | Clear the playback buffer. |

The host sends commands and waveform samples as `uint16`; firmware combines the low byte followed by the high byte. Waveform samples are intended to use the 10-bit output range, 0–1023; the app does not explicitly clamp imported voltages to that range. The device returns ASCII records:

```text
timestamp_ms,input_mV,output_mV;
```

Saved CSVs contain `Time` plus `Volt_In` and/or `Volt_Out`. Device timestamps may retain a nonzero origin; the uploader subtracts the minimum timestamp when loading a file. The import routine detects time columns by `time`, `sec`, or `stamp` and voltage columns by `volt`, `amp`, or `meas` in their names. Use the saved CSV column names above and milliseconds/millivolts for playback.

## Known limitations in the preserved source

| Area | Observation |
| --- | --- |
| Impulse-response transfer | The three impulse buffers have capacity 500, but `impulse()` indexes them in a loop of 10,000 iterations (`PLAYBACK_BUF_SIZE`). The transfer loop exceeds the declared impulse-buffer capacity. |
| Upload capacity | The app uses `MAX_NUM_SAMPLE = 20000`; the firmware playback buffer holds 10,000 samples. The app's duration alert also does not stop the upload. |
| Playback indexing | Monitoring indexes modulo the full buffer capacity, without checking how many waveform samples have actually been uploaded. Recording mode reaches the same firmware monitoring path. |
| Timing | Host resampling and firmware indexing use a nominal 2 ms interval, but the monitor loop includes `delay(5)` and serial output. A 500 Hz sustained acquisition rate is not established by those constants. |
| Time origin | `tSt_ms` is `uint16_t`, although `millis()` produces a longer timestamp. It is set on upload, rather than on entry to monitoring, which can affect playback alignment. |
| Stream parsing | MATLAB parses the currently available serial bytes without preserving an unfinished record between reads, so boundary fragments may be lost. |
| Impulse waiting | The app waits for the first response byte without a timeout in impulse mode. |

The poster's analog bandwidth figures and design goals do not establish the achieved sampling rate of this digital implementation. End-to-end acquisition, playback, and plant response require validation with the original hardware.
