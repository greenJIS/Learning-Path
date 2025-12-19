# BootstrapVue Documentation (Exhaustive Guide)

> A complete, production-oriented reference for **BootstrapVue v2 (Bootstrap 4)** components, helpers, directives, and real‑world UI patterns.

This documentation is designed for:

- Engineers working on **Vue 2 + BootstrapVue** projects
- Teams maintaining legacy BootstrapVue codebases
- Fast onboarding and consistent UI implementation

---

## 📦 Version Scope

- **BootstrapVue**: v2.x
- **Bootstrap**: v4.x
- **Vue**: Vue 2.x

> ⚠️ BootstrapVue is now in maintenance mode. This guide focuses on **stability, best practices, and real‑world usage**, not new feature development.

---

## 📚 Documentation Structure

```
/bootstrapvue-docs
├── README.md
├── layout.md
├── content.md
├── navigation.md
├── forms.md
├── buttons.md
├── feedback-overlays.md
├── data-display.md
├── media.md
├── utilities-helpers.md
├── patterns-auth.md
├── patterns-dashboard.md
└── patterns-tables.md
```

---

## 🧱 Component Coverage

This guide provides **100% exhaustive coverage**, including:

### Core Components

- Layout system (`b-container`, `b-row`, `b-col`)
- Content (`b-card`, `b-list-group`, `b-media`)
- Navigation (`b-navbar`, `b-nav`, `b-tabs`, `b-breadcrumb`)
- Forms (all form controls and groups)
- Buttons and button groups
- Feedback and overlays
- Data display and tables
- Media and embeds

### Minor Helpers & Internals

- Helper components (`b-link`, `b-img`, `b-icon`)
- Directives (`v-b-modal`, `v-b-tooltip`, `v-b-popover`, `v-b-toggle`)
- Plugins (`Toast`, `Modal`, `Popover`)
- Transition helpers
- Slot-based utilities

---

## 🎯 Real‑World UI Patterns

Dedicated pattern guides are included:

- **Authentication** (`patterns-auth.md`)

  - Login forms
  - Registration
  - Validation & error handling

- **Dashboard Layouts** (`patterns-dashboard.md`)

  - Responsive grids
  - KPI cards
  - Navigation + content regions

- **Data Tables** (`patterns-tables.md`)

  - Sorting & filtering
  - Pagination
  - Action menus

Each pattern focuses on:

- Component composition
- Accessibility
- Maintainability

---

## 🧠 Usage Philosophy

- Prefer **BootstrapVue props** over custom CSS
- Use **utility classes** for spacing and alignment
- Leverage **slots** for flexibility
- Keep markup declarative and readable

---

## 🚀 Getting Started

Install dependencies:

```bash
npm install bootstrap bootstrap-vue
```

Register BootstrapVue:

```js
import Vue from "vue";
import BootstrapVue from "bootstrap-vue";

Vue.use(BootstrapVue);
```

---

## 🔗 References

- Official BootstrapVue Docs
- Bootstrap 4 Utility API

---

**Next** [`layout.md`](./layout.md)
