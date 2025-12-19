# Button Components

> This section documents **BootstrapVue button components**, including types, variants, sizes, icons, groups, and real-world UI patterns.

---

## 1. `<b-button>`

**Purpose:** Standard BootstrapVue button.

```vue
<b-button variant="primary" size="lg">Primary Button</b-button>
```

**Props:**

- `variant` – `primary`, `secondary`, `success`, `danger`, `warning`, `info`, `light`, `dark`, `link`
- `size` – `sm`, `lg`, default
- `disabled` – boolean
- `block` – full-width button

---

## 2. Button with Icon

```vue
<b-button variant="success">
  <b-icon icon="check" /> Submit
</b-button>
```

**Notes:**

- Combine `b-icon` for visual indicators
- Supports all variants and sizes

---

## 3. Outline Buttons

```vue
<b-button variant="primary" outline>Primary Outline</b-button>
```

- Outline style uses `outline` prop
- Works with all color variants

---

## 4. Button Groups

```vue
<b-button-group>
  <b-button variant="primary">Left</b-button>
  <b-button variant="secondary">Middle</b-button>
  <b-button variant="success">Right</b-button>
</b-button-group>
```

- Horizontal button group
- Can be vertical using `vertical` prop

---

## 5. Toggle Buttons

```vue
<b-button-group toggle>
  <b-button v-model="selected" variant="primary">Option 1</b-button>
  <b-button v-model="selected" variant="secondary">Option 2</b-button>
</b-button-group>
```

- Supports `v-model` for active state
- Ideal for filter options or segmented controls

---

## 6. Link Buttons

```vue
<b-button href="/home" variant="link">Go Home</b-button>
```

- Styled as button but behaves as anchor
- Supports router links via `to` prop

---

## 7. Real-World Pattern: Form Actions

```vue
<b-form-group>
  <b-button variant="primary" type="submit">Save</b-button>
  <b-button variant="secondary" type="reset">Cancel</b-button>
</b-form-group>
```

- Primary for main action, secondary for cancel/reset
- Common in forms and modal dialogs

---

## 8. Real-World Pattern: Button Toolbar

```vue
<b-button-toolbar class="mb-3">
  <b-button-group class="mr-2">
    <b-button variant="primary">Bold</b-button>
    <b-button variant="primary">Italic</b-button>
  </b-button-group>
  <b-button-group>
    <b-button variant="success">Save</b-button>
  </b-button-group>
</b-button-toolbar>
```

- Toolbar for grouped actions
- Supports multiple groups and spacing utilities

---

## Summary

- `b-button` is versatile with **variants, sizes, block/full-width, outline**
- Combine with `b-icon` for visual context
- Use groups and toggle for segmented controls and toolbars

---

**Next:** [`feedback-overlays.md`](./feedback-overlays.md)
