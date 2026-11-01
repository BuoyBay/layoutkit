---
title: "LayoutKit"
summary: "Headless layout source snapshots, precise edit proposals, extension catalogs, and project refactor planning."
category: "Overview"
order: 0
keywords: ["layout", "source model", "designer", "refactor", "constraints"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# LayoutKit

LayoutKit reads Buoy Window/View declarations as immutable source snapshots and proposes focused edits. It preserves comments, unknown expressions, whitespace outside changed spans, and code that is not part of the edited layout. It never evaluates a source document to inspect it.

Use `LayoutDocument` to inspect nodes and propose geometry/property/constraint edits. Use `LayoutCatalog` to describe editable properties and register compiled or data-only design integrations. Project-wide rename/delete planning belongs to `LayoutProjectRefactor`, using a complete source closure supplied by the host.

## Revision and coordinate model

Snapshots have a `Version`; node IDs belong to that snapshot. Edit ranges are half-open UTF-8 byte offsets. The application keeps an authoritative EditorKit document, compares revisions, applies a whole edit batch once, and loads a fresh snapshot. Saving, undo, redo, and atomic multi-buffer changes remain host responsibilities.

Computed geometry and ambiguous or unsupported syntax remain read-only. Constraint-controlled frames are not directly draggable. The model is a source-preserving editor, not a live layout constraint solver.

## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
