# VueJS - Zero to Advanced Learning Path

## Lesson 4 — Vue Computed Properties and Watchers

### Computed Properties

Computed properties are derived state—values computed from other reactive variables.

Computed properties exist:

- To avoid duplicating logic inside templates
- To make heavy calculations efficient through caching
- To automatically update when dependencies change

Example:

```vue
<template>
  <div>
    <h1>Full Name: {{ fullName }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: "John",
      lastName: "Doe",
    };
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
  },
};
</script>
```

In this example, `fullName` is a computed property that concatenates `firstName` and `lastName`. It will automatically update whenever either of those data properties change.

### Computed vs methods

| Feature | Computed                     | Methods                     |
| ------- | ---------------------------- | --------------------------- |
| Cached  | Yes                          | No                          |
| Re-runs | Only when dependency changes | Every time template renders |
| Use for | Derived state                | Imperative logic            |

Example difference:

```vue
<template>
  <div>
    <h1>Full Name (Computed): {{ fullName }}</h1>
    <h1>Full Name (Method): {{ getFullName() }}</h1>
  </div>
</template>
```

```vue
<script>
export default {
  data() {
    return {
      firstName: "John",
      lastName: "Doe",
    };
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
  },
  methods: {
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
  },
};
</script>
```

In this example, `fullName` is cached and only recalculated when `firstName` or `lastName` change, while `getFullName()` runs every time the template renders.

### Watchers

Watchers let you perform actions in response to reactive changes.

They are ideal for:

- API calls
- Form validation
- Side effects
- Delayed/debounced operations

Basic watcher example:

```vue
<template>
  <div>
    <input v-model="question" placeholder="Ask a question" />
    <p>{{ answer }}</p>
  </div>
</template>
```

```vue
<script>
export default {
  data() {
    return {
      question: "",
      answer: "I cannot give you an answer until you ask a question!",
    };
  },
  watch: {
    question(newQuestion) {
      this.answer = "Thinking...";
      this.getAnswer(newQuestion);
    },
  },
  methods: {
    getAnswer(question) {
      // Simulate an API call
      setTimeout(() => {
        this.answer = `You asked: ${question}`;
      }, 1000);
    },
  },
};
</script>
```

### Watchers: Deep, Immediate, and Multiple Sources

1. **Deep Watchers**

   Used for nested objects:

   ```js
   const user = ref({ name: "John", age: 20 });

   watch(
     user,
     () => {
       console.log("User changed");
     },
     { deep: true }
   );
   ```

2. **Immediate Watchers**

   Run the handler immediately on setup:

   ```js
   watch(
     search,
     (val) => {
       console.log("Initial run + changes:", val);
     },
     { immediate: true }
   );
   ```

3. **Watching Multiple Sources**

   ```js
   const first = ref("A");
   const last = ref("B");

   watch([first, last], ([newFirst, newLast]) => {
     console.log("Either changed:", newFirst, newLast);
   });
   ```

### Computed vs Watch — When to Use Which

Use **computed** when:

- You need derived state
- No side effects needed
- You want caching

Use **watch** when:

- You need side effects (API calls, timers, logging)
- You need async operations
- You need to react to but not display the value

Performance Considerations:

- Computed properties drastically improve performance due to caching
- Watchers can cause too many triggers if used incorrectly
- Avoid deep watchers unless necessary
- Avoid doing expensive logic inside template expressions

### Real‑World Patterns

1. **Debounced search API call**

   ```js
   let timeout;
   watch(search, (value) => {
     clearTimeout(timeout);
     timeout = setTimeout(() => {
       fetch(`/api/search?q=${value}`);
     }, 400);
   });
   ```

2. **Form auto‑saving**

   ```js
   watch(formData, () => saveToLocalStorage(formData.value), {
     deep: true,
   });
   ```

3. **Computed filtering**

   ```js
   const filtered = computed(() => {
     return items.value.filter((i) => i.done === false);
   });
   ```

### Mini Project — Reactive Search Filter (Computed + Watch)

**Requirements**

- A list of items
- A search field
- Computed property filters items
- Watcher logs search keyword changes

```vue
<template>
  <div>
    <input v-model="search" placeholder="Search items..." />
    <ul>
      <li v-for="item in filteredItems" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>
```

```vue
<script>
export default {
  data() {
    return {
      search: "",
      items: [
        { id: 1, name: "Apple" },
        { id: 2, name: "Banana" },
        { id: 3, name: "Orange" },
        { id: 4, name: "Grapes" },
      ],
    };
  },
  computed: {
    filteredItems() {
      return this.items.filter((item) =>
        item.name.toLowerCase().includes(this.search.toLowerCase())
      );
    },
  },
  watch: {
    search(newSearch) {
      console.log("Search changed to:", newSearch);
    },
  },
};
</script>
```
