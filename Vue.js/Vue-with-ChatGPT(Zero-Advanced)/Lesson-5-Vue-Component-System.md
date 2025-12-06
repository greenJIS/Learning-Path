# VueJS - Zero to Advanced Learning Path

## Lesson 5 — Vue Component System

Components are **reusable**, **encapsulated UI units** that help you:

- Organize large applications
- Split UI into maintainable parts
- Reuse logic and styling
- Improve scalability in complex interfaces

Example of a Vue component:

```vue
<!-- UserCard.vue -->
<template>
  <div class="user-card">
    <h2>{{ name }}</h2>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    name: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.user-card {
  border: 1px solid #ccc;
  padding: 16px;
  border-radius: 8px;
}
</style>
```

### Component Registration

Components can be registered **globally** or **locally**.

- **Global Registration**: Available throughout the app.

  ```js
  import Vue from "vue";
  import UserCard from "./components/UserCard.vue";

  Vue.component("UserCard", UserCard);
  ```

- **Local Registration**: Available only within a specific component.

  ```vue
  <script setup>
  import MyButton from "./MyButton.vue";
  </script>

  <template>
    <MyButton label="Click" />
  </template>
  ```

### Props (Data Input for Components)

Props allow passing data from a parent component to a child component.

Basic props usage:

```vue
<script>
const props = defineProps(["title", "count"]);
</script>
```

Props with type & default

```vue
<script>
const props = defineProps({
  title: { type: String, required: true },
  count: { type: Number, default: 0 },
});
</script>
```

Best practices

- Avoid passing deeply nested objects
- Keep prop API simple and predictable
- Use clear naming: **isActive**, **items**, **user**, **variant**

### Emitting Events (Child → Parent)

Events communicate upwards.

1. Basic example

```vue
<script>
const emit = defineEmits(["increase"]);

function handleClick() {
  emit("increase");
}
</script>
```

2. Emitting with payload

```vue
<script>
emit("update:modelValue", newValue);
</script>
```

3. Typed events (recommended)

```vue
<script>
const emit = defineEmits<{
  (e: "increase"): void;
  (e: "update:modelValue", value: string): void;
}>();
</script>
```

### Component Communication Patterns

- **Parent** → **Child**: Props
- **Child** → **Parent**: Events
- **Sibling** ↔ **Sibling**: Lift state up or use a store
- **Deep Component Chains**: Provide/Inject
- **Global State**: Pinia or Vuex (not required for small apps)

### Slots — The Most Powerful Component Feature

Slots allow parent components to pass **template content** into children.

1. **Default Slot**

   ```vue
   <template>
     <Card>
       <p>This is inside the slot</p>
     </Card>
   </template>
   ```

2. **Named Slots**

   ```vue
   <Card>
   <template #header> Title </template>
   <template #footer> Footer Text </template>
   </Card>
   ```

3. **Scoped Slots**

   Allows children to expose data to parents.

   ```vue
   <ItemList :items="items">
   <template #default="{ item }">
   <strong>{{ item.name }}</strong>
   </template>
   </ItemList>
   ```

### One-Way Data Flow

Vue enforces **one-way binding** for predictable UI behavior.

Child components:

- Receive props (read-only)
- Must never mutate props directly

Anti-pattern:

```js
props.count++; // WRONG
```

Correct approach:

```js
emit("update:count", props.count + 1);
```

### Component Best Practices

- Keep components small and focused
- One component = one responsibility
- Name components consistently
  - `BaseButton.vue`
  - `AppHeader.vue`
  - `ProductCard.vue`
- Avoid passing unnecessary props
- Favor composition over duplication
- Keep component folder structures predictable

### Mini Project — Reusable Card + Button UI System

**Requirements**:

- Build two components: **AppButton** and **AppCard**
- Card must support header, content, footer slots
- Button should emit a **click** event and take props (**variant**, **label**)

**Example Structure**:

```sh
src/components/
├─ AppButton.vue
└─ AppCard.vue
```

**AppCard.vue**:

```vue
<template>
  <div class="card">
    <header><slot name="header" /></header>
    <main><slot /></main>
    <footer><slot name="footer" /></footer>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ddd;
  padding: 16px;
  border-radius: 8px;
}
</style>
```

**AppButton.vue**:

```vue
<script setup>
const props = defineProps({
  label: String,
  variant: { type: String, default: "primary" },
});
const emit = defineEmits(["click"]);
</script>

<template>
  <button :class="variant" @click="emit('click')">
    {{ label }}
  </button>
</template>

<style scoped>
.primary {
  background: black;
  color: white;
  padding: 8px 12px;
}
.secondary {
  background: gray;
  color: white;
  padding: 8px 12px;
}
</style>
```

Explanation: The AppButton component accepts two props: `label` for the button text and `variant` to determine the button style (primary or secondary). It emits a `click` event when the button is clicked. The styles are scoped to the component, providing distinct appearances for primary and secondary variants.
