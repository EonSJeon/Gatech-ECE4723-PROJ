# Project documentation

| File | Description |
| --- | --- |
| [Project poster](poster/venus-flytrap-recording-playback-poster.jpeg) | Original Georgia Tech senior design poster: project motivation, analog circuitry, digital design, validation figures, instructions, and team credits. |
| [Final presentation](presentation/final-presentation.pptx) | Original 14-slide presentation, including the original speaker notes and embedded media. |
| [Final presentation video](../media/videos/presentations/final-project-presentation-and-demo.mp4) | Complete 5:19 presentation and demonstration video, retained in its original MP4 encoding. |
| [Implementation notes](implementation-notes.md) | Hardware/software interface, firmware dependencies, and limitations found while inspecting the final source. |
| [File map](file-map.csv) | Original file locations, current locations, SHA-256 hashes, and explicit records of removed generated metadata and duplicate excerpts. |
| [App preview](images/hashirama-app.png) | Existing preview extracted from `Hashirama.mlapp`; the app file itself is unchanged. |

Watch the [project explanation video](https://youtu.be/vUATFXuZiM0), published as **ECE4723 The Venus Flytrap Recording and Playback Device** by Sangeon Jeon (5:19).

The README's technical description and credits are grounded in the local poster, presentation, and final source. The video's title and duration were verified from YouTube metadata; its full transcript was not available during organization.

## Preservation and file names

Photos and videos were named from their visible contents. Video classification used sampled frames from the start, middle, and end of each clip, rather than a full frame-by-frame review. Sequence numbers distinguish similar views and do not imply distinct experimental trials.

The final application, firmware, historical code, datasets, presentation, and original media retain their original bytes. The file map records both the old and new paths so existing notes can be reconciled after the reorganization. Legacy development filenames were retained inside the archive to preserve experimental provenance.

Generated Finder and MATLAB metadata (`.DS_Store` and `.MATLABDriveTag`) is intentionally removed and ignored. The former metadata-only archive and its directories are no longer retained. In the file map, these 19 entries use `remove-generated-metadata` with empty current-path and current-hash fields; their original hashes remain as a record of the cleanup. Project code, data, presentations, and media are outside this metadata cleanup.

The partial presentation recording `Record_2024_05_30_11_57_47_740.mp4` was removed after its opening slides and audio were matched to the complete `Senior Design Project Demo.mp4`. Its file-map entry uses `remove-duplicate-presentation-excerpt`; the complete video is retained as `media/videos/presentations/final-project-presentation-and-demo.mp4` with its original SHA-256 hash.
