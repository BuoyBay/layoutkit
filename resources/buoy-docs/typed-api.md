---
title: "layoutkit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["LayoutCatalog", "LayoutChoiceFactory", "LayoutChoiceView", "LayoutControlDescriptor", "LayoutDiscovery", "LayoutDocument", "LayoutGlyphIcon", "LayoutIconPainter", "LayoutImageIconPainter", "LayoutNode", "LayoutPastePlan", "LayoutProjectRefactor", "LayoutProjectRefactorHost", "LayoutProperty", "LayoutPropertyDescriptor", "LayoutPropertyEditor", "LayoutPropertyEditorHost", "LayoutPropertyEditorContextV1", "LayoutPropertyViewFactory", "LayoutRecipeIconPainter", "LayoutRecipeRenderer", "LayoutRelations", "LayoutRenderer", "LayoutReusablePropertyViewV1"]
dependencies: []
symbols: ["LayoutCatalog", "LayoutChoiceFactory", "LayoutChoiceView", "LayoutControlDescriptor", "LayoutDiscovery", "LayoutDocument", "LayoutGlyphIcon", "LayoutIconPainter", "LayoutImageIconPainter", "LayoutNode", "LayoutPastePlan", "LayoutProjectRefactor", "LayoutProjectRefactorHost", "LayoutProperty", "LayoutPropertyDescriptor", "LayoutPropertyEditor", "LayoutPropertyEditorHost", "LayoutPropertyEditorContextV1", "LayoutPropertyViewFactory", "LayoutRecipeIconPainter", "LayoutRecipeRenderer", "LayoutRelations", "LayoutRenderer", "LayoutReusablePropertyViewV1"]
related: ["api.md", "getting-started.md", "index.md"]
---

# layoutkit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## LayoutRenderer

`Public Interface LayoutRenderer`

### RendererId

