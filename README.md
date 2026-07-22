# Aether Learning | Student Progress Dashboard

A highly responsive, interactive single-page e-learning dashboard prototype demonstrating instant, real-time statistics updating using **only HTML5 and CSS3** (zero JavaScript).

## 🚀 Try It Now
To view the dashboard, simply open `index.html` directly in any modern web browser.
* Double-click the `index.html` file in your file explorer, OR
* Use a local server extension (e.g., Live Server in VS Code) to run it locally.

---

## 🛠️ How It Works (The Pure CSS State Machine)

To satisfy the constraint of having **no JavaScript**, this prototype utilizes the **CSS Checkbox Hack** (`:checked` state controller). 

### 1. State Mapping
* A hidden checkbox input `<input type="checkbox" id="update-toggle">` sits at the top level of the DOM.
* The **"Update Now"** button is marked up as a HTML `<label for="update-toggle">`. When a user clicks this label, it acts directly on the checkbox, toggling its checked state.

### 2. Sibling Selection & Styling Triggers
Using the CSS general sibling combinator (`~`), we capture the checkbox state and update the entire UI hierarchy dynamically:
```css
/* Update numbers, progress circles, charts, and unlock badges on check */
#update-toggle:checked ~ .dashboard-wrapper .stat-number-roll {
  transform: translateY(-50%); /* Roll numbers to updated values */
}
```

### 3. Key Interactive Transitions
* **Rolling Numbers**: The numbers (completed courses, pending assignments, badges) slide vertically using Hardware-Accelerated 3D transforms (`translateY`) to reveal the new values seamlessly.
* **XP Progress & Level Up Bubble**: The XP progress bar increases in width, and a floating green `+750 XP` indicator ascends and fades into view with a spring-like bounce.
* **Circular Progress Ring**: The courses ring SVG uses CSS transition on `stroke-dashoffset` to smoothly animate completion from `60%` to `75%`.
* **Lock-to-Unlock Badges**: Unsynced badges scale up and bounce using `@keyframes` sequential animations, fading out their lock padlock icon, removing their grayscale filters, and adding a neon color border and glow.
* **Weekly Bar Chart**: The Thursday and Friday bars grow from low initial levels to new peaks, with hover tooltips displaying updated metrics.
* **Milestone Activity Feed**: Two new activities ("Course Completed" and "Badge Earned") slide down and fade in at the top of the feed sequentially using stagger delays.
* **Notification Pulse**: The pulsing orange dot in the bell icon disappears, signifying that notification updates are synced.

---

## 🎨 Design System & Aesthetics
* **Theme**: Deep slate dark theme (`#0a0b10`) optimized for readability, with modern color-coded gradient schemes for categories (emerald green for completed, crimson red for pending, amber orange for badges).
* **Glassmorphism**: Sleek card layout using `backdrop-filter: blur()`, semi-transparent borders, and faint radial hover glows to reflect high-end dashboard design.
* **Typography**: Clean display headings using Google Fonts **Outfit** and body text using **Plus Jakarta Sans**.
* **Responsiveness**:
  * **Desktop (>= 1024px)**: Full layout with a comprehensive left-hand sidebar navigation.
  * **Tablet (768px - 1024px)**: Responsive sidebar collapsing into a space-efficient icon navigation layout, with stats forming a 2x2 grid.
  * **Mobile (< 768px)**: Optimized bottom-navigation dock (mobile-native format) and columns reflowing to single-stack panels for ergonomic thumb actions.
