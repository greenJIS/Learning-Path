# Content Components

> This section documents all **BootstrapVue content-related components**, used for structuring and presenting information. These components are heavily used in marketing pages, dashboards, lists, and detail views.

---

## 1. `<b-card>`

**Purpose:** A flexible content container with optional header, footer, images, and actions.

```vue
<b-card title="Project Overview" sub-title="Last updated today">
  <p class="mb-0">This card contains summary information.</p>
</b-card>
```

### Common Props

- `title`, `sub-title`
- `header`, `footer`
- `img-src`, `img-alt`, `img-top`, `img-bottom`
- `no-body`

### Slots

- `header`, `footer`, `img`, default

**Usage Notes:**

- Prefer slots for complex headers
- Combine with utility classes for spacing

---

## 2. Card Subcomponents

### `<b-card-header>` / `<b-card-body>` / `<b-card-footer>`

```vue
<b-card>
  <b-card-header>Header</b-card-header>
  <b-card-body>Main content</b-card-body>
  <b-card-footer>Footer actions</b-card-footer>
</b-card>
```

**Explanation:**

- Provides semantic separation
- Useful for dashboards and forms

---

## 3. `<b-list-group>`

**Purpose:** Displays lists of content items.

```vue
<b-list-group>
  <b-list-group-item active>Active item</b-list-group-item>
  <b-list-group-item>Item</b-list-group-item>
</b-list-group>
```

### Variants

- `flush`
- Contextual variants (`variant="success"`)

**Usage Notes:**

- Supports links and buttons
- Ideal for menus and sidebars

---

## 4. `<b-media>`

**Purpose:** Aligns media (image/icon) alongside content.

```vue
<b-media>
  <template #aside>
    <b-img src="avatar.png" rounded="circle" />
  </template>
  <h6>User Name</h6>
  <p class="mb-0">Comment text</p>
</b-media>
```

**Usage Notes:**

- Common in comments, activity feeds

---

## 5. `<b-img>`

**Purpose:** Responsive image wrapper.

```vue
<b-img src="image.jpg" fluid alt="Responsive image" />
```

### Key Props

- `fluid`, `fluid-grow`
- `thumbnail`
- `rounded`, `rounded-circle`
- `lazy`

**Explanation:**

- Automatically applies Bootstrap image styles

---

## 6. `<b-icon>`

**Purpose:** SVG icon rendering (Bootstrap Icons).

```vue
<b-icon icon="check-circle" variant="success" />
```

**Notes:**

- Requires `BootstrapVueIcons` plugin
- Supports size, animation, rotation

---

## 7. `<b-jumbotron>`

**Purpose:** Hero-style content section.

```vue
<b-jumbotron header="Welcome" lead="This is a hero section">
  <b-button variant="primary">Get Started</b-button>
</b-jumbotron>
```

**Usage Notes:**

- Common on landing pages
- Deprecated in Bootstrap 5 but valid here

---

## 8. `<b-badge>`

**Purpose:** Small count or label indicator.

```vue
<b-badge variant="info">New</b-badge>
```

**Usage Notes:**

- Combine with headings or buttons

---

## 9. `<b-avatar>`

**Purpose:** Displays user avatar.

```vue
<b-avatar src="user.jpg" variant="primary" />
```

**Explanation:**

- Supports images, initials, icons

---

## 10. Typography Helpers

### `<b-lead>`

```vue
<b-lead>This is lead text</b-lead>
```

### `<b-blockquote>`

```vue
<b-blockquote>
  Quoted content
</b-blockquote>
```

---

## 11. Real-World Pattern: Card Grid

```vue
<b-row>
  <b-col md="4" v-for="item in items" :key="item.id">
    <b-card :title="item.title" class="mb-4">
      {{ item.description }}
    </b-card>
  </b-col>
</b-row>
```

**Why this works:**

- Responsive grid
- Minimal markup
- Highly reusable

---

## 12. Real-World Pattern: Activity Feed

```vue
<b-list-group>
  <b-list-group-item v-for="log in logs" :key="log.id">
    <b-media>
      <template #aside>
        <b-avatar :text="log.user[0]" />
      </template>
      <strong>{{ log.user }}</strong> {{ log.action }}
    </b-media>
  </b-list-group-item>
</b-list-group>
```

---

## Summary

- Content components focus on **readability and composition**
- Slots provide maximum flexibility
- Combine with layout and utilities for best results

---

**Next:** [`navigation.md`](./navigation.md)
