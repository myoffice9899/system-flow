# Diagram Editor - Like Draw.io

A web-based diagram editor with drawing, connecting, and exporting capabilities, similar to Draw.io.

## Features

### Drawing Tools
- **Rectangle**: Draw rectangular shapes
- **Circle**: Draw circular shapes
- **Diamond**: Draw diamond/rhombus shapes
- **Text**: Add text elements
- **Group**: Create container for hierarchical diagrams (can hold sub-flows)

### Software Development Icons
- **Database**: Database or data storage
- **Cloud**: Cloud services/infrastructure
- **Server**: Server or backend system
- **API**: API endpoint or interface
- **User**: User or actor in the system
- **Process**: Process, computation, or gear/settings

### Editing Tools
- **Select**: Select, move, and resize shapes
- **Auto-connect**: Click on existing shapes to instantly start connections
- **Undo/Redo**: Full history with Ctrl+Z / Ctrl+Y keyboard shortcuts

### Hierarchical Diagrams & Detailed Views
- **Multi-level navigation**: Create overview diagrams with detailed sub-flows
- **Detailed view for ALL shapes**: Every shape can now have its own detailed layer (not just groups)
- **Context-aware detailed view**: When entering a shape, see:
  - **Previous/Inbound shapes** on the left (green boxes with ◀)
  - **Next/Outbound shapes** on the right (blue boxes with ▶)
  - **Summary box** at top showing connection counts (↓ inbound | outbound ↑)
- **Auto-connect on shapes**: Click on a shape to automatically start drawing a connection
- **Breadcrumb navigation**: Track and navigate between levels
- **Nested details**: Shapes can contain other shapes at multiple levels deep
- **Import capability**: Right-click → Import to add content from JSON or Mermaid files

### Customization
- Change fill color
- Change stroke color
- Adjust stroke width
- Add text to shapes (double-click)

### As-Is / To-Be Comparison
- **Create To-Be diagram**: Right-click on canvas to create a duplicate for comparison
- **Switch views**: Toggle between As-Is and To-Be diagrams
- **Independent editing**: Edit each diagram separately
- **Exit comparison**: Return to single view mode

### Export/Import
- **Export to PNG** image
- **Save diagram as JSON** (full hierarchy preserved)
- **Load diagram from JSON**
- **Import into shapes**: Right-click any shape → Import
  - **JSON format**: Standard diagram format
  - **Mermaid format**: Import flowcharts from .mmd or .mermaid files
  - Supports: `A[Rectangle]`, `B(Circle)`, `C{Diamond}`
  - Connections: `A --> B`, `A -->|label| B`

## How to Use

1. **Open the Editor**
   - Open `index.html` in your web browser

2. **Draw Shapes**
   - Click on a shape button (rectangle, circle, diamond, text, or dev icons)
   - **Single click** on canvas to create default size shape
   - **Click and drag** on canvas to create custom size shape

3. **Select and Move**
   - Click the "Select" tool
   - Click on a shape to select it
   - **Drag on empty canvas** to draw selection box and select multiple shapes
   - Hold **Ctrl/Cmd + Click** to add shapes to selection
   - Drag to move the shape(s)
   - Use the handles to resize
   - **Right-click** to deselect all shapes and return to Select tool

4. **Connect Shapes**
   - **Easy method**: While in draw mode, click on any existing shape to auto-start connection
   - **Auto-create target**: Drag from a shape and release on empty space to create a new connected shape!
   - **Or use Connect tool**: Click the "Connect" tool, then click first shape and drag
   - Drag to another shape and release to connect
   - Drag to empty space and release to create a new shape at that point with auto-connection
   - Blue line with arrow preview shows while dragging
   - Target shape turns green when hovering over it
   - Bidirectional connections (A→B and B→A) automatically curve to avoid overlap
   - Click on any connection line to add a label/sequence number

5. **Work with Detailed Views (All Shapes)**
   - **Every shape** can now have detailed contents inside!
   - **Click to select**, then **Double-click to rename**
   - **Double-click unselected shape** to enter its detailed view
   - **Right-click** → "Detailed" to enter detail layer
   - When inside detailed view, see **context boxes** from all 4 directions:
     - **Top**: Shapes above that connect here (▼ inbound, ▲ outbound)
     - **Bottom**: Shapes below that connect here (▲ inbound, ▼ outbound)
     - **Left**: Shapes on left that connect here (▶ inbound, ◀ outbound)
     - **Right**: Shapes on right that connect here (◀ inbound, ▶ outbound)
   - Draw shapes and connections inside any shape
   - Use the "← Back" button or click breadcrumb to return to parent level
   - Group shapes show item count in bottom-right corner

6. **Customize Appearance**
   - Select a shape
   - Use the color pickers and width input to change properties

7. **Add Text**
   - Double-click any shape to add or edit text

8. **As-Is / To-Be Comparison**
   - Right-click on any shape (or canvas) and select "Create To-Be"
   - A comparison toolbar appears with "As-Is" and "To-Be" buttons
   - Click buttons to switch between diagrams
   - Edit the To-Be diagram independently from As-Is
   - Use this to plan changes before implementing them
   - Click "✕ Exit Comparison" to return to normal mode

