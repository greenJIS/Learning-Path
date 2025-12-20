# Utilities and Helper Components

> This section documents **BootstrapVue utility components, helpers, directives, and plugins** for enhanced UI interactions.

---

## 1. Directives

### `v-b-tooltip`

```vue
<b-button v-b-tooltip.hover title="Tooltip text">Hover Me</b-button>
```

- Shows tooltip on hover/focus
- Can use triggers: `hover`, `click`, `focus`

### `v-b-popover`

```vue
<b-button
  v-b-popover.hover.click
  title="Popover"
  content="More info"
>Click Me</b-button>
```

- Displays rich popover content
- Supports HTML in content

### `v-b-modal`

```vue
<b-button v-b-modal.modal1>Open Modal</b-button>
<b-modal id="modal1">Modal Content</b-modal>
```

- Opens modal by ID
- Supports dynamic content

### `v-b-toggle`

```vue
<b-button v-b-toggle.collapse1>Toggle Collapse</b-button>
<b-collapse id="collapse1">Hidden content</b-collapse>
```

- Toggles collapse or accordion components

---

## 2. Helper Components

### `<b-link>`

```vue
<b-link href="#">Clickable Link</b-link>
```

- Styled anchor tag
- Supports `router-link` usage

### `<b-icon>`

- Already covered in content, reusable anywhere
- Props: `icon`, `variant`, `font-scale`, `rotation`

---

## 3. Plugins

### Toast

```vue
this.$bvToast.toast('Message', { title: 'Notification', variant: 'success',
solid: true })
```

- Displays toast notifications
- Configurable position, auto-hide, variant

### Modal

- Can open programmatically: `this.$bvModal.show('modal-id')`
- Supports static backdrop, scrollable content

### Popover

- Can open programmatically: `this.$bvPopover.show(target)`
- Supports triggers and HTML content

---

## 4. Utility Classes in Vue [🔗](../_BootstrapVue-Utility-Classes.md)

- Spacing: `m-1`, `mt-2`, `px-3`
- Display: `d-flex`, `d-none`, `d-md-block`
- Text: `text-center`, `text-primary`
- Flex: `justify-content-between`, `align-items-center`
- Borders & rounding: `rounded`, `border`, `border-top`

```vue
<b-card class="mb-3 p-3 text-center rounded">Card</b-card>
```

- Combine utilities with components for rapid layouts

---

## 5. Real-World Pattern: Tooltip + Popover Buttons

```vue
<b-button v-b-tooltip.hover title="Tooltip!">Hover</b-button>
<b-button
  v-b-popover.hover
  title="Popover"
  content="Extra info"
>Click</b-button>
```

- Quick info overlays
- Used in dashboards, tables, and forms

---

## 6. Real-World Pattern: Toast Notifications

```vue
<b-button @click="showToast">Notify</b-button>
<script>
export default {
  methods: {
    showToast() {
      this.$bvToast.toast("Action successful", {
        variant: "success",
        solid: true,
      });
    },
  },
};
</script>
```

- Feedback for user actions
- Auto-dismissed and colored variants

---

## Summary

- Directives and helpers **extend interactivity** without custom JS
- Plugins (`Toast`, `Modal`, `Popover`) **simplify feedback/UI overlays**
- Utility classes combine with components for **fast, consistent styling**

---

**Next:** Real-world UI patterns Markdown files ([`patterns-auth.md`](./patterns-auth.md), [`patterns-dashboard.md`](./patterns-dashboard.md), [`patterns-tables.md`](./patterns-tables.md))
