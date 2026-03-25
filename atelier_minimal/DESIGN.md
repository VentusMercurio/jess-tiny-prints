# Design System Specification: The Curated Gallery

## 1. Overview & Creative North Star
**Creative North Star: The Digital Curator**
This design system moves away from the "e-commerce template" and toward the "editorial exhibition." It treats the screen not as a functional grid, but as a physical gallery wall where art is given room to breathe. The system is built on **Intentional Asymmetry** and **Tonal Depth**, breaking the rigid verticality of standard web design. We favor overlapping elements, generous "museum-grade" whitespace, and high-contrast typography to elevate Jess' Tiny Prints from a shop to an experience.

## 2. Colors & Surface Philosophy
The palette is rooted in organic, tactile materials—unbleached paper, charcoal, and botanical dyes.

### Palette Highlights
- **Foundation:** `surface` (#fbf9f1) acts as our gallery wall.
- **Accents:** `primary` (#4e635a - Sage) and `secondary` (#78564e - Muted Earth) provide a sophisticated, grounded contrast.
- **Typography:** `on_surface` (#1b1c17) is a soft charcoal, avoiding the harshness of pure black.

### The "No-Line" Rule
To maintain a high-end feel, **1px solid borders are prohibited for sectioning.** Physical boundaries must be defined through:
1. **Background Shifts:** A section of `surface_container_low` sitting atop a `surface` background.
2. **Whitespace:** Utilizing the upper ends of our spacing scale (`16` to `24`) to create "void-based" separation.

### Surface Hierarchy & Nesting
Treat the UI as a series of stacked fine-art papers.
- **Level 0 (Base):** `surface`
- **Level 1 (Sections):** `surface_container_low` or `surface_container`
- **Level 2 (Interactive Elements):** `surface_container_highest` or `surface_container_lowest` for cards that need to "pop" forward or "recede" back.

### The "Glass & Gradient" Rule
For floating navigation or modal overlays, use **Glassmorphism**. Apply a semi-transparent `surface` color (80% opacity) with a `20px` backdrop-blur. For primary CTAs, use a subtle linear gradient from `primary` to `primary_container` to add a tactile, "ink-on-paper" depth.

## 3. Typography
The typographic voice is an interplay between the traditional (Serif) and the contemporary (Sans-Serif).

*   **Display & Headlines (`notoSerif`):** These are our "title cards." Use `display-lg` for hero statements with tight letter-spacing to emphasize the high-contrast strokes of the serif.
*   **Body & Titles (`manrope`):** Our "curatorial notes." The sans-serif must always be set with generous line-height (1.6x) to ensure the text feels as light as the art it describes.
*   **Labels (`manrope`):** Use `label-md` in all-caps with `0.1rem` letter-spacing for metadata (e.g., "LIMITED EDITION," "8x10 PRINT").

## 4. Elevation & Depth
We eschew traditional drop shadows in favor of **Tonal Layering**.

*   **The Layering Principle:** Depth is achieved by placing a `surface_container_lowest` card on a `surface_container_low` background. This creates a "natural lift" without the "dirty" look of grey shadows.
*   **Ambient Shadows:** If a floating element (like a shopping bag) requires a shadow, use a `24px` blur at 4% opacity. The shadow color must be a tinted version of `on_surface` (#1b1c17), never pure black.
*   **The Ghost Border:** If a container needs a frame (e.g., a print preview), use the `outline_variant` token at **15% opacity**. This creates a "suggestion" of a border rather than a hard line.

## 5. Components

### Buttons
*   **Primary:** Solid `primary` background with `on_primary` text. Use `DEFAULT` (0.25rem) roundedness. No shadows.
*   **Secondary:** Ghost style. No background, `outline` border at 20% opacity, `primary` text.
*   **States:** On hover, primary buttons should shift to `primary_container` with a subtle `0.5rem` lift via ambient shadow.

### Cards & Lists
*   **The Gallery Card:** Forbid divider lines. Use `spacing-6` (2rem) of vertical whitespace between items. Images should always be the hero; text should be secondary and left-aligned.
*   **Selection Chips:** Use `secondary_fixed` for selected states and `surface_container_high` for unselected. Corners should be `full` (pill-shaped).

### Input Fields
*   **Style:** Minimalist. Only a bottom border using `outline_variant` at 40% opacity. Upon focus, the border transitions to `primary` at 100% opacity.
*   **Labels:** Floating `label-md` that rests just above the input line, never inside the box.

### Curated Components (New)
*   **The "Matte" Frame:** A component for displaying Jess' prints. It uses a `surface_container_lowest` inner area with a wide `surface_container_high` border (simulating a physical picture frame matte).
*   **Editorial Pull-Quote:** Using `display-sm` in `secondary` color, center-aligned, used to break up long blocks of text with artist insights.

## 6. Do's and Don'ts

### Do
*   **Use Asymmetry:** Offset an image to the right while its description sits lower on the left.
*   **Embrace the Void:** If a page feels "empty," don't fill it. Whitespace is a luxury brand's best friend.
*   **Layer Surfaces:** Use `surface_container_lowest` for elements that users can interact with (buttons, cards).

### Don't
*   **No Hard Outlines:** Never use 100% opaque borders for cards or sections.
*   **No Standard Grids:** Avoid 12-column grids that force items into perfect rows. Let images vary in height like a gallery wall.
*   **No "Pure" Shadows:** Never use the default CSS `box-shadow: 0 2px 4px rgba(0,0,0,0.5)`. It destroys the organic feel of the cream palette.