# JigsawPuzzle Extension Documentation

## Introduction
The **JigsawPuzzle** extension allows you to create fully functional, professional-grade jigsaw puzzle games within MIT App Inventor, Kodular, and other derivative platforms. It handles the complex logic of image slicing, piece shape generation (Bezier curves), touch interaction, and game state management.

## Installation
1.  Download the `io.th.jigsawpuzzle.aix` file.
2.  Open your project in App Inventor (or Kodular/Niotron).
3.  Go to the **Extension** palette and click **Import extension**.
4.  Drag the **JigsawPuzzle** component onto your screen.

## Designer & Blocks Reference

### Properties
These properties can be set in the Designer or via Blocks.

| Property | Type | Description |
| :--- | :--- | :--- |
| **Image** | Text | The filename of the image asset to use for the puzzle (e.g., `puzzle1.jpg`). |
| **Rows** | Number | Number of horizontal rows of pieces. (Set via `StartGame` usually) |
| **Columns** | Number | Number of vertical columns of pieces. (Set via `StartGame` usually) |
| **BackgroundColor** | Color | The background color behind the puzzle pieces. |
| **BgPatternStyle** | Number | Background pattern style: `0` (None), `1` (Grid), `2` (Dots), `3` (Rhombus). |
| **PatternColor** | Color | Color of the background pattern lines or dots. |
| **PatternSpacing** | Number | Spacing between pattern elements (default: 100). |
| **CutoutStyle** | Number | Style of piece tabs/holes: `1` (Classic), `2` (Boxy), `3` (Round). |
| **EmbossThickness** | Number | Visual depth of the piece edges (1 to 10). |
| **ShowPreview** | Boolean | If true, shows a semi-transparent version of the full image behind the pieces. |
| **PreviewAlpha** | Number | Transparency of the preview image (0.0 to 1.0). |

### Methods (Functions)
| Block | Description |
| :--- | :--- |
| **Initialize(layout)** | Initializes the puzzle view inside the specified layout component (e.g., VerticalArrangement). **Must be called first.** |
| **StartGame(rows, columns)** | Generates a new puzzle with the specified grid size (e.g., 3x3, 5x5) using the current Image. |
| **Shuffle()** | Scatters the pieces randomly across the board. |
| **GetPieceCount()** | Returns the number of pieces currently on the board. |
| **StartTimer()** | Starts the internal game timer. |
| **StopTimer()** | Stops/Pauses the internal game timer. |
| **ResetTimer()** | Resets the timer to 0. |
| **GetElapsedTime()** | Returns the total elapsed time in seconds. |
| **ZoomIn()** | Zooms into the puzzle view. |
| **ZoomOut()** | Zooms out of the puzzle view. |
| **SetZoom(scale)** | Sets a specific zoom level (0.1 to 5.0). |
| **ResetView()** | Resets zoom and pan to the default centered view. |

### Events
| Event | Description |
| :--- | :--- |
| **PuzzleCompleted()** | Triggered when all pieces have been correctly joined. |
| **PieceMerged(remainingPieces)** | Triggered when two pieces snap together. Returns the count of remaining loose chunks. |
| **TimerUpdated(seconds)** | Triggered every second while the timer is running. Useful for updating a time display label. |

## Usage Example

### 1. Basic Setup
*   Add a **VerticalArrangement** to your screen (Width=Fill Parent, Height=Fill Parent). Rename it to `PuzzleContainer`.
*   Add the **JigsawPuzzle** extension.

### 2. specific Blocks
**When Screen1.Initialize:**
- call `JigsawPuzzle1.Initialize` (layout: `PuzzleContainer`)
- set `JigsawPuzzle1.Image` to `"my_image.png"`
- call `JigsawPuzzle1.StartGame` (rows: `3`, columns: `3`)
- call `JigsawPuzzle1.Shuffle`

**When JigsawPuzzle1.PuzzleCompleted:**
- Show a "You Win!" notifier.

**When ButtonZoomIn.Click:**
- call `JigsawPuzzle1.ZoomIn`

---
**Technical Support & Updates**
For support, contact TechHamara.
