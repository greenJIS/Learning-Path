# Layout Components

> This section covers all **BootstrapVue layout-related components and helpers**, built on top of the **Bootstrap 4 grid system**. These components are foundational for page structure, responsiveness, and alignment.

---

## 1. `<b-container>`

**Purpose:** Provides a responsive layout container.

### Variants

- Fixed-width (default)
- Fluid (`fluid` prop)

```vue
<b-container>
  <p>Fixed-width responsive container</p>
</b-container>

<b-container fluid>
  <p>Full-width container</p>
</b-container>
```

**Notes:**

- Adds horizontal padding automatically
- Required parent for `<b-row>`

---

## 2. `<b-row>`

**Purpose:** Creates a horizontal group of columns.

```vue
<b-row>
  <b-col>Column A</b-col>
  <b-col>Column B</b-col>
</b-row>
```

**Key Props**

- `no-gutters` – removes column padding
- Responsive gutter control via utilities

**Notes:**

- Uses Flexbox internally
- Must be a child of `<b-container>`

---

## 3. `<b-col>`

**Purpose:** Defines responsive grid columns.

```vue
<b-col cols="12" md="6" lg="4">
  Responsive column
</b-col>
```

**Key Props**

- `cols` – default width (1–12)
- `sm`, `md`, `lg`, `xl` – breakpoint widths
- `order`, `order-sm`, `order-md`
- `offset`, `offset-md`

**Notes:**

- Auto-sizes if no width is provided
- Can change order per breakpoint

---

## 4. Column Ordering

```vue
<b-row>
  <b-col order="2">Second</b-col>
  <b-col order="1">First</b-col>
</b-row>
```

**Explanation:**

- Useful for responsive reflow without DOM changes

---

## 5. Column Offsetting

```vue
<b-row>
  <b-col md="4" offset-md="4">Centered</b-col>
</b-row>
```

**Explanation:**

- Creates horizontal spacing using grid math

---

## 6. Responsive Alignment (Utilities)

While not components, alignment is essential to layout.

```vue
<b-row class="align-items-center justify-content-between">
  <b-col>Left</b-col>
  <b-col class="text-end">Right</b-col>
</b-row>
```

**Utilities Used:**

- `align-items-*`
- `justify-content-*`
- `text-*`

---

## 7. `<b-container-fluid>` (Alias)

```vue
<b-container fluid>
  <p>Equivalent to container-fluid</p>
</b-container>
```

**Explanation:**

- No separate component exists
- `fluid` prop replaces it

---

## 8. Real-World Pattern: Page Layout Skeleton

```vue
<b-container fluid>
  <b-row>
    <b-col cols="12" md="3">Sidebar</b-col>
    <b-col cols="12" md="9">Main Content</b-col>
  </b-row>
</b-container>
```

**Why this works:**

- Mobile-first stacking
- Desktop side-by-side layout
- No custom CSS required

---

## 9. Real-World Pattern: Centered Content

```vue
<b-container class="vh-100 d-flex align-items-center justify-content-center">
  <b-card>Centered Card</b-card>
</b-container>
```

**Explanation:**

- Common for auth pages
- Uses Flex utilities with layout components

---

## Summary

- Layout components are minimal but powerful
- Most behavior comes from **props + utilities**
- Always design mobile-first

---

**Next:** [`content.md`](./content.md)
