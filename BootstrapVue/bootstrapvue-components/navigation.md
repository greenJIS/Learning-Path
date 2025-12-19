# Navigation Components

> This section covers all **BootstrapVue navigation-related components**, used for menus, tabs, breadcrumbs, and paginated navigation. Navigation is essential for structured apps, dashboards, and responsive websites.

---

## 1. `<b-navbar>`

**Purpose:** Responsive navigation header.

```vue
<b-navbar toggleable="lg" type="dark" variant="primary">
  <b-navbar-brand href="#">Brand</b-navbar-brand>
  <b-navbar-toggle target="nav-collapse" />
  <b-collapse id="nav-collapse" is-nav>
    <b-navbar-nav>
      <b-nav-item href="#">Home</b-nav-item>
      <b-nav-item href="#">About</b-nav-item>
    </b-navbar-nav>
  </b-collapse>
</b-navbar>
```

**Props:**

- `toggleable` – breakpoint for collapsing
- `type` – dark/light
- `variant` – color scheme

**Notes:**

- Fully responsive
- Slots allow custom content

---

## 2. `<b-nav>`

**Purpose:** Navigation container for links, tabs, or pills.

```vue
<b-nav pills>
  <b-nav-item active href="#">Home</b-nav-item>
  <b-nav-item href="#">Profile</b-nav-item>
</b-nav>
```

**Variants:**

- `tabs` or `pills`
- Horizontal or vertical

---

## 3. `<b-nav-item>` / `<b-nav-item-dropdown>`

**Purpose:** Single navigation links and dropdowns.

```vue
<b-nav-item-dropdown text="Menu" right>
  <b-dropdown-item href="#">Action 1</b-dropdown-item>
  <b-dropdown-item href="#">Action 2</b-dropdown-item>
</b-nav-item-dropdown>
```

**Notes:**

- Works with `b-nav` and `b-navbar`
- Dropdowns can be aligned left/right

---

## 4. `<b-tabs>` / `<b-tab>`

**Purpose:** Tabbed content interface.

```vue
<b-tabs>
  <b-tab title="Home" active>
    Home content
  </b-tab>
  <b-tab title="Profile">
    Profile content
  </b-tab>
</b-tabs>
```

**Props:**

- `active` – sets default active tab
- `lazy` – lazy load tab content
- `disabled` – disable tab

---

## 5. `<b-breadcrumb>`

**Purpose:** Show page hierarchy.

```vue
<b-breadcrumb
  :items="[
    { text: 'Home', href: '/' },
    { text: 'Library', href: '/library' },
    { text: 'Data', active: true },
  ]"
/>
```

**Notes:**

- Supports `active` state
- Improves UX in nested pages

---

## 6. `<b-pagination>`

**Purpose:** Navigation for paginated content.

```vue
<b-pagination v-model="currentPage" :total-rows="100" :per-page="10" />
```

**Notes:**

- Works with `b-table` or any data list
- Supports alignment and size variants

---

## 7. Real-World Pattern: Dashboard Sidebar

```vue
<b-nav vertical pills>
  <b-nav-item href="#">Dashboard</b-nav-item>
  <b-nav-item href="#">Users</b-nav-item>
  <b-nav-item-dropdown text="Reports">
    <b-dropdown-item href="#">Sales</b-dropdown-item>
    <b-dropdown-item href="#">Traffic</b-dropdown-item>
  </b-nav-item-dropdown>
</b-nav>
```

**Explanation:**

- Vertical sidebar menu
- Pills for active highlighting
- Dropdown for nested sections

---

## 8. Real-World Pattern: Top Navbar

```vue
<b-navbar toggleable="md" variant="light" type="light">
  <b-navbar-brand href="#">App</b-navbar-brand>
  <b-navbar-toggle target="nav-collapse" />
  <b-collapse id="nav-collapse" is-nav>
    <b-navbar-nav class="ml-auto">
      <b-nav-item href="#">Home</b-nav-item>
      <b-nav-item href="#">Profile</b-nav-item>
      <b-nav-item href="#">Settings</b-nav-item>
    </b-navbar-nav>
  </b-collapse>
</b-navbar>
```

**Explanation:**

- Responsive top navigation
- Collapses on mobile
- Right-aligned links

---

## Summary

- Navigation components are flexible and composable
- Combine `b-navbar`, `b-nav`, and `b-tabs` for all types of menus
- Use `b-breadcrumb` and `b-pagination` for enhanced UX

---

**Next:** [`forms.md`](./forms.md)