`Function RendererId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### Paint

`Sub Paint(g As IGraphics, x As Double, y As Double, width As Double, height As Double, values As JSONItem, selected As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `width` | `Double` | `ByVal` | Required |
| `height` | `Double` | `ByVal` | Required |
| `values` | `JSONItem` | `ByVal` | Required |
| `selected` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutPropertyEditor

`Public Interface LayoutPropertyEditor`

### EditorId

`Function EditorId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### EditExpression

`Function EditExpression(currentExpression As String) As Optional Of String`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Optional Of String` |

## LayoutPropertyEditorHost

`Public Interface LayoutPropertyEditorHost`

### CommitExpression

`Function CommitExpression(expression As String) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `expression` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

## LayoutPropertyEditorContextV1

Optional read-only context implemented by LayoutCanvas snapshot bindings.
`SiblingExpression(propertyName As String) As Optional Of String` returns a raw
source expression from the bound node, or None when absent. Do not evaluate it.
`IsCurrent() As Boolean` checks the binding's revision, selection and generation.
Mutation continues through `LayoutPropertyEditorHost.CommitExpression`.

## LayoutPropertyViewFactory

`Public Interface LayoutPropertyViewFactory`

### EditorId

`Function EditorId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### CreateView

`Function CreateView(currentExpression As String, host As LayoutPropertyEditorHost) As View`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `View` |

## LayoutReusablePropertyViewV1

`Public Interface LayoutReusablePropertyViewV1`

Optional lifecycle contract for a native editor View. Build children once; rebind displayed values and callbacks to the new host without retaining the old host. Old snapshot hosts remain expired. Rebind must not append native children.

### RebindProperty

`Sub RebindProperty(currentExpression As String, host As LayoutPropertyEditorHost)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

Returns: no value.

## LayoutPropertyDescriptor

`Public Class LayoutPropertyDescriptor`

Unknown kinds and expression defaults are retained verbatim for inspection. ValidateExpression is a mutation gate, never an evaluator or source parser.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Name` | `String` | Yes | No | — | — |
| `Kind` | `String` | Yes | No | — | — |
| `DefaultExpression` | `String` | Yes | No | — | — |
| `DisplayName` | `String` | No | No | — | — |
| `Category` | `String` | No | No | `"Properties"` | — |
| `EditorId` | `String` | No | No | `""` | — |
| `ReadOnly` | `Boolean` | No | No | `False` | — |
| `Options` | `Array Of String` | No | No | `[]` | — |
| `ConstructorParameter` | `String` | No | No | `""` | — |
| `ConstructorIndex` | `Integer` | No | No | `-1` | — |
| `Minimum` | `Optional Of Double` | No | No | `None` | — |
| `Maximum` | `Optional Of Double` | No | No | `None` | — |
| `StepValue` | `Double` | No | No | `1.0` | — |
| `Metadata` | `JSONItem` | No | No | — | — |

### Constructor

`Public Sub Constructor(name As String, kind As String, defaultExpression As String = "")`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `name` | `String` | `ByVal` | Required |
| `kind` | `String` | `ByVal` | Required |
| `defaultExpression` | `String` | `ByVal` | `""` |

Returns: no value.

### ValidateExpression

`Public Function ValidateExpression(expression As String) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `expression` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

## LayoutControlDescriptor

`Public Class LayoutControlDescriptor`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `TypeName` | `String` | Yes | No | — | — |
| `DisplayName` | `String` | Yes | No | — | — |
| `PackageName` | `String` | Yes | No | — | — |
| `DefaultWidth` | `Integer` | No | No | `100` | — |
| `DefaultHeight` | `Integer` | No | No | `30` | — |
| `Metadata` | `JSONItem` | No | No | — | — |
| `Description` | `String` | No | No | `""` | One-line palette/tooltip description; empty when the provider gave none. |
| `Category` | `String` | No | No | — | Palette grouping ("Buttons", "Text", "Input", "Containers", "Indicators", "Data", "Media" for builtins). Unset package controls group under their package name; unset builtin-package controls under "Controls". |
| `Properties` | `Array Of LayoutPropertyDescriptor` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(typeName As String, displayName As String, packageName As String = "builtin")`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |
| `displayName` | `String` | `ByVal` | Required |
| `packageName` | `String` | `ByVal` | `"builtin"` |

Returns: no value.

### AddProperty

`Public Sub AddProperty(descriptor As LayoutPropertyDescriptor)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `descriptor` | `LayoutPropertyDescriptor` | `ByVal` | Required |

Returns: no value.

## LayoutIconPainter

`Public Interface LayoutIconPainter`

Draws a square palette icon at (x, y) with side size points. dark selects the dark-appearance palette. Painters must not retain g and must be side-effect free.

### PaintIcon

`Sub PaintIcon(g As IGraphics, x As Double, y As Double, size As Double, dark As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `size` | `Double` | `ByVal` | Required |
| `dark` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutGlyphIcon

`Public Class LayoutGlyphIcon Implements LayoutIconPainter`

The builtin Buoy control glyph set drawn with IGraphics vectors: a 24-unit grid, 1.75-unit strokes in the ink colour and one accent detail per glyph. Unknown glyph names draw the generic control glyph.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Glyph` | `String` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(glyph As String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `glyph` | `String` | `ByVal` | Required |

Returns: no value.

### Normalize

`Public Shared Function Normalize(name As String) As String`

Lower-case, separator-free key: "Text field", "text-field" and "TextField" all resolve to "textfield".

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `name` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `String` |

### Knows

`Public Shared Function Knows(name As String) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `name` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### PaintIcon

`Public Sub PaintIcon(g As IGraphics, x As Double, y As Double, size As Double, dark As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `size` | `Double` | `ByVal` | Required |
| `dark` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutCatalog

`Public Class LayoutCatalog`

### Constructor

`Public Sub Constructor()`

No parameters.

Returns: no value.

### Categories

`Public Function Categories() As Array Of String`

Palette group order: builtin groups first, then any other categories in first-registration order (package names and custom groups).

No parameters.

#### Returns

| Type |
| --- |
| `Array Of String` |

### RegisterIcon

`Public Sub RegisterIcon(typeName As String, painter As LayoutIconPainter)`

Compiled extensions and discovered data icons register painters here; a later registration for the same type replaces the earlier one (hosts may re-theme). Types need not be registered controls, so hosts can also supply icons for layout roots such as Window. The identity is resolved when this is called: an exact type name (or a unique qualified source name, as Find) first; otherwise a bare source name such as "Thing" for "pkg.Thing" maps to the one registered control whose type name or sourceTypeName matches it (case-insensitively, like icon keys). If none or several match, the icon is stored under the name as given, so IconFor finds it only by that exact (case-insensitive) name; register controls before their icons, and use the qualified type name when two packages share a source name. "Window" (the layout root, never a control) is never resolved this way, so a package control whose source name is Window cannot capture a host's root icon. Other unregistered core names (Splitter, TreeView...) do resolve to a unique package control that claims them; register those core icons before loading packages.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |
| `painter` | `LayoutIconPainter` | `ByVal` | Required |

Returns: no value.

### IconFor

`Public Function IconFor(typeName As String) As LayoutIconPainter`

Never Nil: a registered painter, else the builtin glyph for an unqualified builtin type (including roots such as Window and Splitter), else the package glyph for package controls, else the generic control glyph.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutIconPainter` |

### HasRegisteredIcon

`Public Function HasRegisteredIcon(typeName As String) As Boolean`

True when IconFor returns a painter registered through RegisterIcon.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### Register

`Public Sub Register(descriptor As LayoutControlDescriptor)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `descriptor` | `LayoutControlDescriptor` | `ByVal` | Required |

Returns: no value.

### Find

`Public Function Find(typeName As String) As LayoutControlDescriptor`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutControlDescriptor` |

### Controls

`Public Function Controls() As Array Of LayoutControlDescriptor`

No parameters.

#### Returns

| Type |
| --- |
| `Array Of LayoutControlDescriptor` |

### FindSource

`Public Function FindSource(typeName As String, imports As Array Of String) As LayoutControlDescriptor`

Resolve a bare source type only through the document's actual imports.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |
| `imports` | `Array Of String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutControlDescriptor` |

### RegisterRenderer

`Public Sub RegisterRenderer(typeName As String, renderer As LayoutRenderer)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |
| `renderer` | `LayoutRenderer` | `ByVal` | Required |

Returns: no value.

### RendererFor

`Public Function RendererFor(typeName As String) As LayoutRenderer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `typeName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutRenderer` |

### RegisterEditor

`Public Sub RegisterEditor(editor As LayoutPropertyEditor)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `editor` | `LayoutPropertyEditor` | `ByVal` | Required |

Returns: no value.

### EditorFor

`Public Function EditorFor(id As String) As LayoutPropertyEditor`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `id` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutPropertyEditor` |

### RegisterEditorView

`Public Sub RegisterEditorView(factory As LayoutPropertyViewFactory)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `factory` | `LayoutPropertyViewFactory` | `ByVal` | Required |

Returns: no value.

### EditorViewFor

`Public Function EditorViewFor(id As String) As LayoutPropertyViewFactory`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `id` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutPropertyViewFactory` |

### RegisterBuiltinControls

`Public Sub RegisterBuiltinControls()`

Registers the core UI controls the Control grammar can declare without constructor arguments (Splitter needs one, so it is a glyph-only layout type). Property spellings are compiler-checked by tests/layoutkit_catalog_test.bui.

No parameters.

Returns: no value.

## LayoutRecipeRenderer

`Public Class LayoutRecipeRenderer Implements LayoutRenderer`

Fixed interpreter: no source evaluation, FFI, package callbacks, or control construction.

### Constructor

`Public Sub Constructor(control As LayoutControlDescriptor, recipe As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `control` | `LayoutControlDescriptor` | `ByVal` | Required |
| `recipe` | `JSONItem` | `ByVal` | Required |

Returns: no value.

### RendererId

`Public Function RendererId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### Paint

`Public Sub Paint(g As IGraphics, x As Double, y As Double, width As Double, height As Double, values As JSONItem, selected As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `width` | `Double` | `ByVal` | Required |
| `height` | `Double` | `ByVal` | Required |
| `values` | `JSONItem` | `ByVal` | Required |
| `selected` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutRecipeIconPainter

`Public Class LayoutRecipeIconPainter Implements LayoutIconPainter`

Data-only icon: the shared recipe interpreter painted into a 24x24 design grid scaled to the requested size and clipped to the icon square.

### Constructor

`Public Sub Constructor(control As LayoutControlDescriptor, recipe As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `control` | `LayoutControlDescriptor` | `ByVal` | Required |
| `recipe` | `JSONItem` | `ByVal` | Required |

Returns: no value.

### PaintIcon

`Public Sub PaintIcon(g As IGraphics, x As Double, y As Double, size As Double, dark As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `size` | `Double` | `ByVal` | Required |
| `dark` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutImageIconPainter

`Public Class LayoutImageIconPainter Implements LayoutIconPainter`

Package-supplied PNG icon (decoded lazily on first paint, never executed). Falls back to the declarative or generic icon when the image cannot be decoded. Holds the bytes, never a path: only PNG-signed data with an IHDR of at most 512x512 is ever decoded, and only with the PNG decoder.

### Constructor

`Public Sub Constructor(data As Bytes, fallback As LayoutIconPainter)`

data holds PNG bytes (re-validated before decoding).

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `Bytes` | `ByVal` | Required |
| `fallback` | `LayoutIconPainter` | `ByVal` | Required |

Returns: no value.

### Constructor (overload 2)

`Public Sub Constructor(data As Bytes, filePath As String, fallback As LayoutIconPainter)`

Compatibility form. A non-empty filePath is read once, now, with a 64 KiB bounded read and the same PNG checks; an unusable file paints the fallback.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `Bytes` | `ByVal` | Required |
| `filePath` | `String` | `ByVal` | Required |
| `fallback` | `LayoutIconPainter` | `ByVal` | Required |

Returns: no value.

### IsLoaded

`Public Function IsLoaded() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### PaintIcon

`Public Sub PaintIcon(g As IGraphics, x As Double, y As Double, size As Double, dark As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `size` | `Double` | `ByVal` | Required |
| `dark` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutChoiceView

`Public Class LayoutChoiceView Inherits View Implements LayoutReusablePropertyViewV1`

Generic native choice editor; all commits pass through the host's revision gate.

### Constructor

`Public Sub Constructor(options As Array Of String, currentExpression As String, host As LayoutPropertyEditorHost)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `options` | `Array Of String` | `ByVal` | Required |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

Returns: no value.

### RebindProperty

`Public Sub RebindProperty(currentExpression As String, host As LayoutPropertyEditorHost)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

Returns: no value.

### PerformChoice

`Public Sub PerformChoice(expression As String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `expression` | `String` | `ByVal` | Required |

Returns: no value.

## LayoutChoiceFactory

`Public Class LayoutChoiceFactory Implements LayoutPropertyViewFactory`

### Constructor

`Public Sub Constructor(id As String, options As Array Of String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `id` | `String` | `ByVal` | Required |
| `options` | `Array Of String` | `ByVal` | Required |

Returns: no value.

### EditorId

`Public Function EditorId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### CreateView

`Public Function CreateView(currentExpression As String, host As LayoutPropertyEditorHost) As View`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `View` |

## LayoutDiscovery

`Public Class LayoutDiscovery`

Data-only discovery. Refresh the index with discover_layout_packages.py before startup discovery; this module intentionally has no native ZIP dependency.

### Constructor

`Public Sub Constructor()`

No parameters.

Returns: no value.

### ImportDescriptor

`Public Function ImportDescriptor(descriptor As JSONItem, catalog As LayoutCatalog) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `descriptor` | `JSONItem` | `ByVal` | Required |
| `catalog` | `LayoutCatalog` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

### LoadIndex

`Public Function LoadIndex(location As String, catalog As LayoutCatalog) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `location` | `String` | `ByVal` | Required |
| `catalog` | `LayoutCatalog` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

### DiscoverDirectory

`Public Function DiscoverDirectory(location As String, catalog As LayoutCatalog) As JSONItem`

Scans a refreshed project index or an unpacked package resource directory. Archive/global scanning happens in the startup helper, never by executing code.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `location` | `String` | `ByVal` | Required |
| `catalog` | `LayoutCatalog` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

## LayoutProperty

`Public Class LayoutProperty`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Name` | `String` | Yes | No | — | — |
| `RawValue` | `String` | Yes | No | — | — |
| `Editable` | `Boolean` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(name As String, rawValue As String, editable As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `name` | `String` | `ByVal` | Required |
| `rawValue` | `String` | `ByVal` | Required |
| `editable` | `Boolean` | `ByVal` | Required |

Returns: no value.

## LayoutNode

`Public Class LayoutNode`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Id` | `String` | Yes | No | — | — |
| `TypeName` | `String` | Yes | No | — | — |
| `Name` | `String` | Yes | No | — | — |
| `ParentId` | `String` | Yes | No | — | — |
| `X` | `Integer` | Yes | No | — | — |
| `Y` | `Integer` | Yes | No | — | — |
| `Width` | `Integer` | Yes | No | — | — |
| `Height` | `Integer` | Yes | No | — | — |
| `Editable` | `Boolean` | Yes | No | — | — |
| `Properties` | `Array Of LayoutProperty` | Yes | No | — | — |
| `HasLiteralFrame` | `Boolean` | Yes | No | — | Declared frame geometry is available for preview, even when constraints prevent direct manipulation. This does not claim a solved constraint frame. |

### Constructor

`Public Sub Constructor(id As String, typeName As String, name As String, parentId As String, x As Integer, y As Integer, width As Integer, height As Integer, editable As Boolean, properties As Array Of LayoutProperty, hasLiteralFrame As Boolean = False)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `id` | `String` | `ByVal` | Required |
| `typeName` | `String` | `ByVal` | Required |
| `name` | `String` | `ByVal` | Required |
| `parentId` | `String` | `ByVal` | Required |
| `x` | `Integer` | `ByVal` | Required |
| `y` | `Integer` | `ByVal` | Required |
| `width` | `Integer` | `ByVal` | Required |
| `height` | `Integer` | `ByVal` | Required |
| `editable` | `Boolean` | `ByVal` | Required |
| `properties` | `Array Of LayoutProperty` | `ByVal` | Required |
| `hasLiteralFrame` | `Boolean` | `ByVal` | `False` |

Returns: no value.

## LayoutPastePlan

`Public Class LayoutPastePlan`

Paste/embed plans: Edits address the original snapshot and must be applied atomically against LayoutDocument.Version. Names lists the final top-level control names (after uniquifying) so hosts can select them after reloading.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Edits` | `Array Of EditorEdit` | No | No | `[]` | — |
| `Names` | `Array Of String` | No | No | `[]` | — |
| `Imports` | `Array Of String` | No | No | `[]` | Import lines this plan adds (empty when every recorded import is present). |

## LayoutDocument

`Public Class LayoutDocument`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `SourceText` | `String` | Yes | No | — | — |
| `Version` | `Integer` | Yes | No | — | — |
| `Nodes` | `Array Of LayoutNode` | Yes | No | — | A fresh copy in declaration order on every read (callers may mutate it). Hot loops should read it once, or use NodeCount/NodeAt, which do not copy. |

### Constructor

`Public Sub Constructor(sourceText As String, version As Integer = 1)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `sourceText` | `String` | `ByVal` | Required |
| `version` | `Integer` | `ByVal` | `1` |

Returns: no value.

### NodeCount

`Public Function NodeCount() As Integer`

Number of nodes; NodeAt(0 To NodeCount() - 1) walks Nodes without copying.

No parameters.

#### Returns

| Type |
| --- |
| `Integer` |

### NodeAt

`Public Function NodeAt(index As Integer) As LayoutNode`

The node at a declaration-order index; throws OutOfBoundsException when out of range.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `index` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutNode` |

### FindNode

`Public Function FindNode(id As String) As LayoutNode`

The node with exactly this opaque id, or Nil. O(1); no fallback scan.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `id` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutNode` |

### DeclarationStartByte

`Public Function DeclarationStartByte(id As String) As Integer`

Declaration byte offset in this immutable source snapshot. IDs stay opaque.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `id` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### FrameEdits

`Public Function FrameEdits(nodeId As String, x As Integer, y As Integer, width As Integer, height As Integer) As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `nodeId` | `String` | `ByVal` | Required |
| `x` | `Integer` | `ByVal` | Required |
| `y` | `Integer` | `ByVal` | Required |
| `width` | `Integer` | `ByVal` | Required |
| `height` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### PropertyEdits

`Public Function PropertyEdits(nodeId As String, propertyName As String, rawValue As String) As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `nodeId` | `String` | `ByVal` | Required |
| `propertyName` | `String` | `ByVal` | Required |
| `rawValue` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### SourceImports

`Public Function SourceImports() As Array Of String`

Basic unconditional imports used to resolve palette symbols in this snapshot. Aliased, selective and conditional imports are deliberately not inferred. Scanned once per snapshot; every call returns a fresh copy callers may extend.

No parameters.

#### Returns

| Type |
| --- |
| `Array Of String` |

### InsertControlEdits

`Public Function InsertControlEdits(parentId As String, typeName As String, controlName As String, x As Integer, y As Integer, width As Integer, height As Integer) As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `parentId` | `String` | `ByVal` | Required |
| `typeName` | `String` | `ByVal` | Required |
| `controlName` | `String` | `ByVal` | Required |
| `x` | `Integer` | `ByVal` | Required |
| `y` | `Integer` | `ByVal` | Required |
| `width` | `Integer` | `ByVal` | Required |
| `height` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### InsertControlEdits (overload 2)

`Public Function InsertControlEdits(parentId As String, typeName As String, controlName As String, x As Integer, y As Integer, width As Integer, height As Integer, importName As String) As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `parentId` | `String` | `ByVal` | Required |
| `typeName` | `String` | `ByVal` | Required |
| `controlName` | `String` | `ByVal` | Required |
| `x` | `Integer` | `ByVal` | Required |
| `y` | `Integer` | `ByVal` | Required |
| `width` | `Integer` | `ByVal` | Required |
| `height` | `Integer` | `ByVal` | Required |
| `importName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### InsertControlEdits (overload 3)

`Public Function InsertControlEdits(parentId As String, typeName As String, controlName As String, x As Integer, y As Integer, width As Integer, height As Integer, properties As JSONItem, importName As String = "") As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `parentId` | `String` | `ByVal` | Required |
| `typeName` | `String` | `ByVal` | Required |
| `controlName` | `String` | `ByVal` | Required |
| `x` | `Integer` | `ByVal` | Required |
| `y` | `Integer` | `ByVal` | Required |
| `width` | `Integer` | `ByVal` | Required |
| `height` | `Integer` | `ByVal` | Required |
| `properties` | `JSONItem` | `ByVal` | Required |
| `importName` | `String` | `ByVal` | `""` |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### Constraints

`Public Function Constraints(rootId As String) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `rootId` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

### ConstraintEdits

`Public Function ConstraintEdits(rootId As String, constraintId As String, leftNodeId As String, leftAnchor As String, relation As String, rightNodeId As String, rightAnchor As String, offset As Integer, priority As String = "Required") As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `rootId` | `String` | `ByVal` | Required |
| `constraintId` | `String` | `ByVal` | Required |
| `leftNodeId` | `String` | `ByVal` | Required |
| `leftAnchor` | `String` | `ByVal` | Required |
| `relation` | `String` | `ByVal` | Required |
| `rightNodeId` | `String` | `ByVal` | Required |
| `rightAnchor` | `String` | `ByVal` | Required |
| `offset` | `Integer` | `ByVal` | Required |
| `priority` | `String` | `ByVal` | `"Required"` |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### DeleteConstraintEdits

`Public Function DeleteConstraintEdits(rootId As String, constraintId As String) As Array Of EditorEdit`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `rootId` | `String` | `ByVal` | Required |
| `constraintId` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### RenameControlEdits

`Public Function RenameControlEdits(nodeId As String, newName As String) As Array Of EditorEdit`

Layout-local only: declaration and constraint references in this root. Project refactoring must prove and update code-behind references separately.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `nodeId` | `String` | `ByVal` | Required |
| `newName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### DeleteControlEdits

`Public Function DeleteControlEdits(nodeId As String) As Array Of EditorEdit`

Removes layout source only; project code-behind remains the caller's responsibility.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `nodeId` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### ReorderEdits

`Public Function ReorderEdits(nodeId As String, mode As String) As Array Of EditorEdit`

Z-order is declaration order among siblings (later = in front). Moves whole control blocks with their leading comment lines; all bytes are retained. mode: front&#124;forward&#124;backward&#124;back. An unchanged order returns no edits.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `nodeId` | `String` | `ByVal` | Required |
| `mode` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### CopySnippet

`Public Function CopySnippet(ids As Array Of String) As String`

Self-contained clipboard text for the selected control blocks, including nested children and leading comments. Imports are inferred: none when every copied type is a built-in control, otherwise this file's basic imports.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `ids` | `Array Of String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `String` |

### CopySnippet (overload 2)

`Public Function CopySnippet(ids As Array Of String, imports As Array Of String) As String`

imports: exact source imports the snippet needs (for example catalog sourceImport metadata); an empty array records none.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `ids` | `Array Of String` | `ByVal` | Required |
| `imports` | `Array Of String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `String` |

### PlanPaste

`Public Function PlanPaste(parentId As String, snippet As String, offsetX As Integer, offsetY As Integer) As LayoutPastePlan`

Plan inserting a CopySnippet text as the front-most children of parentId (root or View). Clashing names in the destination root are renumbered (button1 -> button2), top-level frames are offset by (offsetX, offsetY), text is re-indented and recorded imports missing here are added.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `parentId` | `String` | `ByVal` | Required |
| `snippet` | `String` | `ByVal` | Required |
| `offsetX` | `Integer` | `ByVal` | Required |
| `offsetY` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutPastePlan` |

### PlanEmbed

`Public Function PlanEmbed(ids As Array Of String, containerName As String) As LayoutPastePlan`

Wrap same-container controls in a new View sized to their bounds; children are re-based to View coordinates. Names (and code-behind references such as Me.name or With name) are unchanged because nested controls remain typed members of the window class. Refused when a constraint references them.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `ids` | `Array Of String` | `ByVal` | Required |
| `containerName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutPastePlan` |

### PlanUnembed

`Public Function PlanUnembed(viewId As String) As LayoutPastePlan`

Remove a plain View (Frame only) and move its children to the View's container, re-based to container coordinates. Code-behind that names the View itself (Me.view, With view) stops compiling; hosts should prove there are no such references (for example with LayoutProjectRefactor.PlanDelete).

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `viewId` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `LayoutPastePlan` |

## LayoutProjectRefactorHost

`Public Interface LayoutProjectRefactorHost`

### RenameLayoutControl

`Function RenameLayoutControl(expectedVersion As Integer, nodeId As String, newName As String) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `expectedVersion` | `Integer` | `ByVal` | Required |
| `nodeId` | `String` | `ByVal` | Required |
| `newName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### DeleteLayoutControl

`Function DeleteLayoutControl(expectedVersion As Integer, nodeId As String) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `expectedVersion` | `Integer` | `ByVal` | Required |
| `nodeId` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

## LayoutProjectRefactor

`Public Class LayoutProjectRefactor`

### PlanRename

`Public Function PlanRename(items As JSONItem, selectedItemId As String, nodeId As String, newName As String) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `JSONItem` | `ByVal` | Required |
| `selectedItemId` | `String` | `ByVal` | Required |
| `nodeId` | `String` | `ByVal` | Required |
| `newName` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

### PlanDelete

`Public Function PlanDelete(items As JSONItem, selectedItemId As String, nodeId As String) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `JSONItem` | `ByVal` | Required |
| `selectedItemId` | `String` | `ByVal` | Required |
| `nodeId` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

## LayoutRelations

`Public Class LayoutRelations`

Shared geometry guidance for native designers and GUI linters. All coordinates are parent-relative layout units. Profile margins/spacing are caller policy.

### CanArrange

`Public Shared Function CanArrange(document As LayoutDocument, id As String) As Boolean`

True when the arrangement batches (AlignToEdits, DistributeEdgesEdits, SpaceEdits, MatchSizeEdits, MoveByEdits, FramesEdits) accept this control: an editable, visible, non-root control with a literal positive Frame whose ancestors are visible, editable plain Views with literal Frames up to a root that also has a literal Frame. Editors use it to enable commands.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `id` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### ArrangementDisabledReason

`Public Shared Function ArrangementDisabledReason(document As LayoutDocument, id As String) As String`

Empty exactly when CanArrange accepts this single control; otherwise a user-facing first-failure explanation, not a stable machine-readable code. Batch cardinality, duplicates, shared parents, modes and resulting geometry are validated separately by the requested arrangement operation.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `id` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `String` |

### Snap

`Public Shared Function Snap(document As LayoutDocument, nodeId As String, x As Integer, y As Integer, width As Integer, height As Integer, tolerance As Integer, margins As Array Of Integer, spacing As Array Of Integer, resize As Boolean = False) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `nodeId` | `String` | `ByVal` | Required |
| `x` | `Integer` | `ByVal` | Required |
| `y` | `Integer` | `ByVal` | Required |
| `width` | `Integer` | `ByVal` | Required |
| `height` | `Integer` | `ByVal` | Required |
| `tolerance` | `Integer` | `ByVal` | Required |
| `margins` | `Array Of Integer` | `ByVal` | Required |
| `spacing` | `Array Of Integer` | `ByVal` | Required |
| `resize` | `Boolean` | `ByVal` | `False` |

#### Returns

| Type |
| --- |
| `JSONItem` |

### NearMisses

`Public Shared Function NearMisses(document As LayoutDocument, tolerance As Integer, margins As Array Of Integer, spacing As Array Of Integer, centerTolerance As Integer = 3) As JSONItem`

Near alignment requires a consensus of at least two same-type siblings. Margin/spacing/centering findings are advisory near misses, never mandates.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `tolerance` | `Integer` | `ByVal` | Required |
| `margins` | `Array Of Integer` | `ByVal` | Required |
| `spacing` | `Array Of Integer` | `ByVal` | Required |
| `centerTolerance` | `Integer` | `ByVal` | `3` |

#### Returns

| Type |
| --- |
| `JSONItem` |

### AlignEdits

`Public Shared Function AlignEdits(document As LayoutDocument, ids As Array Of String, mode As String) As Array Of EditorEdit`

The first selected sibling is the alignment reference; edit batches retain source trivia and must be applied atomically against document.Version.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `mode` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### DistributeEdits

`Public Shared Function DistributeEdits(document As LayoutDocument, ids As Array Of String, axis As String) As Array Of EditorEdit`

Equal gaps retain first/last positions; integer rounding is deterministic.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `axis` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### AlignToEdits

`Public Shared Function AlignToEdits(document As LayoutDocument, ids As Array Of String, mode As String, reference As String) As Array Of EditorEdit`

Align to the selection bounds, the key control (ids(0)) or each control's own container (0, 0, width, height). Parent-relative; one atomic batch.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `mode` | `String` | `ByVal` | Required |
| `reference` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### DistributeEdgesEdits

`Public Shared Function DistributeEdgesEdits(document As LayoutDocument, ids As Array Of String, edge As String) As Array Of EditorEdit`

Equalise one edge between the outermost controls (3+ siblings). The outermost controls keep their positions; sizes never change.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `edge` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### SpaceEdits

`Public Shared Function SpaceEdits(document As LayoutDocument, ids As Array Of String, axis As String, mode As String, amount As Integer) As Array Of EditorEdit`

Gap commands along axis x&#124;y. mode: equal (3+, outermost fixed), increase, decrease (by amount, never below touching), remove (gap 0) or set (gap = amount). The first control in axis order stays fixed.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `axis` | `String` | `ByVal` | Required |
| `mode` | `String` | `ByVal` | Required |
| `amount` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### MatchSizeEdits

`Public Shared Function MatchSizeEdits(document As LayoutDocument, ids As Array Of String, dimension As String) As Array Of EditorEdit`

Match width, height or both to the key control ids(0). Controls may live in different containers; positions never change.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `dimension` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### MoveByEdits

`Public Shared Function MoveByEdits(document As LayoutDocument, ids As Array Of String, dx As Integer, dy As Integer) As Array Of EditorEdit`

Offset every selected control by (dx, dy) in its own parent coordinates. A control whose ancestor is also selected moves with that ancestor only.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `dx` | `Integer` | `ByVal` | Required |
| `dy` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |

### FramesEdits

`Public Shared Function FramesEdits(document As LayoutDocument, ids As Array Of String, frames As JSONItem) As Array Of EditorEdit`

Commit explicit frames: frames is a JSON array of {x, y, width, height} objects aligned with ids (group drag/resize previews). Values are rounded.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `document` | `LayoutDocument` | `ByVal` | Required |
| `ids` | `Array Of String` | `ByVal` | Required |
| `frames` | `JSONItem` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of EditorEdit` |