9. **Export**
   - Click "Export PNG" to save as an image
   - Click "Save JSON" to save the diagram data
   - Click "Load JSON" to open a saved diagram

## Keyboard Shortcuts

- **Delete** or **Backspace**: Delete selected shape(s)
- **Escape**: Deselect all shapes and return to Select tool
- **Ctrl/Cmd + Z**: Undo last action
- **Ctrl/Cmd + Y** or **Ctrl/Cmd + Shift + Z**: Redo
- **Ctrl/Cmd + Click**: Add shape to selection (multi-select)
- **Right-click**: Deselect all and return to Select tool
- **Double-click** on unselected shape: Enter detailed view
- **Double-click** on selected shape: Rename shape

## File Structure

```
diagram-editor/
├── index.html      # Main HTML file
├── style.css       # Styling
├── script.js       # Application logic
└── README.md       # This file
```

## Technical Details

- Pure JavaScript (no external dependencies)
- HTML5 Canvas API for rendering
- Modern glassmorphism UI with CSS gradients and backdrop filters
- Responsive design with grid background
- Support for drag, resize, and connection operations
- **Universal detailed view system** - every shape can contain children
- Hierarchical data structure for infinite-depth nesting
- Breadcrumb navigation for multi-level diagrams
- Full export/import support for all hierarchy levels
- **Undo/Redo system** - full history tracking with up to 50 states
- **Auto-connect mode** - intelligent shape click detection switches to connection mode
- **Smart shape creation** - drag from shape to empty space auto-creates connected shapes
- **Context-aware detailed views** - automatic 4-direction layout for connected shapes
- **Smart double-click** - rename if selected, enter details if not selected
- **Mermaid parser** - import flowchart syntax from .mmd files
- **JSON import/export per shape** - each shape can import external diagrams
- **Smart bidirectional connection detection** with automatic curve rendering
- **Quadratic Bezier curves** for smooth bidirectional arrows
- **Arrow preview rendering** while dragging connections
- Connection label system with clickable lines
- Distance-based click detection for precise line selection
- **Multi-selection support** with marquee selection (drag to select)
- Batch operations for moving and deleting multiple shapes
- Right-click context menu for quick actions
- **As-Is / To-Be comparison mode** with independent state management
- Deep cloning algorithm for diagram duplication

## Browser Compatibility

Works in all modern browsers that support HTML5 Canvas:
- Chrome/Edge
- Firefox
- Safari
- Opera

## Tips

- **Modern UI**: Glassmorphism design with gradient colors and smooth animations
- **Quick shapes**: Single-click to create default size, or drag for custom size
- **Auto-connect**: Click on an existing shape while in draw mode to start connecting instantly
- **Smart connection workflow**:
  - Click shape → Drag → Release on another shape = Connect
  - Click shape → Drag → Release on empty space = Create new shape + Auto-connect!
- **Multi-select**: Drag to draw selection box, or Ctrl/Cmd+Click to add shapes
- **Right-click**: Quick way to deselect all and reset to Select tool
- Use the grid background to align shapes precisely
- **Every shape has details**: Double-click any shape (not just groups!) to enter its detailed view
- **Software dev icons**: Use database, cloud, server, API, user, and process icons
- **Keyboard shortcuts**:
  - Delete/Backspace to remove, Esc to deselect
  - Ctrl+Z / Ctrl+Y: Undo / Redo (up to 50 actions)
  - Double-click unselected shape: Enter details
  - Double-click selected shape: Rename
- **Bidirectional connections**: Create A→B and B→A for automatic curved lines
- **Arrow preview**: See where your connection arrow points while dragging
- **Connection labels**: Click on any line to add sequence numbers or labels
- **Batch operations**: Select multiple shapes and move or delete them together
- Connections automatically update when shapes move
- Use JSON export/import to save and share diagrams (includes all nested content)
- Drag and drop makes connecting shapes quick and intuitive
- Watch for the green highlight to confirm your connection target
- Create hierarchical diagrams by adding details to any shape
- Build complex multi-level architectures with shape-within-shape structure
- Breadcrumbs show your current location in the hierarchy
- Details can be nested infinitely deep for complex system modeling
- **Context boxes in detailed view**: Automatically see connected shapes from all 4 directions
  - **Green boxes** (inbound): Shapes pointing TO this shape
  - **Blue boxes** (outbound): Shapes this shape points TO
  - Position based on actual shape location (top/bottom/left/right)
  - **Orange summary** (top center): Total inbound and outbound count
- **Import Mermaid diagrams**: Right-click → Import → Select .mmd file
  - Example Mermaid: `A[Start] --> B(Process) --> C{Decision}`
- **As-Is / To-Be comparison**: Right-click and select "Create To-Be" to compare current state with planned future state
- Each diagram (As-Is and To-Be) maintains independent state including all nested details
- Use comparison mode to visualize and plan system improvements or process changes
