# Inspect and edit declarative layouts without a GUI

A headless source model and explicit extension catalog for the native Buoy layout editor. Requires EditorKit. Import `layoutkit.LayoutDocument` for `LayoutDocument`, `LayoutNode` and `LayoutProperty`, and `layoutkit.LayoutCatalog` for catalog descriptors and extension interfaces. Buoy 0.72 rejects selective imports of these classes/interfaces; there is no self-named module for bare `Import layoutkit`.

`LayoutDocument(sourceText, version)` is an immutable snapshot. `Nodes`, `FindNode`, `FrameEdits` and `PropertyEdits` inspect source or propose half-open UTF-8 `EditorEdit` ranges. The host keeps the authoritative `EditorDocument`, compares the snapshot version with its current revision, and applies the entire batch once. It then reloads a fresh snapshot. Node IDs belong to a snapshot; resolve them again after source changes. Undo, redo, saved baselines and disk persistence belong to the host.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add layoutkit --git https://github.com/BuoyBay/layoutkit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.
BPM also resolves `editorkit`.

## Example

```buoy
Import layoutkit.LayoutDocument

Sub Main()
    Dim source As String = "Window Contact\n    Frame = (0, 0, 400, 240)\nEnd Window\n"
    Dim snapshot As New LayoutDocument(source, 1)
    For Each node As LayoutNode In snapshot.Nodes
        Print node.Name + ": " + node.TypeName
    Next
End Sub
```

## Build and API reference

Source is in `modules/`, with native/runtime inputs where required. Use the
[package guide](docs/API.md) for backend-specific build prerequisites, ownership
rules and supported targets. Rebuilding a native backend requires that target's
compiler and SDK; sealing an archive alone does not rebuild the backend.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

The generated agent files and editor settings stay local and are ignored by Git.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
