# VueJS - Zero to Advanced Learning Path

## Lesson 9 - Forms & `v-model`

`v-model` creates **two‑way binding**:

- Updates the UI when data changes
- Updates data when the user types

Example:

```vue
<input v-model="name" />
<p>Hello, {{ name }}</p>
```

Internally, this expands to:

```vue
<input :value="name" @input="name = $event.target.value" />
```

### `v-model` with Different Input Types

- **Text Field**

```vue
<input v-model="username" />
```

- **Textarea**

```vue
<textarea v-model="bio"></textarea>
```

- **Checkbox (Boolean)**

```vue
<input type="checkbox" v-model="isSubscribed" />
```

- **Checkbox (Array)**

```vue
<input type="checkbox" value="JavaScript" v-model="skills" />
<input type="checkbox" value="Python" v-model="skills" />
<input type="checkbox" value="PHP" v-model="skills" />
```

skills becomes an array of selected values.

- **Radio Buttons**

```vue
<input type="radio" value="male" v-model="gender" />
<input type="radio" value="female" v-model="gender" />
```

- **Select (Single)**

```vue
<select v-model="country">
  <option value="bd">Bangladesh</option>
  <option value="in">India</option>
</select>
```

- **Select (Multiple)**

```vue
<select v-model="selectedTags" multiple>
  <option value="vue">Vue</option>
  <option value="react">React</option>
  <option value="svelte">Svelte</option>
</select>
```

### Modifiers

- `.trim`

Automatically removes whitespace.

```vue
<input v-model.trim="username" />
```

- `.number`

Converts input to a number.

```vue
<input v-model.number="age" />
```

- `.lazy`

Updates on blur, not every keystroke.

```vue
<input v-model.lazy="email" />
```

### Custom Components with `v-model`

`v-model` works with child components using the `modelValue` prop and the `update:modelValue` event.

_Child Component_

```vue
<script setup>
defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue"]);
</script>

<input
  :value="modelValue"
  @input="emit('update:modelValue', $event.target.value)"
></input>
```

_Parent_

```vue
<MyInput v-model="name" />
```

**Multiple `v-model` Bindings**

You may define custom model names.

_Child_:

```vue
<script setup>
defineProps(["title", "content"]);
const emit = defineEmits(["update:title", "update:content"]);
</script>
```

_Parent_:

```vue
<PostEditor v-model:title="postTitle" v-model:content="postContent" />
```

### Form Validation Patterns

- **Basic Reactive Validation**

```js
const email = ref("");
const error = computed(() => {
  return email.value.includes("@") ? "" : "Invalid email";
});
```

- **Touch Validation**

```js
const touched = ref(false);
const validate = computed(() => {
  if (!touched.value) return "";
  return email.value.includes("@") ? "" : "Email required";
});
```

- **Form Submit Guard**

```js
if (!email.value.includes("@")) return;
```

- **Using external libraries**

  - VeeValidate
  - Yup
  - Zod
  - VueUse form patterns

### Common Real‑World Form Implementations

- Login Form

```vue
<input v-model="email">
<input v-model="password" type="password" />
<button @click="login">Login</button>
```

- Search Bar with Debounce

```vue
<input v-model.lazy="query" />
```

Or with watch + debounce.

- Dynamic Field Arrays

```vue
<div v-for="(field, i) in fields" :key="field.id">
  <input v-model="field.value"/>
  <button @click="remove(i)">X</button>
</div>
```

- Contact Form

Fields: **name**, **email**, **phone**, **message**

Includes validation and reset.

### Mini Project — Complete Registration Form

**Features**

- Full two‑way binding with validation
- Multiple field types
- Display submitted result

**Template**

```vue
<form @submit.prevent="submitForm">
  <input v-model.trim="form.name" placeholder="Full Name" />
  <input v-model.trim="form.email" type="email" placeholder="Email" />
  <input v-model.number="form.age" placeholder="Age" />


  <label>
    <input type="checkbox" v-model="form.terms" /> I agree to terms
  </label>


  <select v-model="form.country">
    <option value="bd">Bangladesh</option>
    <option value="us">USA</option>
  </select>


  <button>Submit</button>
</form>

<div v-if="submitted">
  <h3>Submitted Data:</h3>
  <pre>{{ form }}</pre>
</div>
```

Script

```js
import { ref } from "vue";

const form = ref({
  name: "",
  email: "",
  age: null,
  terms: false,
  country: "",
});

const submitted = ref(false);

const submitForm = () => {
  if (!form.value.name || !form.value.email) return;
  submitted.value = true;
};
```
