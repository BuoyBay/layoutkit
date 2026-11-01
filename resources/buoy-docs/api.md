---
title: "LayoutKit API"
summary: "Public APIs and lifecycle contracts for LayoutKit."
category: "Reference"
order: 20
keywords: ["layout", "source model", "designer", "refactor", "constraints"]
symbols: ["LayoutDocument", "LayoutNode", "LayoutProperty", "LayoutDocument.FrameEdits", "LayoutDocument.PropertyEdits", "LayoutDocument.InsertControlEdits", "LayoutDocument.ConstraintEdits", "LayoutDocument.DeclarationStartByte", "LayoutCatalog", "LayoutControlDescriptor", "LayoutPropertyDescriptor", "LayoutRenderer", "LayoutPropertyEditor", "LayoutPropertyViewFactory", "LayoutReusablePropertyViewV1", "LayoutDiscovery", "LayoutProjectRefactor", "LayoutProjectRefactorHost", "LayoutRelations"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# LayoutKit API

## Source model: `layoutkit.LayoutDocument`

| Symbol | Behavior |
| --- | --- |
| `LayoutDocument(sourceText, version = 1)` | Immutable source snapshot with `SourceText`, `Version`, and `Nodes`. |
| `LayoutNode` | Opaque `Id`, type/name/parent identity, literal bounds, editable state, and properties. |
| `LayoutProperty` | Property name, original expression, and editability. |
| `FindNode(id)` | Resolve an ID against this snapshot; absent nodes return `Nil`. |
| `DeclarationStartByte(id)` | Declaration-line byte offset for diagnostics, including read-only nodes. |
| `FrameEdits(...)`, `PropertyEdits(...)` | Propose precise geometry or supported scalar-expression changes. |
| `InsertControlEdits(...)` | Insert into a supported parent; property JSON contains typed scalar values. An optional source import supports package controls. |
| `SourceImports()` | Token-aware basic unconditional imports for source-type resolution. |
| `Constraints(rootId)` | Structured constraint records; unsupported expressions stay read-only. |
| `ConstraintEdits(...)`, `DeleteConstraintEdits(...)` | Insert/update/remove supported constraints; an empty constraint ID inserts. |
| `RenameControlEdits(...)`, `DeleteControlEdits(...)` | Declaration and layout-constraint changes only, not a complete application refactor. |

## Catalog: `layoutkit.LayoutCatalog`

`LayoutControlDescriptor` describes type identity, display name, package, default size, metadata, and explicit `LayoutPropertyDescriptor` values. Property descriptors carry kind, default expression, choices, numeric limits, constructor metadata, and read-only state.

`LayoutCatalog.Register`, `Find`, `Controls`, and `FindSource` manage descriptors. `FindSource(typeName, imports)` uses actual imports and refuses ambiguous source matches. `RegisterRenderer`, `RegisterEditor`, and `RegisterEditorView` attach compiled integrations; their corresponding lookup methods return `Nil` when absent.

`LayoutRenderer` paints through `IGraphics`. `LayoutPropertyEditor` returns an optional expression. Native factories implement `LayoutPropertyViewFactory`; commits go through `LayoutPropertyEditorHost.CommitExpression`. Reusable native Views implement `LayoutReusablePropertyViewV1.RebindProperty` and replace their snapshot-bound host on each rebind.

## Discovery, relations, and project commands

`layoutkit.LayoutDiscovery` exposes `LayoutDiscovery.ImportDescriptor`, `LoadIndex`, and `DiscoverDirectory`. It registers bounded data-only descriptors and rendering recipes without running package constructors or code-behind.

`LayoutRelations.ArrangementDisabledReason(document, id)` returns an empty string exactly when `CanArrange` accepts the single control, or a user-facing explanation of its first eligibility failure. Explanations are not stable machine-readable codes. Batch cardinality, duplicate selections, shared-parent requirements, modes, and resulting geometry remain operation-specific checks.

`layoutkit.LayoutRelations` exposes shared `Snap`, `NearMisses`, `AlignEdits`, and `DistributeEdits` measurements/planners for supported literal geometry.

`layoutkit.LayoutRefactor` exposes `LayoutProjectRefactor.PlanRename(items, selectedItemId, nodeId, newName)` and `PlanDelete(items, selectedItemId, nodeId)`. Plans include expected revisions and original spans. Supply the complete project source closure, including unsaved buffers and unopened code-behind files, and apply all changes atomically. Disable these commands when source coverage cannot be established; omitted references cannot be proven safe.

## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)


[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
