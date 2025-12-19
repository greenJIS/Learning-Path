# Form Components

> This section covers all **BootstrapVue form components**, including input controls, validation states, and groupings for building real-world forms.

---

## 1. `<b-form>`

**Purpose:** Wrapper for form elements.

```vue
<b-form @submit.prevent="onSubmit">
  <b-form-input v-model="name" required placeholder="Enter name" />
  <b-button type="submit" variant="primary">Submit</b-button>
</b-form>
```

**Notes:**

- Handles submit events
- Integrates with validation

---

## 2. `<b-form-input>`

**Purpose:** Standard text input.

```vue
<b-form-input v-model="email" type="email" placeholder="Email" />
```

**Key Props:**

- `type`, `value`, `placeholder`, `required`, `disabled`
- `state` for validation (true/false/null)

---

## 3. `<b-form-textarea>`

**Purpose:** Multi-line input.

```vue
<b-form-textarea v-model="message" rows="3" />
```

**Notes:**

- `rows` and `max-rows` props control height
- Supports validation states

---

## 4. `<b-form-select>`

**Purpose:** Dropdown select input.

```vue
<b-form-select v-model="selected" :options="['Option 1', 'Option 2']" />
```

**Notes:**

- Options can be array or object
- Supports multiple selection

---

## 5. `<b-form-checkbox>` / `<b-form-checkbox-group>`

```vue
<b-form-checkbox v-model="agree">Accept Terms</b-form-checkbox>

<b-form-checkbox-group v-model="selectedOptions" :options="['A', 'B', 'C']" />
```

**Notes:**

- Group binds to an array
- Supports `name` and `switch` style

---

## 6. `<b-form-radio>` / `<b-form-radio-group>`

```vue
<b-form-radio-group v-model="choice" :options="['Yes', 'No']" />
```

**Notes:**

- Supports inline layout
- Can be disabled or required

---

## 7. `<b-form-file>`

**Purpose:** File input.

```vue
<b-form-file v-model="file" placeholder="Choose a file" />
```

**Notes:**

- Shows filename by default
- Can accept multiple files

---

## 8. `<b-form-rating>` (Optional plugin)

**Purpose:** Star rating input.

```vue
<b-form-rating v-model="rating" variant="warning" />
```

**Notes:**

- Supports hover, read-only
- Optional, requires `BootstrapVueIcons`

---

## 9. Input Groups

```vue
<b-input-group prepend="@">
  <b-form-input v-model="username" placeholder="Username" />
</b-input-group>
```

**Notes:**

- Supports prepend, append, buttons, dropdowns
- Used for login forms and search bars

---

## 10. Validation States

```vue
<b-form-input v-model="email" type="email" :state="emailState" />
<b-form-invalid-feedback>Email is invalid</b-form-invalid-feedback>
```

**Notes:**

- `state` prop: true = valid, false = invalid, null = neutral
- Combine with `b-form-feedback`

---

## 11. Real-World Pattern: Login Form

```vue
<b-form @submit.prevent="login">
  <b-form-group label="Email">
    <b-form-input v-model="email" type="email" required />
  </b-form-group>
  <b-form-group label="Password">
    <b-form-input v-model="password" type="password" required />
  </b-form-group>
  <b-button type="submit" variant="primary">Login</b-button>
</b-form>
```

**Notes:**

- Uses `b-form-group` for labeling
- Validation ready

---

## 12. Real-World Pattern: Registration Form

```vue
<b-form @submit.prevent="register">
  <b-row>
    <b-col md="6">
      <b-form-group label="First Name">
        <b-form-input v-model="firstName" required />
      </b-form-group>
    </b-col>
    <b-col md="6">
      <b-form-group label="Last Name">
        <b-form-input v-model="lastName" required />
      </b-form-group>
    </b-col>
  </b-row>
  <b-form-group label="Email">
    <b-form-input v-model="email" type="email" required />
  </b-form-group>
  <b-form-checkbox v-model="agree">I agree to terms</b-form-checkbox>
  <b-button type="submit" variant="success">Register</b-button>
</b-form>
```

**Notes:**

- Uses grid for layout
- Includes checkbox for agreement
- Multi-input form with validation

---

## Summary

- Covers **all input types, groups, validation**
- Designed for **real-world authentication and registration forms**
- Works seamlessly with **Bootstrap utilities and layout components**

---

**Next:** [`button.md`](./buttons.md)
