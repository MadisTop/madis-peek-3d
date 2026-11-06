# Madis Peek 3D

[English](README.md) | [简体中文](README.zh-CN.md)

Madis Peek 3D is a Tauri-based desktop application for previewing, inspecting, simplifying, and making lightweight edits to triangular 3D meshes.

Website: <https://madis.top>

## Download

Official desktop packages are published through this repository's [GitHub Releases](https://github.com/MadisTop/madis-peek-3d/releases) and mirrored to [Gitee Releases](https://gitee.com/madis/madis-peek-3d/releases). Use the package list shown on the selected Release page.

Test builds are marked as **Pre-release**. When a Release contains `SHA256SUMS.txt`, verify the downloaded file before installation.

## Features

- Imports OBJ, STL, and GLB 2.0 triangular meshes
- Decodes GLB meshes using `KHR_draco_mesh_compression`
- Smooth orbit, pan, zoom, fit-to-view, native file picker, startup-file opening, and drag-and-drop workflows
- A bilingual Simplified Chinese/English interface that follows the operating-system language by default and can be changed persistently from View → Language
- A View menu that can hide or restore the toolbar, properties panel, and status bar for the current session
- Solid, opacity, wireframe, reference grid, coordinate axes, plus in-viewport 3D bounds and dimension lines
- File name, full path, original file size, vertex count, triangle count, bounding dimensions, and development-mode on-demand render timing
- Coordinate-precision simplification with synchronized comparison views for the original mesh and 0–7 decimal places
- Lightweight mesh editing: move and merge vertices, vertex/edge-midpoint/XYZ-axis snapping, face selection and deletion, degenerate-face cleanup, and single-step undo
- Exports OBJ and binary STL, saves viewport screenshots, and provides a GLB export path that attempts Draco compression
- Custom frameless desktop window with system, light, or dark application themes, with independently selectable viewport backgrounds
- Normal updates can download silently in the background and install on exit; required updates can be checked and installed immediately, with the official download page kept as a fallback

## Format limitations

Madis Peek 3D converts imported content into one editable triangular mesh. Multiple GLB meshes are flattened after applying node world transforms. Basic color is preserved where possible, but textures, detailed materials, animations, skinning, morph targets, cameras, lights, and the original scene hierarchy are not preserved as a lossless round trip.

GLB export depends on the Draco encoder and runtime environment. Encoding errors are reported rather than silently falling back to uncompressed GLB. Do not rely on this application as the only copy of production assets; keep the original model files.

## Shortcuts

| Shortcut               | Action                                                          |
| ---------------------- | --------------------------------------------------------------- |
| `Ctrl/Cmd+O`           | Open a model                                                    |
| `Ctrl/Cmd+S`           | Open the model export panel                                     |
| `Ctrl/Cmd+P`           | Save a viewport screenshot                                      |
| `Ctrl/Cmd+Z`           | Single-step undo / switch between the two latest mesh snapshots |
| `E`                    | Toggle edit mode                                                |
| `F`                    | Fit model to view                                               |
| `R`                    | Reset the camera                                                |
| `G`                    | Toggle the reference grid                                       |
| `A`                    | Toggle the coordinate axes                                      |
| `F5`                   | Clear the current model                                         |
| `Delete` / `Backspace` | Delete the selected triangle in edit mode                       |
| `Esc`                  | Close dialogs or cancel the current vertex drag                 |

`Cmd` means the macOS Command key; Windows and Linux use `Ctrl`.

## Supported platforms

Targets include Windows x64, Linux x64, macOS Intel, and macOS Apple Silicon. Available versions and package formats are listed on the selected Release page.

## Installation safety and privacy

Choose an official package matching your operating system and processor architecture, read the version-specific notices, and verify `SHA256SUMS.txt` when supplied. A matching file name, successful download, or checksum alone does not establish the download source or signing identity.

- Updater Minisign signatures verify update payloads. They are not Windows Authenticode, macOS Developer ID/notarization, or Linux package signatures, and do not guarantee that the operating system will show no security warnings.
- If Windows reports an unknown publisher or SmartScreen warning, or macOS shows a security warning, check the download source and the signing identity displayed by the operating system. Do not globally disable system protection to install the application.
- When a Linux release supplies an OpenPGP public key and full fingerprint, confirm the fingerprint through a trusted channel before verifying the signature. Verification methods for different package formats are not interchangeable.
- For separate channels such as Microsoft Store, check the publisher identity and installation permissions shown by that store.
- Keep original model copies and open only files from trusted sources. Remove local paths, personal information, and sensitive model content before reporting an issue; do not upload private models without authorization.

## Feedback

Report installation or usage problems through this repository's Issues page. Include the operating system, application version, model format, approximate vertex/triangle count, and reproducible steps. Do not attach private or proprietary 3D models unless you are authorized to share them.
