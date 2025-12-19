# Feedback and Overlay Components

> This section covers **alerts, toasts, modals, popovers, and tooltips** in BootstrapVue, with examples and real-world UI patterns.

---

## 1. `<b-alert>`

```vue
<b-alert show variant="success" dismissible>
  Action completed successfully!
</b-alert>
```

- `show` – controls visibility
- `variant` – color: `success`, `danger`, `warning`, etc.
- `dismissible` – can be closed by user

---

## 2. Toast Notifications

```vue
<b-button @click="showToast">Show Toast</b-button>
<script>
export default {
  methods: {
    showToast() {
      this.$bvToast.toast("Data saved successfully", {
        title: "Notification",
        variant: "success",
        solid: true,
      });
    },
  },
};
</script>
```

- Auto-dismissed notifications
- Configurable position, variant, title, solid/outline style

---

## 3. `<b-modal>`

```vue
<b-button v-b-modal.modal1>Open Modal</b-button>
<b-modal id="modal1" title="Modal Title">
  <p class="my-4">Modal content goes here.</p>
</b-modal>
```

- Controlled via `v-b-modal` directive or programmatically
- Supports dynamic content, scrollable content, and size variants

---

## 4. `<b-popover>`

```vue
<b-button
  v-b-popover.hover.click
  title="Popover"
  content="Extra info"
>Hover or Click Me</b-button>
```

- Supports hover, click, or focus triggers
- Can include HTML content and title
- Can be programmatically shown/hidden

---

## 5. `<b-tooltip>`

```vue
<b-button v-b-tooltip.hover title="Tooltip text">Hover Me</b-button>
```

- Simple hover or focus tooltip
- Customizable placement: `top`, `bottom`, `left`, `right`

---

## 6. Real-World Pattern: Dismissible Alerts

```vue
<b-alert v-model="showAlert" variant="warning" dismissible>
  Please check your input.
</b-alert>
<b-button @click="showAlert = true">Show Alert</b-button>
```

- Alerts can be toggled with `v-model`
- Supports any variant

---

## 7. Real-World Pattern: Modal Confirmation

```vue
<b-button
  variant="danger"
  @click="$bvModal.show('confirm-modal')"
>Delete</b-button>
<b-modal
  id="confirm-modal"
  title="Confirm Delete"
  ok-title="Yes"
  cancel-title="No"
  @ok="deleteItem"
>
  Are you sure you want to delete this item?
</b-modal>
```

- Confirmation dialogs for critical actions
- OK/Cancel buttons with events

---

## 8. Real-World Pattern: Popover Help Icons

```vue
<b-icon-question-circle
  v-b-popover.hover
  title="Help"
  content="More info about this field"
/>
```

- Inline help for forms or dashboards
- Non-intrusive guidance for users

---

## 9. Summary

- **Alerts** for messages and validation feedback
- **Toasts** for notifications
- **Modals** for dialogs and confirmations
- **Popovers & Tooltips** for inline guidance and extra info
- Combine with buttons, icons, and forms for interactive UIs

---

**Next:** [`data-display.md`](./data-display.md)
