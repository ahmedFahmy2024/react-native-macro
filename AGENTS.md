# Expo HAS CHANGED

Read the exact versioned docs at https://docs.expo.dev/versions/v55.0.0/ before writing any code.

## Expo Workspace Rules & Best Practices

### 1. Navigation & Expo Router
* **Clean Layout Structure:**
  - Keep `_layout.tsx` files minimal, using them strictly for navigation definition (e.g. Tab systems or Stack structures).
  - Prefer modern tab grouping using the `(tabs)` directory pattern.
  - Disable default platform headers using `headerShown: false` and create custom, premium headers inside your screens for full design flexibility.

### 2. Styling (Tailwind CSS v4 & NativeWind v5)
* **CSS-First Styling:**
  - We use Tailwind CSS v4 and NativeWind v5. Under this setup, **do NOT use babel.config.js** for Tailwind configuration.
  - Load all tailwind layers in `src/global.css` using standard `@import` statements.
  - Wrap essential elements (`View`, `Text`, `Pressable`, `ScrollView`) using `useCssElement` from `react-native-css` to support high-performance utility className structures.
  - Use platform-specific media queries in CSS (`@media ios`, `@media android`) for custom platform styles and colors (e.g. `platformColor()` on iOS, `light-dark()` fallbacks on other platforms).

### 3. Native Data Fetching
* **Standard Fetching Hooks:**
  - Prefer robust hooks (e.g., TanStack Query, SWR) over inline `useEffect` fetching.
  - Implement full support for memory caching, automatic retry on network failure, offline sync, and state revalidation.
  - Design visual loading skeleton interfaces, empty states, and custom Error Boundary pages.

### 4. Fluid Motion & Touch Gestures
* **Native Reanimated Worklets:**
  - Use `react-native-reanimated` for smooth, responsive animations.
  - Ensure all layout and gesture transitions run purely on the Native UI thread using Worklets to keep the JS thread free and running at a constant 60 FPS.
