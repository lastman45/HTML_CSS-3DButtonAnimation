# 3D Button Animation

A pure CSS 3D social media button animation effect featuring Facebook, Instagram, Twitter, and GitHub buttons with hover interactions, depth shadows, and brand color transitions.

---

## Preview

When hovered, each button lifts and translates in 3D space, revealing its brand color across the face, left side, and bottom face of the button — creating a convincing three-dimensional push-up effect.

---

## Project Structure

```
project/
├── 3DButtonAnimation.html   # Markup — button list with Font Awesome icons
└── 3DButtonAnimation.css    # All styles — layout, 3D transforms, hover effects, responsiveness
```

---

## Features

- **3D skew/rotate transform** — buttons are rendered at an angle using `rotate`, `skew`, and `translate` CSS transforms to simulate a 3D isometric perspective
- **Pseudo-element depth faces** — `::before` (left side) and `::after` (bottom face) are crafted with `skewY` and `skewX` to form the visible depth of each button
- **Smooth hover lift** — on hover, buttons translate upward and to the right while the drop shadow deepens, simulating a physical press-lift
- **Per-button brand colors** — each button transitions to its platform's official color on hover (face + both depth faces simultaneously)
- **Responsive layout** — stacks vertically on mobile with adjusted dimensions

---

## Tech Stack

| Technology | Usage |
|---|---|
| HTML5 | Semantic list structure for buttons |
| CSS3 | 3D transforms, pseudo-elements, transitions |
| Font Awesome 7 | Social media icons (`fab` icon set) |
| Google Fonts | Roboto Condensed typeface |

---

## How It Works

### 3D Illusion

The 3D effect is achieved entirely through CSS transforms — no JavaScript, no 3D libraries.

```css
/* Base state: rotated and skewed to appear isometric */
ul li a {
  transform: rotate(-30deg) skew(25deg) translate(0, 0);
  box-shadow: -20px 20px 10px rgba(0, 0, 0, 0.5);
}

/* Hover state: lifts the button up and to the right */
ul li a:hover {
  transform: rotate(-30deg) skew(25deg) translate(20px, -15px);
  box-shadow: -50px 50px 50px rgba(0, 0, 0, 0.5);
}
```

### Depth Faces (Pseudo-elements)

The left wall and bottom floor of each button are built using `::before` and `::after`:

```css
/* Left face */
ul li a:before {
  top: 10px;
  left: -20px;
  width: 20px;
  height: 100%;
  background: #b1b1b1;
  transform: skewY(-45deg);
}

/* Bottom face */
ul li a:after {
  bottom: -20px;
  left: -10px;
  width: 100%;
  height: 20px;
  background: #b1b1b1;
  transform: skewX(-45deg);
}
```

### Brand Color Mapping

| Button | Brand Color |
|---|---|
| Facebook | `#4267b2` |
| Instagram | `#C13584` |
| Twitter | `#000000` |
| GitHub | `#333333` |

On hover, the brand color is applied to the anchor element and both `::before` / `::after` pseudo-elements simultaneously, so all three visible faces change color together.

---

## Getting Started

### Prerequisites

An internet connection is required to load the external dependencies (Font Awesome and Google Fonts). No build tools or package managers are needed.

### Running Locally

1. Clone or download the project files
2. Keep both files (`3DButtonAnimation.html` and `3DButtonAnimation.css`) in the same directory
3. Open `3DButtonAnimation.html` in any modern browser

```bash
# Example using a simple local server (optional)
npx serve .
# or
python -m http.server 8000
```

### Linking Your Social Profiles

Replace the `#` placeholder in each anchor's `href` attribute with the target URL:

```html
<a href="https://facebook.com/yourprofile">
```

---

## Customization

### Adding a New Button

1. Add a new `<li>` in `3DButtonAnimation.html`:

```html
<li>
  <a href="#">
    <i class="fab fa-linkedin-in"></i>
    <span>LinkedIn</span>
  </a>
</li>
```

2. Add the corresponding hover color rules in `3DButtonAnimation.css` (using the correct `nth-child` index):

```css
ul li:hover:nth-child(5) a         { background: #0077b5; }
ul li:hover:nth-child(5) a::before { background: #0077b5; }
ul li:hover:nth-child(5) a::after  { background: #0077b5; }
```

### Changing Button Size

Adjust `width` and `height` on `ul li a`, and `font-size` / `line-height` on `.fa`:

```css
ul li a {
  width: 240px;   /* wider button */
  height: 90px;   /* taller button */
}
ul li a .fa {
  font-size: 48px;
  line-height: 90px;
}
```

### Changing the Background

```css
body {
  background: #1a1a2e;  /* dark background example */
}
```

---

## Responsive Behavior

| Breakpoint | Behavior |
|---|---|
| > 768px | Buttons displayed horizontally in a row |
| ≤ 768px | Buttons stack vertically; width 90%, height 60px, icon 30px |
| ≤ 480px | Height reduced to 50px, icon reduced to 24px |

---

## Browser Support

Works in all modern browsers that support CSS3 transforms and transitions:

- Chrome 36+
- Firefox 16+
- Safari 9+
- Edge 12+

> Internet Explorer is not supported due to its limited CSS transform support.

---

## Dependencies

| Dependency | Version | CDN |
|---|---|---|
| Font Awesome | 7.0.0 | `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/7.0.0/css/all.min.css` |
| Roboto Condensed | (Google Fonts) | Loaded via CSS `font-family` declaration |

---

## License

This project is provided as-is for educational and personal use. Social media brand colors and logos belong to their respective companies.
