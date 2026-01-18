# Maleks SWAP: Mobile-First UI/UX Plan

## 1. Core Philosophy: "Fluid & Native"
The previous design suffered from rigid grid structures that broke on smaller screens. The new approach adopts a **Fluid Card System**. The interface will not "shrink" to fit mobile; it will be *born* on mobile and expand for desktop.

### Key Principles
*   **Mobile-First Code**: CSS media queries will target *min-width* (desktop), not *max-width* (mobile). The default state is mobile.
*   **System-Native Aesthetics**: We will leverage the user's operating system design language (San Francisco on iOS, Roboto on Android) to feel like a native app.
*   **Zero-Latency Feel**: Interactions must feel instant. We will prioritize perceived performance over actual data freshness (show cached data immediately, update silently).

## 2. Performance Strategy (Speed)
To achieve the "fastest loading times" requested:

| Feature | Strategy | Benefit |
| :--- | :--- | :--- |
| **Typography** | Use System Fonts (`-apple-system`, `BlinkMacSystemFont`, `Roboto`) | **0ms Load Time**. No network request for font files. Text is visible instantly. |
| **Icons** | Inline SVG Symbols | No external icon font requests. Crisp at any size. |
| **Data** | `localStorage` + `stale-while-revalidate` | App loads instantly with last known rates. No "Loading..." spinners on repeat visits. |
| **Code** | Single-File Architecture | One HTML file containing critical CSS and JS. One network request total. |

## 3. UI/UX Layout: "Thumb-Zone" Design
Mobile screens are tall. We will place interactive elements where the thumb naturally rests.

### Structure
1.  **Header (Top)**: Minimal branding, simple "Settings" gear (for dark mode).
2.  **Ticker (Top)**: Slim, auto-scrolling ticker for live market context (Gold, Oil, BTC).
3.  **Main Stage (Center/Bottom)**:
    *   **Input Card**: Large, tappable currency selector. Big numeric keypad-friendly input.
    *   **Swap Action**: Floating Action Button (FAB) style, centered between inputs.
    *   **Result Card**: High-contrast output.
4.  **Navigation (Bottom)**: Fixed bottom tab bar for "Swap", "Stocks", "Insights".

## 4. Visual Style
*   **Color Palette**:
    *   **Light Mode**: Off-white background (`#F5F5F7`), White cards, Black text.
    *   **Dark Mode**: Deep gray background (`#000000`), Dark gray cards (`#1C1C1E`), White text.
    *   **Accent**: "Maleks Blue" (`#007AFF`) for primary actions (Apple-like blue).
*   **Shapes**: Large border-radius (20px) for a friendly, modern feel.
*   **Feedback**: Active states for all buttons (opacity change or scale) to confirm taps.

## 5. Technical Implementation Steps
1.  **Skeleton**: Build semantic HTML5 structure.
2.  **Style**: Write mobile CSS first. Add `@media (min-width: 768px)` only for desktop constraints (centering the app container).
3.  **Logic**: Implement vanilla JS for conversion, fetching, and caching.
4.  **PWA**: Add manifest and service worker for installability.

This plan addresses the "faulty layout" by removing complexity and addresses "loading times" by removing heavy assets.

## Update: Auto-Refresh & UI Polish v1.2
- **Logic**: Fetch new rates every **30 seconds**.
- **UX**: Add a **visual progress bar** (slim line at the top of the card) to indicate the next update.
- **UI**: Fix alignment of flags within input fields to ensure they are vertically centered and have proper breathing room.

## Update: Cleaner Refresh v1.3
- **Logic**: Change auto-refresh interval from 30s to **60 seconds**.
- **UI**: Remove the visual progress bar for a cleaner, less distracting interface. Updates will happen silently in the background.
