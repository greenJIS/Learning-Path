# VueJS - Zero to Advanced Learning Path

## Lesson 8 — List Rendering (`v-for`)

List rendering is one of the most powerful and frequently used features in Vue. Nearly every app you build will involve dynamic lists: **tables**, **menus**, **grids**, **cards**, **filtered lists**, **virtualized lists**, etc.

### Basic Syntax of `v-for`

The `v-for` directive is used to render a list of items based on an array. The basic syntax is as follows:

**Array Loop**

```vue
<li v-for="item in items" :key="item.id">
  {{ item.name }}
</li>
```

**Access item and index**

```vue
<li v-for="(item, index) in items" :key="item.id">
  {{ index }} - {{ item.name }}
</li>
```

**Binding dynamic data**

```vue
<div v-for="product in products" :key="product.id">
  {{ product.name }} — {{ product.price }}
</div>
```

### Why `key` Matters

Vue needs `stable identity` for each item when updating lists.

**Good Keys**

- Unique IDs
- Database primary keys

**Bad Keys**

- Array index (causes buggy state reuse)
- Random numbers (changes every render)

**Correct Example**

```vue
<div v-for="todo in todos" :key="todo.id">
  {{ todo.text }}
</div>
```

**Incorrect Example**

```vue
<div v-for="todo in todos" :key="Math.random()"></div>
```

**Consequences of wrong keys**

- Input fields keep wrong values
- Animations break
- DOM state mismatch

### Iterating Objects

You can also use `v-for` to iterate over the properties of an object.

```vue
<div v-for="(value, key) in user" :key="key">
  {{ key }}: {{ value }}
</div>
```

Order is not guaranteed unless using `Object.entries()` first.

### Iterating Numbers

You can iterate over a range of numbers using `v-for`.

```vue
<div v-for="n in 10" :key="n">
  Number {{ n }}
</div>
```

Generates 10 iterations: 1 → 10.

### Nested `v-for`

You can nest `v-for` directives to create more complex structures.

```vue
<div v-for="(category, i) in categories" :key="category.id">
  <h3>{{ category.name }}</h3>

  <li v-for="(item, j) in category.items" :key="item.id">
    {{ item.label }}
  </li>
</div>
```

Always give **unique keys per level**.

### Combining `v-for` with `v-if`

_Never use them on the same element_.

**Bad**

```vue
<li v-for="item in items" v-if="item.inStock"></li>
```

**Good**

```vue
<li v-for="item in items" :key="item.id">
  <template v-if="item.inStock">
    {{ item.name }}
  </template>
</li>
```

Or pre-filter the array:

```vue
<li v-for="item in inStockItems" :key="item.id"></li>
```

### Common Transform Patterns

- **Filtering**:

```vue
<li v-for="item in items.filter((i) => i.available)">
  {{ item.name }}
</li>
```

- **Sorting**:

```vue
<li v-for="item in items.slice().sort((a, b) => a.name.locale.Compare(b.name))">
  {{ item.name }}
</li>
```

- **Mapping**:

```vue
<li v-for="title in items.map((i) => i.title)">
  {{ title }}
</li>
```

- **Grouping (computed)**:

```js
computed: {
  groupedItems() {
    return this.items.reduce((groups, item) => {
      const group = item.category;
      if (!groups[group]) groups[group] = [];
      groups[group].push(item);
      return groups;
    }, {});
  }
}
```

### Performance Considerations

1. Avoid large lists directly (Use pagination or virtualization if)

- More than 500+ items
- Heavy DOM inside items

2. Stable keys improve diffing

- Good keys reduce re-renders.

3. Computed transforms are cached

- Filtering/sorting should happen in computed.

### Real-World List UI Implementations

1. **Todo List**

```vue
<li v-for="todo in todos" :key="todo.id">
  <input type="checkbox" v-model="todo.done"> {{ todo.text }}
</li>
```

2. **Product Grid**

```vue
<div class="grid">
  <Card
    v-for="product in products"
    :key="product.sku"
    :data="product"
  />
</div>
```

3. **Dynamic Menu**

```vue
<li v-for="link in nav" :key="link.href">
  <RouterLink :to="link.href">{{ link.label }}</RouterLink>
</li>
```

4. **Chat Messages**

```vue
<div v-for="message in messages" :key="message.timestamp">
  <strong>{{ message.user }}</strong>: {{ message.text }}
</div>
```

### Mini Project — Dynamic Student List Manager

**Features**

- Add a student
- Remove a student
- Sort alphabetically
- Filter by grade

**Template**

```vue
<input v-model="newStudent" placeholder="Name" />
<button @click="add">Add</button>
<h3>Students</h3>
<li v-for="student in filteredAndSorted" :key="student.id">
  {{ student.name }} — {{ student.grade }}
  <button @click="remove(student.id)">X</button>
</li>
```

**Script**

```js
import { ref, computed } from "vue";

const newStudent = ref("");
const students = ref([
  { id: 1, name: "Aisha", grade: "A" },
  { id: 2, name: "Rafi", grade: "B" },
]);

const add = () => {
  if (!newStudent.value.trim()) return;
  students.value.push({
    id: Date.now(),
    name: newStudent.value,
    grade: ["A", "B", "C"][Math.floor(Math.random() * 3)],
  });
  newStudent.value = "";
};

const remove = (id) => {
  students.value = students.value.filter((s) => s.id !== id);
};

const filteredAndSorted = computed(() => {
  return students.value
    .filter((s) => s.grade !== "C")
    .sort((a, b) => a.name.localeCompare(b.name));
});
```

Explanation: This mini project demonstrates dynamic list rendering with adding, removing, sorting, and filtering functionalities using `v-for` in Vue.js.
