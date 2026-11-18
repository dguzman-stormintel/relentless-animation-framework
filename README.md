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

## Detailed workflow

### Prepare your pages

Each page is one image containing a rectangular grid of frames, not a document page or a video. Use image formats your browser can decode. Keep frame dimensions and the grid consistent, and maintain character and background continuity across pages. Select all pages together: selecting a new set replaces the current set. File names are sorted naturally, so page-2 comes before page-10.

Manual mode divides every page evenly using the same column and row settings. Auto mode looks for solid dark or light horizontal and vertical separators on each page; when detection fails it uses the manual column and row values. Auto detection may still find the wrong grid: always inspect the green cut lines. Trim removes pixels from each frame edge; auto-detected frames also receive a small inset. Choose row order for left-to-right then down, or column order for top-to-bottom then across.

### Playback and editing

Use the thumbnail strip or slider to select a frame. Start here and End here define the included range; All frames clears it. Forward, Reverse, and Ping-pong determine playback and export order. The speed control sets frames per second. Move, Duplicate, and Delete act on the current frame. Undo reverses edits and Reset all restores the original frame sequence. Any frame edit resets the playback range to all frames; setting changes rebuild the sequence and clear edit history.

### Export

The export uses the current edited sequence, range, direction, frame rate, and repeat count. Original and 2x set output dimensions; dimensions are rounded down to even pixel values. MP4 uses the device's WebCodecs H.264 encoder and the bundled MP4 muxer. WebM uses canvas recording and MediaRecorder, so recording takes approximately the sequence duration. Preview the result and verify the download on your device. Exports contain video frames only; the current interface does not add audio or captions.

For forward playback, approximate duration in seconds = number of selected frames × repeat count ÷ frames per second. Ping-pong adds the reverse journey, excluding duplicated endpoints, so its frame count differs.

## Troubleshooting

- **Wrong frame boundaries or order:** inspect the page previews; choose Manual and set the right dimensions and frame order. Adjust trim carefully.
- **Some images are missing:** choose image files supported by your browser, then reselect the complete set. Files that cannot be decoded are skipped.
- **MP4 unavailable:** H.264 support depends on the browser, device, and frame dimensions. Try WebM or another compatible browser. WebCodecs may require a secure context such as HTTPS or localhost.
- **WebM unavailable:** the browser must support MediaRecorder and canvas capture with a supported WebM codec. Try another compatible browser.
- **Black bars or cropped edges:** similarly sized frames are center-cropped to a shared size; differing frame sizes are scaled to fit with black bars. Use consistently sized source frames.
- **Slow export or memory errors:** use smaller source pages, original export size, fewer frames, or fewer repeats. Keep the page active while recording WebM.
- **Changes disappeared:** session edits are not saved as a reusable project. Export before closing and retain the original pages.

## Technical notes and verification

The repository currently contains one self-contained HTML file with inline styles, application JavaScript, and a bundled MP4 muxer. No installation, build step, API key, image-generation model, backend server, or automated tests are present in the repository. Image selection and frame processing are implemented in the browser; this code review found no fetch call in the HTML. The optional footer links open external websites. An optional host download integration is attempted when available; otherwise the browser download mechanism is used.

Documentation describes the code inspected in this repository; it is not a claim that every browser, codec, device, or export path has been tested. Before redistribution, identify the exact bundled muxer version and its license and retain required notices. The repository owner has not specified a project license; no license is granted by this README.
