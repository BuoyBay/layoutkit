---
title: "LayoutKit getting started"
summary: "Inspect a source snapshot."
category: "Guides"
order: 10
keywords: ["layout", "source model", "designer", "refactor", "constraints"]
related: ["index.md", "api.md", "typed-api.md"]
---

# LayoutKit getting started

Install the `layoutkit` and `editorkit` archives in `packages/`. Import whole modules such as `layoutkit.LayoutDocument` and `layoutkit.LayoutCatalog`; the package has no self-named entry module for bare `Import layoutkit`.

This complete example inspects a simple Window declaration. The layout text is data: no Window is constructed by the parser.

For mutations, retain the snapshot revision along with proposed `EditorEdit` values. Recheck that revision against the authoritative document before applying the entire batch. Reload after commits and after undo/redo; resolve node IDs again. Empty or unsupported edit proposals must not be mistaken for a successful source change.

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

Call `RegisterBuiltinControls()` once on a fresh catalog. Register trusted compiled extensions explicitly, or import data-only descriptor indexes with `layoutkit.LayoutDiscovery`. Refresh into a fresh catalog so removed packages disappear. Run only the discovery helper shipped by the host, not a project-supplied executable.

## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
