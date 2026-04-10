# Design System Document: The Technical Partner

## 1. Overview & Creative North Star
This design system is built to transform a standard agency presence into a high-end technical consultancy. The goal is to move beyond the "SaaS template" aesthetic and into the realm of **Architectural Intelligence**.

### Creative North Star: "The Digital Architect"
The "Digital Architect" focuses on precision, depth, and structural clarity. Unlike standard layouts that rely on heavy borders and loud colors, this system uses **tonal depth** and **intentional asymmetry** to guide the eye. We prioritize breathing room (white space) and editorial-grade typography to signal authority. By overlapping elements and utilizing glassmorphism, we create an interface that feels like a sophisticated HUD (Heads-Up Display) for enterprise-level AI automation.

---

## 2. Colors & Surface Philosophy

The palette transitions from a standard corporate blue to a "Midnight Technical" aesthetic, utilizing deep navy tones and vibrant emerald accents to denote high-tech precision.

### The "No-Line" Rule
**Explicit Instruction:** Designers are prohibited from using 1px solid borders to define sections. Boundaries must be established through:
1.  **Background Color Shifts:** Moving from `surface` (#0b1326) to `surface_container_low` (#131b2e).
2.  **Tonal Transitions:** Using slight variations in the blue-dark spectrum to indicate content blocks.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of semi-transparent layers.
*   **Base:** `surface` (#0b1326) — The deep foundation.
*   **Low Elevation:** `surface_container_low` (#131b2e) — Primary section blocks.
*   **High Elevation:** `surface_container_highest` (#2d3449) — Interactive cards or focused modals.

### The "Glass & Gradient" Rule
To elevate the experience, floating elements (like Navigation Bars or Quick-Action Panels) should use **Glassmorphism**:
*   **Fill:** `surface_container` at 70% opacity.
*   **Effect:** Backdrop blur of 20px - 40px.
*   **Accent:** A subtle linear gradient from `primary` (#b4c5ff) to `primary_container` (#2563eb) at 15% opacity to give a "sheen" to the glass.

---

## 3. Typography: Editorial Authority

We use a high-contrast pairing of **Space Grotesk** for structural impact and **Inter** for functional clarity.

*   **Display (Space Grotesk):** Large, bold, and slightly tightened letter-spacing (-2%). Used for Hero sections to command immediate attention.
*   **Headlines (Space Grotesk):** Medium weights. These act as the "architectural markers" of the page.
*   **Body (Inter):** Highly legible, optimized for technical descriptions. We lean on `body-md` (0.875rem) for most content to maintain a sleek, modern feel.
*   **Labels (Inter):** All-caps with increased letter-spacing (+5%) for "technical metadata" tags.

**Hierarchy Strategy:** Typography isn't just for reading; it's for navigation. Use `display-lg` to break the grid, allowing text to overlap onto secondary surface containers to create visual "momentum."

---

## 4. Elevation & Depth

In this system, depth is a function of light and layering, not shadows alone.

### The Layering Principle
Achieve lift by nesting surface tiers. A `surface_container_lowest` card sitting on a `surface_container_low` background creates a "recessed" look, while a `surface_container_high` card on a `surface` background creates a "raised" look.

### Ambient Shadows
Traditional drop shadows are too "heavy" for this technical aesthetic. 
*   **Shadow Specs:** If a shadow is required, it must be `on_surface` color at 6% opacity, with a 32px blur and 16px Y-offset. This mimics soft ambient light.

### The "Ghost Border" Fallback
If contrast is required for accessibility:
*   **Requirement:** Use `outline_variant` (#434655) at 20% opacity. 
*   **Prohibition:** Never use 100% opaque borders.

---

## 5. Components

### Buttons
*   **Primary:** A vibrant gradient from `primary_container` (#2563eb) to a slightly darker custom blue. High-roundedness (`full`) to contrast against sharp card corners.
*   **Secondary:** Glass-style. `outline_variant` at 20% with a backdrop blur.
*   **CTA Accent:** Utilize `secondary` (#4edea3) sparingly for "Conversion" moments (e.g., "Book Audit").

### Cards & Lists
*   **Style:** No borders. Use `surface_container_low` for the card body. 
*   **Spacing:** Use a 32px or 48px internal padding to ensure "Premium Breathing Room."
*   **Interaction:** On hover, the card should shift to `surface_container_high` and scale by 1.02%—no harsh shadows.

### High-Tech Accents (Bespoke Components)
*   **Status Indicators:** Small, pulsing `secondary_fixed` (#4edea3) dots to indicate "Live AI Systems" or "Active Automations."
*   **Data Visualization Chips:** Use `tertiary_container` for small data-points or "AI Confidence" scores.

---

## 6. Do’s and Don’ts

### Do:
*   **Use Asymmetry:** Place a `display-lg` headline so it hangs off the edge of a container.
*   **Use Tonal Shifts:** Define sections by changing the background from `surface` to `surface_container_lowest`.
*   **Prioritize Icons:** Use thin-stroke, high-quality SVG icons in `primary` (#b4c5ff) to build technical trust.

### Don't:
*   **Don't use Dividers:** Never use a horizontal line to separate list items. Use 24px of vertical space or a subtle background hover state instead.
*   **Don't use Solid Black:** The darkest point should be `surface` (#0b1326). Pure black (#000000) feels "dead" and unrefined.
*   **Don't Over-Color:** Stick to the deep blues and whites. Reserve `secondary` (Green) and `tertiary` (Light Blue) for functional feedback and primary CTAs only.

---

## 7. Token Summary

*   **Corner Radius:** Standardized at `lg` (0.5rem) for cards and `full` (9999px) for buttons/chips.
*   **Typography:** Space Grotesk (Headings) / Inter (Body).
*   **Primary Action:** `primary_container` (#2563eb).
*   **Success/Trust:** `secondary` (#4edea3).