# VueJS - Zero to Advanced Learning Path

## Lesson 2 — Vue Application Basics & Reactivity

### Vue Application Structure

A Vue application is created by calling:

```vue
const app = Vue.createApp({ ...options })
```

Then mounted to an element:

```vue
app.mount('#app')
```

### The Root Component

This is your primary configuration object:

```js
const app = Vue.createApp({
  data() {
    return {
      message: "Welcome to Vue Lesson 2",
      count: 0,
      isActive: false,
    };
  },
  methods: {
    increment() {
      this.count++;
    },
  },
});
```

Sections of a Vue component

| Section    | Purpose                       |
| ---------- | ----------------------------- |
| `data()`   | Stores reactive variables     |
| `methods`  | Functions triggered by events |
| `computed` | Derived state                 |
| `watch`    | Side effects                  |
| `template` | The UI structure              |

### Understanding Vue’s Reactivity System

Vue uses **Proxy-based reactivity**.

What does that mean?

When you create a Vue component:

```js
return { count: 0 };
```

Vue wraps count in a Proxy so that:

- Vue knows when it's _read_ (dependency tracking)
- Vue knows when it's _written to_ (trigger updates)

You never manipulate the DOM directly. Vue updates it automatically.

### Template Syntax

Vue templates support:

- Text interpolation: `<h1>{{ message }}</h1>`
- Attribute binding: `js <img :src="imageUrl" :alt="description" />`
- Event handling: `<button @click="increment">Click me</button>`
- Conditionals: `<div v-if="isActive">Active</div>`
- Loops: `<li v-for="item in items" :key="item.id">{{ item.name }}</li>`
- Inline Expressions: `<p>{{ count + 1 }}</p>`

### Vue Directives

- `v-bind`: Binds attributes to expressions.
  ```vue
  <a v-bind:href="url">Link</a>
  ```
- `v-model`: Two-way data binding for form inputs.

  ```vue
  <input v-model="message" />
  ```

- `v-on`: Attaches event listeners.

  ```vue
  <button v-on:click="increment">Click me</button>
  ```

### Conditional Rendering

- `v-if`: Renders element based on condition.

  ```vue
  <div v-if="isActive">Active</div>
  ```

- `v-else` and `v-else-if`: For else conditions.

  ```vue
  <div v-if="isActive">Active</div>
  <div v-else>Inactive</div>
  ```

- `v-show`: Toggles visibility with CSS.

  ```vue
  <div v-show="isActive">Visible</div>
  ```

when to use what?

| Directive | Behavior              | Best Use          |
| --------- | --------------------- | ----------------- |
| v-if      | Adds/removes from DOM | Expensive toggles |
| v-show    | Toggles CSS display   | Frequent toggles  |

### List Rendering with `v-for`

- Looping Arrays

  ```vue
  <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  ```

- Looping Objects

  ```vue
  <div v-for="(value, key) in object" :key="key">
    {{ key }}: {{ value }}
  </div>
  ```

- Looping a Range

  ```vue
  <div v-for="n in 5" :key="n">
    Number {{ n }}
  </div>
  ```

Note: **Importance of `key` attribute**: for performance and correct rendering.

### Methods

- Methods are used for actions.

  ```js
  methods: {
    toggleActive() {
      this.isActive = !this.isActive
    },
    reset() {
      this.count = 0
    }
  }
  ```

Rules:

- Methods run every time they are called
- Use for event handling, updating state
- Should avoid heavy computation (use computed instead)

### Mini Project — Interactive Todo List

- Template

  ```vue
  <div id="app">
    <h1>Todo List</h1>
    <input v-model="newTodo" placeholder="Add a todo" @keyup.enter="addTodo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
  ```

- App Logic

  ```js
  const app = Vue.createApp({
    data() {
      return {
        newTodo: "",
        todos: [],
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== "") {
          this.todos.push(this.newTodo.trim());
          this.newTodo = "";
        }
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      },
    },
  });

  app.mount("#app");
  ```

### Common Mistakes

- Mistake 1 — Forgetting data() must return an object

  - Incorrect:
    ```js
    data: {
      message: "Hello";
    }
    ```
  - Correct:
    ```js
    data() {
      return {
        message: "Hello";
      };
    }
    ```

- Mistake 2 — Using arrow functions inside methods

  - Incorrect:
    ```js
    methods: {
      increment: () => {
        this.count++;
      };
    }
    ```
  - Correct:
    ```js
    methods: {
      increment() {
        this.count++;
      }
    }
    ```
    Note: Arrow functions do not bind their own `this`.

- Mistake 3 — Forgetting keys in `v-for`

  - Incorrect:
    ```vue
    <li v-for="item in items">{{ item.name }}</li>
    ```
  - Correct:
    ```vue
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    ```
    Note: Always provide a unique `key` for better performance and correct rendering.
