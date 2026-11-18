# Relentless Animation Framework

**From still images to motion pictures.**

Created by Daniel Guzman. Relentless turns image pages containing sequential frames into a playable animation and exports a movie in a compatible browser.

## Get started

1. Download [Relentless Animation Framework.html](Relentless%20Animation%20Framework.html) and open it in a browser.
2. Select one or more image pages containing a grid of sequential frames. Pages play in filename order; use names such as page-01.png through page-05.png.
3. Use Auto-detect for frames separated by solid lines, or choose Manual and enter the grid's columns and rows. Choose the frame order and adjust trim if needed.
4. Preview the sequence, change the frame rate, and use the frame editing and playback controls.
5. Choose MP4 or WebM and export. The app displays a preview and asks the browser to save the movie.

For five pages of 12 frames each, use a consistent 4-column by 3-row grid, name the pages in story order, choose Manual, and set columns to 4 and rows to 3. At 12 frames per second, 60 frames play for approximately five seconds before repeats.

## Capabilities

- Load multiple image pages, detect or manually specify frame grids, and inspect cut lines.
- Play forward, reverse, or ping-pong; set a playback range and frame rate.
- Move, duplicate, delete, undo, or reset frames within the current session.
- Export MP4 (H.264) when the browser supports WebCodecs and a supported encoder, or WebM when MediaRecorder and canvas recording are supported. WebM records in real time.

## Important details

This is a self-contained browser application, not an image generator: create or supply the sequential frame sheets first. It does not generate intermediate frames. For a continuous story, the images need consistent characters, settings, and progression.

Edits are in memory and do not alter source images; reloading the page loses the session. Changing grid, order, or trim rebuilds frames and clears edits. Browser, device, codec, and download support vary; try WebM if MP4 is unavailable. Large images or long exports may require substantial device memory.

The HTML includes an MP4 muxer. Review its third-party licensing before redistributing the bundled code; this repository does not currently specify a project license.

## Repository

- Relentless Animation Framework.html — standalone player, editor, and exporter.
- README.md — setup and usage instructions.
