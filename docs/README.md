# Project documentation

| File | Description |
| --- | --- |
| [Project poster](poster/venus-flytrap-recording-playback-poster.jpeg) | Original Georgia Tech senior design poster: project motivation, analog circuitry, digital design, validation figures, instructions, and team credits. |
| [Final presentation](presentation/final-presentation.pptx) | Original 14-slide presentation, including the original speaker notes and embedded media. |
| [Implementation notes](implementation-notes.md) | Hardware/software interface, firmware dependencies, and limitations found while inspecting the final source. |
| [File map](file-map.csv) | Every file present before organization, its new location, and SHA-256 hashes. |
| [App preview](images/hashirama-app.png) | Existing preview extracted from `Hashirama.mlapp`; the app file itself is unchanged. |

Watch the [project explanation video](https://youtu.be/vUATFXuZiM0), published as **ECE4723 The Venus Flytrap Recording and Playback Device** by Sangeon Jeon (5:19).

The README's technical description and credits are grounded in the local poster, presentation, and final source. The video's title and duration were verified from YouTube metadata; its full transcript was not available during organization.

## Preservation and file names

Photos and videos were named from their visible contents. Video classification used sampled frames from the start, middle, and end of each clip, rather than a full frame-by-frame review. Sequence numbers distinguish similar views and do not imply distinct experimental trials.

The final application, firmware, historical code, datasets, presentation, and original media retain their original bytes. The file map records both the old and new paths so existing notes can be reconciled after the reorganization. Legacy development filenames were retained inside the archive to preserve experimental provenance.

Finder and MATLAB metadata are preserved separately in `archive/repository-metadata/`. Those files were recovered from Git after an initial metadata cleanup. Two Finder files (`.DS_Store` and `Results/.DS_Store`) had pre-existing uncommitted changes, so their archived copies are the committed versions; the file map records the differing hashes. The other 17 metadata files match the pre-organization copies.
