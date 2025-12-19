# Authentication UI Patterns

> This section provides **real-world examples of authentication forms** using BootstrapVue components, combining layout, forms, and utilities.

---

## 1. Login Form

```vue
<b-container class="vh-100 d-flex align-items-center justify-content-center">
  <b-card class="w-50 p-4" title="Login">
    <b-form @submit.prevent="login">
      <b-form-group label="Email">
        <b-form-input v-model="email" type="email" required />
      </b-form-group>
      <b-form-group label="Password">
        <b-form-input v-model="password" type="password" required />
      </b-form-group>
      <b-button type="submit" variant="primary" class="w-100">Login</b-button>
    </b-form>
  </b-card>
</b-container>
```

**Explanation:**

- Centered card using Flex utilities
- Simple form with validation-ready inputs
- Full-width button for better UX

---

## 2. Registration Form

```vue
<b-container class="my-5">
  <b-card title="Register" class="p-4">
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
      <b-form-group label="Password">
        <b-form-input v-model="password" type="password" required />
      </b-form-group>
      <b-form-checkbox v-model="agree">I agree to terms and conditions</b-form-checkbox>
      <b-button type="submit" variant="success" class="mt-3 w-100">Register</b-button>
    </b-form>
  </b-card>
</b-container>
```

**Explanation:**

- Uses `b-row` + `b-col` for multi-column inputs
- Checkbox for terms
- Responsive and accessible layout

---

## 3. Password Reset Form

```vue
<b-container class="vh-100 d-flex align-items-center justify-content-center">
  <b-card title="Reset Password" class="p-4 w-50">
    <b-form @submit.prevent="resetPassword">
      <b-form-group label="Email">
        <b-form-input v-model="email" type="email" required />
      </b-form-group>
      <b-button type="submit" variant="warning" class="w-100">Send Reset Link</b-button>
    </b-form>
  </b-card>
</b-container>
```

**Explanation:**

- Centered card layout
- Minimal fields for quick password recovery
- Uses utility classes for spacing and alignment

---

## Summary

- Combines layout, form components, and utilities for **real-world auth UIs**
- Mobile-first and responsive
- Ready for integration with backend authentication logic

---

**Next:** [`patterns-dashboard.md`](./patterns-dashboard.md)
