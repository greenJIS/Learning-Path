# BootstrapVue Utility Classes (Bootstrap 4)

> BootstrapVue does **not introduce custom utility classes**. It fully relies on **Bootstrap 4 utility classes**, which can be used directly inside Vue templates.

This document groups utilities **by similarity** and explains each category for quick reference in GitHub documentation.

## 1. Spacing Utilities (Margin & Padding)

| Type    | Class Pattern    | Example          | Description                                           |
| ------- | ---------------- | ---------------- | ----------------------------------------------------- |
| Margin  | `m{side}-{size}` | `mt-3`           | Adds margin to a specific side                        |
| Padding | `p{side}-{size}` | `px-4`           | Adds padding to a specific side                       |
| Sides   | `t b l r x y`    | `mx-auto`        | Target top, bottom, left, right, horizontal, vertical |
| Sizes   | `0–5`, `auto`    | `mb-0`, `m-auto` | Spacing scale using rem values                        |

**Common Usage**

```html
<div class="mt-4 px-3 mx-auto"></div>
```

## 2. Display Utilities

| Class            | Description                        |
| ---------------- | ---------------------------------- |
| `d-none`         | Hides element                      |
| `d-block`        | Block display                      |
| `d-inline`       | Inline display                     |
| `d-inline-block` | Inline block display               |
| `d-flex`         | Enables Flexbox                    |
| `d-grid`         | Enables CSS Grid (limited support) |

### Responsive Display

```html
<div class="d-none d-md-block"></div>
```

| Prefix | Breakpoint |
| ------ | ---------- |
| `sm`   | ≥576px     |
| `md`   | ≥768px     |
| `lg`   | ≥992px     |
| `xl`   | ≥1200px    |

## 3. Flexbox Utilities

### Flex Direction & Wrapping

| Class         | Description       |
| ------------- | ----------------- |
| `flex-row`    | Horizontal layout |
| `flex-column` | Vertical layout   |
| `flex-wrap`   | Allow wrapping    |
| `flex-nowrap` | Disable wrapping  |

### Alignment

| Class                     | Description           |
| ------------------------- | --------------------- |
| `justify-content-start`   | Align left            |
| `justify-content-center`  | Center horizontally   |
| `justify-content-between` | Space between items   |
| `align-items-center`      | Center vertically     |
| `align-self-end`          | Align individual item |

## 4. Text Utilities

| Category  | Class             | Description            |
| --------- | ----------------- | ---------------------- |
| Alignment | `text-start`      | Left aligned           |
| Alignment | `text-center`     | Center aligned         |
| Alignment | `text-end`        | Right aligned          |
| Transform | `text-uppercase`  | Uppercase text         |
| Transform | `text-lowercase`  | Lowercase text         |
| Transform | `text-capitalize` | Capitalized text       |
| Wrapping  | `text-wrap`       | Allow text wrapping    |
| Wrapping  | `text-nowrap`     | Prevent wrapping       |
| Overflow  | `text-truncate`   | Truncate with ellipsis |

## 5. Color Utilities

### Text Colors

| Class            | Meaning             |
| ---------------- | ------------------- |
| `text-primary`   | Primary theme color |
| `text-secondary` | Secondary color     |
| `text-success`   | Success state       |
| `text-danger`    | Error state         |
| `text-warning`   | Warning state       |
| `text-info`      | Informational       |
| `text-light`     | Light text          |
| `text-dark`      | Dark text           |
| `text-muted`     | Muted text          |

### Background Colors

| Class        | Meaning            |
| ------------ | ------------------ |
| `bg-primary` | Primary background |
| `bg-success` | Success background |
| `bg-danger`  | Danger background  |
| `bg-warning` | Warning background |
| `bg-info`    | Info background    |
| `bg-light`   | Light background   |
| `bg-dark`    | Dark background    |

## 6. Sizing Utilities

| Category | Class    | Description    |
| -------- | -------- | -------------- |
| Width    | `w-25`   | 25% width      |
| Width    | `w-50`   | 50% width      |
| Width    | `w-75`   | 75% width      |
| Width    | `w-100`  | Full width     |
| Height   | `h-25`   | 25% height     |
| Height   | `h-50`   | 50% height     |
| Height   | `h-100`  | Full height    |
| Max      | `mw-100` | Max width 100% |

## 7. Position Utilities

| Class               | Description          |
| ------------------- | -------------------- |
| `position-static`   | Default position     |
| `position-relative` | Relative positioning |
| `position-absolute` | Absolute positioning |
| `position-fixed`    | Fixed position       |
| `position-sticky`   | Sticky position      |

### Offsets

| Class      | Description     |
| ---------- | --------------- |
| `top-0`    | Align to top    |
| `bottom-0` | Align to bottom |
| `start-0`  | Align left      |
| `end-0`    | Align right     |

## 8. Border Utilities

| Category | Class            | Description     |
| -------- | ---------------- | --------------- |
| Border   | `border`         | Add border      |
| Border   | `border-0`       | Remove border   |
| Border   | `border-top`     | Top border only |
| Color    | `border-primary` | Colored border  |
| Radius   | `rounded`        | Rounded corners |
| Radius   | `rounded-circle` | Circular shape  |
| Radius   | `rounded-pill`   | Pill shape      |

## 9. Visibility & Overflow

| Category   | Class             | Description               |
| ---------- | ----------------- | ------------------------- |
| Visibility | `visible`         | Visible element           |
| Visibility | `invisible`       | Hidden but occupies space |
| Overflow   | `overflow-hidden` | Hide overflow             |
| Overflow   | `overflow-auto`   | Scroll when needed        |

## 10. Shadow Utilities

| Class         | Description    |
| ------------- | -------------- |
| `shadow-none` | No shadow      |
| `shadow-sm`   | Small shadow   |
| `shadow`      | Default shadow |
| `shadow-lg`   | Large shadow   |

## 11. Interaction Utilities

| Class              | Description            |
| ------------------ | ---------------------- |
| `user-select-none` | Disable text selection |
| `user-select-all`  | Select all text        |
| `pe-none`          | Disable pointer events |
| `pe-auto`          | Enable pointer events  |

## 12. Accessibility Utilities

| Class               | Description        |
| ------------------- | ------------------ |
| `sr-only`           | Screen-reader only |
| `sr-only-focusable` | Visible on focus   |

## Notes

- Fully compatible with **BootstrapVue components**
- Responsive and mobile-first
- Prefer utilities before custom CSS

---
