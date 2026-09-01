# Madis Peek 3D

[English](README.md) | [简体中文](README.zh-CN.md)

Madis Peek 3D is a Tauri-based desktop application for previewing, inspecting, simplifying, and making lightweight edits to triangular 3D meshes.

Website: <https://madis.top>

## Download

Official desktop packages are published through this repository's [GitHub Releases](https://github.com/MadisTop/madis-peek-3d/releases) and mirrored to [Gitee Releases](https://gitee.com/madis/madis-peek-3d/releases). During test distribution both repositories may remain private. Always use the package list actually shown on the selected Release page.

Test builds are marked as **Pre-release**. When a Release contains `SHA256SUMS.txt`, verify the downloaded file before installation.

## Features

- Imports OBJ, STL, and GLB 2.0 triangular meshes
- Decodes GLB meshes using `KHR_draco_mesh_compression`
- Smooth orbit, pan, zoom, fit-to-view, native file picker, startup-file opening, and drag-and-drop workflows
- A bilingual Simplified Chinese/English interface that follows the operating-system language by default and can be changed persistently from View → Language
- A View menu that can hide or restore the toolbar, properties panel, and status bar, with local persistence
- Solid, opacity, wireframe, reference grid, coordinate axes, plus in-viewport 3D bounds and dimension lines
- File name, full path, original file size, vertex count, triangle count, bounding dimensions, and on-demand render timing
- Coordinate-precision simplification with synchronized comparison views for the original mesh and 0–7 decimal places
- Lightweight mesh editing: move and merge vertices, vertex/edge-midpoint/XYZ-axis snapping, face selection and deletion, degenerate-face cleanup, and single-step undo
- Exports OBJ and binary STL, saves viewport screenshots, and provides a GLB export path that attempts Draco compression
- Custom frameless desktop window whose application chrome follows the system light/dark theme, with independently selectable viewport backgrounds
- Normal updates can download silently in the background and install on exit; required updates can be checked and installed immediately, with the official download page kept as a fallback

## Format limitations

Madis Peek 3D converts imported content into one editable triangular mesh. Multiple GLB meshes are flattened after applying node world transforms. Basic color is preserved where possible, but textures, detailed materials, animations, skinning, morph targets, cameras, lights, and the original scene hierarchy are not preserved as a lossless round trip.

GLB export with Draco compression still requires continued runtime verification on each target platform. Do not rely on this application as the only copy of production assets; keep the original model files.

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

`Cmd` means the macOS Command key; Windows and Linux use `Ctrl`. Platform-specific matching is covered by unit tests, while real-keyboard regression remains part of per-platform package validation.

## Platform and trust status

The build configuration targets Windows x64, Linux x64, macOS Intel, and macOS Apple Silicon. Package types depend on the artifacts actually produced for each Release. Real installation and cross-version update flows still require end-to-end verification on all four targets.

Tauri Updater artifacts and `latest.json` are protected with Minisign. This verifies updater payloads; it is not an operating-system code-signing identity.

- Stable Linux Releases require native OpenPGP signatures on AppImage and RPM files and include the public key plus its full fingerprint. DEB files currently rely on SHA-256 and the updater Minisign signature rather than a separate native package signature. Test Releases may explicitly state that native Linux signing was skipped when signing secrets were unavailable.
- Windows NSIS and MSI files in ordinary GitHub/Gitee Releases are not Authenticode-signed and may trigger unknown-publisher or SmartScreen warnings.
- Microsoft Store distribution is a separate channel. An unsigned MSIX submission package is generated by a dedicated workflow and is never uploaded to ordinary Releases; after Partner Center review, the Store-delivered package is signed by Microsoft.
- macOS packages currently use ad-hoc signing only. They do not carry a Developer ID identity and are not notarized by Apple.

Review each Release's notes, `SHA256SUMS.txt`, and—when provided—the Linux signing key and fingerprint before installation.

## Feedback

Report installation or usage problems through this repository's Issues page. Include the operating system, application version, model format, approximate vertex/triangle count, and reproducible steps. Do not attach private or proprietary 3D models unless you are authorized to share them.
