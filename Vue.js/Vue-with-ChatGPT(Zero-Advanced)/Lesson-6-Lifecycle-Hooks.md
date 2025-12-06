# VueJS - Zero to Advanced Learning Path

## Lesson 6 — Lifecycle Hooks

Lifecycle hooks allow you to run logic **during specific stages** of a component’s existence.

- Every Vue component goes through a predictable series of phases:
  - **Creation** (before DOM exists)
  - **Mounting** (DOM exists)
  - **Updating** (reactive change triggers re-render)
  - **Unmounting** (component removed)
- Lifecycle hooks allow you to register functions that run at these stages.

**Lifecycle Diagram (Simplified)**

```plaintext
beforeCreate
    ↓
  created
      ↓
    beforeMount
        ↓
      mounted
          ↓
        beforeUpdate
            ↓
          updated
              ↓
            beforeUnmount
                ↓
              unmounted
```

**Lifecycle Hooks Summary Table**

| Hook            | When It Runs                        | Common Uses                                     |
| --------------- | ----------------------------------- | ----------------------------------------------- |
| onBeforeCreate  | Right after instance initialization | Set up initial data, event listeners            |
| onCreated       | After instance is created           | Fetch initial data, set up reactivity           |
| onBeforeMount   | Before mounting to the DOM          | Last chance to modify data before render        |
| onMounted       | After component is mounted          | DOM-dependent operations, third-party libraries |
| onBeforeUpdate  | Before re-render due to data change | Access current DOM state before update          |
| onUpdated       | After re-render due to data change  | Post-update DOM operations, side effects        |
| onBeforeUnmount | Before component is unmounted       | Cleanup tasks, remove event listeners           |
| onUnmounted     | After component is unmounted        | Final cleanup tasks                             |

Note: All hooks come from Vue’s Composition API and can be imported from 'vue':

```vue
<script setup>
import { onMounted, onUnmounted } from "vue";

onMounted(() => {
  console.log("Component has been mounted!");
});
onUnmounted(() => {
  console.log("Component has been unmounted!");
});
</script>
```

### Major Lifecycle Hooks

1. **`onMounted`**

- Runs when:
  - Component is fully rendered
  - DOM is accessible
- Common uses:
  - API calls
  - Accessing DOM elements
  - Starting intervals or timeouts
- Example:

```vue
<script setup>
import { onMounted, ref } from "vue";

const data = ref(null);

onMounted(async () => {
  const response = await fetch("https://api.example.com/data");
  data.value = await response.json();
});
</script>
```

2. **`onUnmounted`**

- Runs when:
  - Component is removed from DOM
- Common uses:
  - Cleanup tasks
  - Removing event listeners
  - Clearing intervals or timeouts
- Example:

```vue
<script setup>
import { onUnmounted } from "vue";

onUnmounted(() => {
  console.log("Component has been unmounted!");
});
</script>
```

3. **`onBeforeUpdate`** & **`onUpdated`**

- Runs when:
  - Reactive data changes
- Common uses:
  - Accessing DOM before/after updates
- Example:

```vue
<script setup>
import { onBeforeUpdate, onUpdated } from "vue";

onBeforeUpdate(() => {
  console.log("Component is about to update!");
});

onUpdated(() => {
  console.log("Component has been updated!");
});
</script>
```

### Full Execution Order Example

```js
onBeforeMount(() => console.log("beforeMount"));
onMounted(() => console.log("mounted"));
onBeforeUpdate(() => console.log("beforeUpdate"));
onUpdated(() => console.log("updated"));
onBeforeUnmount(() => console.log("beforeUnmount"));
onUnmounted(() => console.log("unmounted"));
```

### Real-World Patterns

P**attern 1**: Fetch API on mount

```js
onMounted(async () => {
  user.value = await fetchUser();
});
```

**Pattern 2**: Window event listeners

```js
function handleResize() {
  console.log(window.innerWidth);
}

onMounted(() => window.addEventListener("resize", handleResize));
onUnmounted(() => window.removeEventListener("resize", handleResize));
```

**Pattern 3**: Timer cleanup

```js
let timer;

onMounted(() => {
  timer = setInterval(() => count.value++, 1000);
});

onUnmounted(() => clearInterval(timer));
```

**Pattern 4**: LocalStorage persistence

```js
onBeforeUnmount(() => {
  localStorage.setItem("form", JSON.stringify(form.value));
});
```

**Common Mistakes to Avoid**

- Using `onMounted` for logic that doesn’t need the DOM
- Forgetting to clean up intervals or listeners → memory leaks
- Calling `async` code without `await` → inconsistent UI
- Doing API calls inside `setup()` instead of `onMounted()`
- Relying on DOM state before it’s ready → errors
- Overusing lifecycle hooks instead of Vue’s reactivity system
- Mixing Options API and Composition API lifecycle hooks

### Mini Project — Scroll Tracker Component

Goal: Build a component that:

- Tracks scroll position
- Updates a reactive variable
- Cleans up listener on unmount

```vue
<template>
  <div>
    <p>Scroll Y: {{ scrollY }}</p>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const scrollY = ref(0);

function handleScroll() {
  scrollY.value = window.scrollY;
}

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>
```

Explanation: This component tracks the vertical scroll position of the window. It uses the `onMounted` lifecycle hook to add a scroll event listener when the component is mounted, updating the `scrollY` reactive variable. The `onUnmounted` hook removes the event listener to prevent memory leaks when the component is destroyed.
