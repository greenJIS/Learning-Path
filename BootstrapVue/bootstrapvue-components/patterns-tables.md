# Table UI Patterns

> This section demonstrates **real-world table patterns** using BootstrapVue, including sortable, filterable, paginated tables and integrations with cards and dashboards.

---

## 1. Basic Table

```vue
<b-table :items="items" :fields="fields" striped hover responsive />
```

**Explanation:**

- Simple table with hover and striped styling
- Responsive for small screens

---

## 2. Table with Scoped Slots

```vue
<b-table :items="users" :fields="fields">
  <template #cell(name)="data">
    <b-avatar :text="data.value[0]" variant="primary" size="2rem" /> {{ data.value }}
  </template>
  <template #cell(status)="data">
    <b-badge :variant="data.value === 'Active' ? 'success' : 'danger'">{{ data.value }}</b-badge>
  </template>
</b-table>
```

**Explanation:**

- Use scoped slots to add avatars and badges
- Enhances readability and UI aesthetics

---

## 3. Paginated Table

```vue
<b-table :items="pagedItems" :fields="fields" striped hover />
<b-pagination v-model="currentPage" :total-rows="items.length" :per-page="10" />
```

**Explanation:**

- Combines table and pagination
- Works well for large datasets

---

## 4. Sortable and Filterable Table

```vue
<b-form-input v-model="filterText" placeholder="Search" class="mb-3" />
<b-table
  :items="items"
  :fields="fields"
  :filter="filterText"
  :sort-by.sync="sortBy"
  striped
  hover
/>
```

**Explanation:**

- `:filter` provides global search
- `:sort-by.sync` enables reactive sorting

---

## 5. Table within Dashboard Cards

```vue
<b-row>
  <b-col md="6" v-for="card in dataCards" :key="card.id">
    <b-card :title="card.title">
      <b-table :items="card.items" small striped hover />
    </b-card>
  </b-col>
</b-row>
```

**Explanation:**

- Embed tables inside cards for dashboards
- Supports multiple cards in a grid layout

---

## 6. Real-World Pattern: Activity Feed Table

```vue
<b-table :items="logs" :fields="['user', 'action', 'date']" striped hover>
  <template #cell(user)="data">
    <b-avatar :text="data.value[0]" size="2rem" class="mr-2" /> {{ data.value }}
  </template>
</b-table>
```

**Explanation:**

- Combines avatars with table rows for user activity logs
- Useful in admin panels and dashboards

---

## Summary

- Real-world tables leverage **scoped slots, badges, avatars, sorting, filtering, and pagination**
- Can be integrated with cards and dashboard layouts for better UX
- Fully responsive and mobile-friendly

---

**Next:** README index file to link all generated Markdown documentation.
