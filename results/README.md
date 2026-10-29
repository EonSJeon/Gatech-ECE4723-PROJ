# Results

This folder contains recorded device data and digital verification evidence. Earlier development/reference recordings live separately in [archive/development/Data/](../archive/development/Data/).

## Measured data

| File | Contents |
| --- | --- |
| [act1.csv](measured-data/act1.csv) | Recorded input trace: 3,090 rows with `Time` and `Volt_In`. |
| [imp1.csv](measured-data/imp1.csv) | Pulse/response recording: 106 rows with `Time`, `Volt_In`, and `Volt_Out`. |
| [real_imp1.csv](measured-data/real_imp1.csv) | Pulse/response recording: 107 rows with the same three columns. The historical `improvise.m` script references this basename. |
| [impulse-response-input-output.jpg](measured-data/impulse-response-input-output.jpg) | Input and response displayed on separate axes; originally `real_imp.jpg`. |
| [impulse-response-overlay.jpg](measured-data/impulse-response-overlay.jpg) | Input and response displayed together; originally `real_imp_combined.jpg`. |

Time is in milliseconds and voltages are in millivolts at the device interface. The CSV timestamps retain their original origins. Data files retain their original names and bytes; descriptive figure names are recorded in the [file map](../docs/file-map.csv).

## Digital system verification

[digital-system-verification/](digital-system-verification/) contains ten frequency sets, from 10 Hz through 100 Hz in 10 Hz increments. Each set includes one CSV and two original oscilloscope screenshots:

```text
sine-010hz.csv
sine-010hz-oscilloscope-01.bmp
sine-010hz-oscilloscope-02.bmp
...
sine-100hz.csv
sine-100hz-oscilloscope-01.bmp
sine-100hz-oscilloscope-02.bmp
```

The numbered captures preserve the ordering of the original `10Hz1.bmp` / `10Hz2.bmp` style names. They identify paired views, not repeatability statistics. Files were renamed without changing the data or image encoding.

Analog frequency-response figures and the original validation discussion are in the [project poster](../docs/poster/venus-flytrap-recording-playback-poster.jpeg). See [implementation notes](../docs/implementation-notes.md) for the distinction between design targets, saved evidence, and current firmware limitations.
