# Development archive

The final product is [`Hashirama.mlapp`](../Hashirama.mlapp) plus [`Senju.cpp`](../Senju.cpp) at the repository root. This archive preserves the supporting development history.

| Location | Contents |
| --- | --- |
| [development/](development/) | Original contents of `bin/`: MATLAB prototypes, utility scripts, waveform generators, intermediate data, figures, and backups. |
| [development/RTOS experiment/](development/RTOS%20experiment/) | Earlier RTOS communication experiment and matching host/device code. |
| [development/Data/dummy data/](development/Data/dummy%20data/) | Development and synthetic/test recordings; original working names are retained. |
| [development/Data/not with our device/](development/Data/not%20with%20our%20device/) | Reference recordings, filtered versions, and figures originally labeled as not collected with this device. |
| [backups/](backups/) | Autosave previously stored alongside measured results. The original `playback.asv` remains under `development/`. |
| [repository-metadata/](repository-metadata/) | Preserved Git versions of historical Finder/MATLAB metadata, with original relative paths. |

All code and experimental/reference files retain their original bytes. Internal development filenames and directory names are intentionally retained to preserve provenance. These scripts include historical hardcoded ports, paths, and experimental assumptions; they are not maintained application entry points.

For example, `development/improvise.m` reads `real_imp1.csv` relative to MATLAB's current directory. To inspect that historical script with its associated measurement, use `results/measured-data/` as the current directory and run the script by its full path. Other scripts may need their original working-directory context.

The [file map](../docs/file-map.csv) records every original location and its current location. The [preservation notes](../docs/README.md#preservation-and-file-names) explain the metadata restoration exception for two pre-existing modified Finder files.
