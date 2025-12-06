# VueJS - Zero to Advanced Learning Path

## Lesson 1 — What is Vue.js

progressive, incrementally adoptable JavaScript framework used to build user interfaces and single-page applications (SPAs)

### Section 1 - Core Principles

a. **Declarative Rendering**: You describe _what_ the UI should look like, and Vue handles _how_ it updates.
Example:

```html
<div id="app">{{ message }}</div>
```

Note: _Vue automatically updates the DOM when data changes_

b. **Component-Based Architecture**: Build encapsulated components that manage their own state and logic. UI is built from small, isolated, reusable components, i.e. Header, Sidebar, Card, Button, Pages etc. Each component has its own: **Template**, **Script**, **Styles**.

c. **Reactive Data System**: Vue tracks data dependencies via a proxy-based reactivity system. When reactive data changes, the UI updates _automatically_. This allows you to focus on _logic_, not manual DOM manipulation.

### Section 2 - Vue Ecosystem

Vue is not just a framework. It is an ecosystem of tools:
| **Package** | **Purpose** |
|----------|----------|
| **Vue Core** | _The runtime framework_ |
| **Vue Router** | _SPA navigation_ |
| **Pinia** | _State management_ |
| **Vite** | _Development server + bundler_ |
| **DevTools** | _Inspector inside browser_ |
| **SFC** | _Compiler .vue file compiler_ |

### Section 3 - Creating a Vue App

Using CDN:

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

<div id="app">
  <h1>{{ message }}</h1>
</div>

<script>
  const { createApp } = Vue;
  createApp({
    data() {
      return {
        message: "Hello, Vue!",
      };
    },
  }).mount("#app");
</script>
```

Explanation:

- `createApp()` creates a Vue instance.
- `data()` returns the reactive properties.
- `{{ message }}` binds to DOM.
- Updating `message` updates UI instantly.

### Section 4 - Vue Directives (Foundation of Vue Templates)

Vue directives are special attributes prefixed with `v-` that provide reactive behavior to the DOM.

a. **v-bind**: Dynamically bind attributes to expressions.

```html
<img v-bind:src="imageUrl" />
<!-- Shorthand -->
<img :src="imageUrl" />
```

b. **v-model**: Two-way data binding for form `input`s.

```html
<input v-model="username" placeholder="Enter your name" />
<p>Your name is: {{ username }}</p>
```

c. **v-if / v-else-if / v-else**: Conditional rendering.

```html
<div v-if="isLoggedIn">Welcome back!</div>
<div v-else>Please log in.</div>
```

d. **v-for**: Render lists based on an array.

```html
<ul>
  <li v-for="item in items" :key="item.id">{{ item.name }}</li>
</ul>
```

e. **v-on**: Event handling.

```html
<button v-on:click="increment">Click me</button>
<!-- Shorthand -->
<button @click="increment">Click me</button>
```

f. **v-show**: Toggle element visibility via CSS `display`.

```html
<div v-show="isVisible">This is visible</div>
```

g. **v-pre**: Skip compilation for this element and its children.

```html
<div v-pre>{{ rawContent }}</div>
```

h. **v-cloak**: Keep element hidden until Vue instance is ready.

```html
<div v-cloak>{{ message }}</div>
```

i. **v-once**: Render element/component only once.

```html
<div v-once>{{ message }}</div>
```

### Section 5 - Styling in Vue

a. Inline Style Binding

```html
<div :style="{ color: activeColor, fontSize: fontSize + 'px' }">
  Styled Text
</div>
```

b. Class Binding

```html
<div :class="{ active: isActive, 'text-large': isLargeText }">
  Class Bound Text
</div>
```

c. Scoped Styles in Single File Components (SFC)

```vue
<template>
  <div class="scoped-text">This text is scoped</div>
</template>
<style scoped>
.scoped-text {
  color: blue;
}
</style>
```

Note: Scoped styles apply only to this component.

### Section 6 - Common Errors & Fixes

- Error: "Property not defined on instance"
  - **Cause**: Trying to access a property that is not defined in the component's data or setup function.
  - **Fix**: Ensure property is defined in `data()` or `setup()`.
- Error: Template Syntax Error
  - **Cause**: Invalid syntax in template (e.g., missing closing tags).
  - **Fix**: Check template for syntax errors.
  - Also, **Vue templates allow only one root element**.

### Section 7 - Mini Project — Interactive Counter

Create a simple counter app with increment and decrement buttons.

```vue
<template>
  <div class="counter-app">
    <h1>Counter: {{ count }}</h1>
    <button @click="decrement">-</button>
    <button @click="increment">+</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const count = ref(0);

    const increment = () => {
      count.value++;
    };

    const decrement = () => {
      count.value--;
    };

    return { count, increment, decrement };
  },
};
</script>

<style scoped>
.counter-app {
  text-align: center;
  margin-top: 50px;
}
button {
  font-size: 20px;
  margin: 5px;
  padding: 10px 20px;
}
</style>
```

Explanation:

- `ref(0)` creates a reactive `count` variable initialized to `0`.
- `increment` and `decrement` functions modify `count`.
- Buttons call these functions on click.
- The UI updates automatically when `count` changes.
