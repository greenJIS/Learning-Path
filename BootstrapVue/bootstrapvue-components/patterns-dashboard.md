# Dashboard UI Patterns

> This section covers **real-world dashboard layouts** using BootstrapVue components, including grids, cards, KPI widgets, and panels.

---

## 1. Grid of Cards

```vue
<b-container fluid>
  <b-row>
    <b-col md="3" v-for="widget in widgets" :key="widget.id">
      <b-card :title="widget.title" class="mb-4">
        <h3>{{ widget.value }}</h3>
        <p class="mb-0 text-muted">{{ widget.description }}</p>
      </b-card>
    </b-col>
  </b-row>
</b-container>
```

**Explanation:**

- Responsive 4-column grid on desktop
- Cards display KPIs or summary info
- Stacks vertically on mobile

---

## 2. Sidebar + Main Panel Layout

```vue
<b-container fluid>
  <b-row>
    <b-col cols="12" md="3">
      <b-card class="mb-4">Sidebar</b-card>
    </b-col>
    <b-col cols="12" md="9">
      <b-card class="mb-4">Main Dashboard Panel</b-card>
      <b-row>
        <b-col md="6">
          <b-card class="mb-4">Widget 1</b-card>
        </b-col>
        <b-col md="6">
          <b-card class="mb-4">Widget 2</b-card>
        </b-col>
      </b-row>
    </b-col>
  </b-row>
</b-container>
```

**Explanation:**

- Sidebar on left, main panel content on right
- Nested rows for widgets
- Fully responsive

---

## 3. KPI Cards with Icons

```vue
<b-row>
  <b-col md="3" v-for="kpi in kpis" :key="kpi.id">
    <b-card class="text-center">
      <b-icon :icon="kpi.icon" variant="primary" font-scale="2"></b-icon>
      <h4>{{ kpi.value }}</h4>
      <p class="text-muted mb-0">{{ kpi.label }}</p>
    </b-card>
  </b-col>
</b-row>
```

**Explanation:**

- Visual representation of KPIs with icons
- Use `b-icon` for instant recognition
- Horizontal grid with responsive stacking

---

## 4. Tabs in Dashboard Panels

```vue
<b-tabs>
  <b-tab title="Overview">
    <b-card>Overview content</b-card>
  </b-tab>
  <b-tab title="Analytics">
    <b-card>Analytics charts</b-card>
  </b-tab>
</b-tabs>
```

**Explanation:**

- Organize dashboard content in tabs
- Avoids long scrollable pages
- Tabs can be combined with cards and tables

---

## 5. Summary

- Dashboards use **cards, grids, tabs, and KPI widgets**
- Mobile-first and responsive layout with `<b-container>`, `<b-row>`, `<b-col>`
- Icons and text enhance visual comprehension
- Combine with tables and charts for detailed data panels

---

**Next:** [`patterns-tables.md`](./patterns-tables.md)
