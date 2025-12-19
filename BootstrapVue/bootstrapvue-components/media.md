# Media Components

> This section covers **BootstrapVue media-related components**, used for images, icons, embeds, carousels, and user avatars.

---

## 1. `<b-carousel>`

**Purpose:** Image/content slider.

```vue
<b-carousel id="carousel-1" controls indicators>
  <b-carousel-slide img-src="slide1.jpg" caption="First Slide" />
  <b-carousel-slide img-src="slide2.jpg" caption="Second Slide" />
</b-carousel>
```

**Props:**

- `controls`, `indicators` – show arrows and dots
- `interval` – autoplay interval in ms
- `background` – overlay color

**Notes:**

- Supports content slides with HTML via default slot
- Works with text, buttons, and media

---

## 2. `<b-embed>`

**Purpose:** Responsive embeds for videos, maps, and iframes.

```vue
<b-embed
  type="iframe"
  aspect="16by9"
  src="https://www.youtube.com/embed/video-id"
/>
```

**Props:**

- `type` – `iframe`, `video`, `embed`
- `aspect` – `21by9`, `16by9`, `4by3`, `1by1`
- `allowfullscreen` – boolean

**Notes:**

- Maintains responsive aspect ratio
- Useful for video tutorials or maps

---

## 3. `<b-img>` Advanced Usage

```vue
<b-img src="logo.png" fluid rounded alt="Logo" lazy />
```

**Props:**

- `fluid` / `fluid-grow` – responsive resizing
- `rounded` / `rounded-circle` – shape
- `thumbnail` – small bordered variant
- `lazy` – defer loading

**Notes:**

- Can be used in carousels, cards, avatars

---

## 4. `<b-avatar>`

**Purpose:** User or icon avatars.

```vue
<b-avatar src="user.jpg" size="3rem" variant="primary" />
<b-avatar text="AB" variant="success" />
```

**Props:**

- `src`, `text`, `icon`
- `size` – px/rem
- `variant` – background color
- `rounded` – circle / pill

**Notes:**

- Often used in lists, media components, and comments

---

## 5. Real-World Pattern: Media Gallery

```vue
<b-row>
  <b-col md="4" v-for="image in images" :key="image.id">
    <b-card>
      <b-img :src="image.src" fluid alt="Gallery Image" />
      <b-card-body>{{ image.caption }}</b-card-body>
    </b-card>
  </b-col>
</b-row>
```

**Notes:**

- Responsive 3-column grid gallery
- Cards combine image and text content

---

## 6. Real-World Pattern: Carousel with Content

```vue
<b-carousel controls indicators>
  <b-carousel-slide>
    <h3>Slide 1</h3>
    <p>Text and buttons can go here</p>
  </b-carousel-slide>
  <b-carousel-slide img-src="slide2.jpg">
    <h3>Slide 2</h3>
  </b-carousel-slide>
</b-carousel>
```

**Notes:**

- Mix of images and custom HTML
- Useful for landing pages or product showcases

---

## Summary

- Media components focus on **responsive, visually rich content**
- Carousels, embeds, and avatars can be combined with cards and grids
- `b-img` and `b-avatar` are foundational for user-centric layouts

---

**Next:** [`utilities-helpers.md`](./utilities-helpers.md)
