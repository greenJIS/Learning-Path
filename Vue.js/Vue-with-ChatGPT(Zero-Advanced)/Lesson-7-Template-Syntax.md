# VueJS - Zero to Advanced Learning Path

## Lesson 7 — Template Syntax

### Templates

Templates in Vue are declarative HTML-like structures that Vue compiles into DOM-rendering functions.

Key points:

- Templates must be **valid HTML**
- Templates support **Vue-specific syntax**
- All reactive state defined in `<script setup>` is accessible in the template

### Mustache Interpolation

For **basic data binding** in Vue.

Uses double curly braces `{{ }}` to display data.

Example:

```vue
<p>Hello, {{ name }}</p>
```

Supports inline expressions:

```vue
<p>{{ count + 2 }}</p>
<p>{{ user.age > 18 ? 'Adult' : 'Child' }}</p>
```

Anti-pattern: Avoid calling functions directly inside interpolation repeatedly.

```vue
{{ expensiveFunction(); }} // not recommended
```

### Attribute Bindings With `v-bind`

Use `v-bind` directive (or shorthand `:`) to bind attributes to dynamic data.

Example:

```vue
<img v-bind:src="imageUrl" alt="Dynamic Image">
```

Or using shorthand:

```vue
<img :src="imageUrl" alt="Dynamic Image">
```

Bind boolean attributes:

```vue
<button :disabled="isDisabled">Submit</button>
```

Bind objects:

```vue
<div v-bind="objectOfAttributes"></div>
```

Note: if `:src="src"` (both name same) then only `:src` will work.

### Binding Classes

**Object Syntax**

```vue
<div :class="{ active: isActive, 'text-large': isLargeText }"></div>
```

**Array Syntax**

```vue
<div :class="[classA, classB]"></div>
```

**Combining Both**

```vue
<div :class="[classA, { active: isActive }]"></div>
```

### Binding Styles

**Object Syntax**

```vue
<div :style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
```

**Array Syntax**

```vue
<div :style="[styleA, styleB]"></div>
```

**Combining Both**

```vue
<div :style="[styleA, { color: activeColor }]"></div>
```

### Using Expressions in Templates

Templates support expressions but **NOT statements**.

Not allowed:

```vue
{{ if (condition) { ... } }} // not allowed
```

Allowed:

```vue
{{ condition ? "Yes" : "No" }}
```

### Conditionals (`v-if` / `v-else` / `v-else-if`)

```vue
<p v-if="isLoggedIn">Welcome</p>
<p v-else>Login required</p>
```

Using groups with `template`:

```vue
<template v-if="loading">
  <p>Loading...</p>
  <Spinner />
</template>
```

v-show for toggling display only

```vue
<p v-show="isVisible">I toggle via CSS display</p>
```

Difference:

- `v-if` = removes/adds element from DOM
- `v-show` = always in DOM but hidden

### List Rendering (`v-for`)

```vue
<li v-for="item in items" :key="item.id">{{ item.name }}</li>
```

Access index

```vue
<li v-for="(item, index) in items" :key="index">
  {{ index }} - {{ item.name }}
</li>
```

Looping through objects

```vue
<div v-for="(value, key) in user" :key="key">
  {{ key }}: {{ value }}
</div>
```

`v-for` + `v-if` (avoid)

Not recommended:

```vue
<li v-for="item in items" v-if="item.show"></li>
```

Better:

```vue
<li v-for="item in items.filter((i) => i.show)"></li>
```

### Template Refs

Refs allow template elements to be directly accessed in script.

```vue
<template>
  <input ref="inputRef" />
</template>

<script setup>
import { ref, onMounted } from "vue";

const inputRef = ref(null);

onMounted(() => {
  inputRef.value.focus();
});
</script>
```

Use cases:

- Focus control
- Working with canvas
- Accessing 3rd-party libraries

**Common Template Anti-Patterns**

- Complex JS logic inside templates
- Long chained expressions
- Using functions inside `v-for`
- Applying `v-if` and `v-for` on the same element
- Excessive nested templates

**Practical Patterns**

Pattern 1: Conditional Classes

```vue
<button :class="['btn', isLoading && 'loading']"></button>
```

Pattern 2: Dynamic component tag

```vue
<component :is="componentType"></component>
```

Pattern 3: Template for conditional blocks

```vue
<template v-if="shouldRender">
  <Section />
  <Footer />
</template>
```

### Mini Project — Dynamic User List UI

Requirements

- Render a list of users with `v-for`
- Show badges based on conditions
- Bind conditional classes
- Use template refs to focus an input when adding new users

```vue
<template>
  <div>
    <input ref="inputRef" v-model="newUser" />
    <button @click="addUser">Add</button>

    <ul>
      <li v-for="user in users" :key="user.id" :class="{ active: user.active }">
        {{ user.name }} <span v-if="user.active">(Active)</span>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const users = ref([
  { id: 1, name: "Alice", active: true },
  { id: 2, name: "Bob", active: false },
]);

const newUser = ref("");
const inputRef = ref(null);

function addUser() {
  if (!newUser.value) return;
  users.value.push({ id: Date.now(), name: newUser.value, active: false });
  newUser.value = "";
  inputRef.value.focus();
}

onMounted(() => {
  inputRef.value.focus();
});
</script>
```

Explanation: This Vue component demonstrates how to use template refs to directly access and manipulate DOM elements. The input field is focused both when the component is mounted and after a new user is added. The list of users is rendered dynamically with conditional classes and badges based on their active status.
