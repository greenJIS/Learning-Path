# Data Display Components

> This section covers all **BootstrapVue components for displaying tabular and structured data**, including tables, pagination, and sorting helpers.

---

## 1. `<b-table>`

**Purpose:** Display tabular data with sorting, filtering, and pagination support.

```vue
<b-table :items="items" :fields="fields" striped hover responsive />
```

**Key Props:**

- `items` – array of data objects
- `fields` – array of field keys or objects with label and formatter
- `striped`, `bordered`, `hover` – visual styles
- `responsive` – horizontal scrolling on small screens
- `sort-by`, `sort-desc` – default sorting

---

## 2. Table Scoped Slots

```vue
<b-table :items="items" :fields="fields">
  <template #cell(name)="data">
    <b-icon icon="person-circle" /> {{ data.value }}
  </template>
</b-table>
```

**Notes:**

- Customize cell content with scoped slots
- Ideal for adding icons, badges, or buttons

---

## 3. `<b-pagination>`

**Purpose:** Navigate large datasets.

```vue
<b-pagination v-model="currentPage" :total-rows="items.length" :per-page="10" />
```

**Props:**

- `v-model` – current page
- `total-rows` – total data rows
- `per-page` – items per page
- `size`, `align`, `variant`

---

## 4. `<b-pagination-nav>`

**Purpose:** Semantic pagination navigation.

```vue
<b-pagination-nav :number-of-pages="10" />
```

**Notes:**

- Generates page links only
- Works with router links

---

## 5. Sorting & Filtering

```vue
<b-table
  :items="items"
  :fields="fields"
  :sort-by.sync="sortBy"
  :filter="filterText"
/>
```

**Explanation:**

- `:sort-by.sync` allows reactive sorting
- `:filter` applies text search across all columns

---

## 6. `<b-badge>` in Tables

```vue
<b-table :items="items" :fields="fields">
  <template #cell(status)="data">
    <b-badge :variant="data.value === 'Active' ? 'success' : 'danger'">
      {{ data.value }}
    </b-badge>
  </template>
</b-table>
```

**Notes:**

- Display status labels, priority, or flags

---

## 7. Real-World Pattern: Paginated Table

```vue
<b-table :items="pagedItems" :fields="fields" striped hover>
</b-table>
<b-pagination v-model="currentPage" :total-rows="items.length" :per-page="10" />
```

**Notes:**

- Combines table + pagination for large data sets
- Minimal code, fully reactive

---

## 8. Real-World Pattern: Dashboard Data Cards with Table

```vue
<b-row>
  <b-col md="6" v-for="summary in summaries" :key="summary.id">
    <b-card :title="summary.title">
      <b-table :items="summary.items" small striped />
    </b-card>
  </b-col>
</b-row>
```

**Explanation:**

- Use in dashboards for multiple mini-tables
- Card + table combination provides clarity

---

## 9. Summary

- `b-table` is highly configurable for **sorting, filtering, and responsive design**
- Pair with `b-pagination` for large datasets
- Scoped slots allow embedding badges, buttons, icons, and custom components

---

**Next:** [`media.md`](./media.md)
