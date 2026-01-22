# CORELLE - Premium Beauty E-Commerce

Welcome to the **CORELLE** repository. This isn't just a static landing page; it's a fully functional e-commerce interface built primarily with **Vanilla JavaScript** and **CSS3**.

My goal with this project was to step away from heavy frontend frameworks (like React or Vue) to see how far I could push native web technologies. The result is a highly animated, responsive, and logic-driven application that handles everything from shopping cart calculations to complex scroll animations.

---

## 🛠 The Tech Stack

I kept the dependencies minimal to focus on performance and raw coding skills:

* **Frontend:** HTML5, CSS3 (Variables, Flexbox, Grid, Advanced Keyframes), Vanilla JavaScript (ES6+).
* **Backend / Auth:** Firebase (Authentication & Firestore).
* **Icons:** Ionicons.
* **Assets:** Google Fonts (Playfair Display & Great Vibes).

---

## ⚡ Key Systems & Features

Here is a breakdown of what’s happening under the hood:

### 1. 🛍️ Custom Shopping Logic (`shop.js`)

I didn't use a library for the cart; I wrote the logic from scratch.

* **Dynamic Cart Sidebar:** Slides in from the right without refreshing the page.
* **Gamified Free Shipping:** There's a dynamic progress bar in the cart that calculates how much more the user needs to spend to unlock free shipping (e.g., "Add 300 RON for free shipping").
* **Smart Notifications:** Instead of ugly browser alerts, I built a custom notification system (`toast` style) that slides in to confirm actions like "Item added" or "Cart cleared".
* **Product Modal:** A quick-view overlay that includes image zooming, quantity selection, and a "Similar Products" section.

### 2. 🔐 Authentication & Security (`login.js`)

The login isn't just a form; it's an experience.

* **Firebase Integration:** Handles real user creation and login sessions.
* **"Wave" Input Animation:** When you click a field, the label letters animate up in a wave pattern using CSS delays (`transition-delay: calc(var(--index) * .05s)`).
* **Real-time Password Strength:** As the user types, a checklist dynamically updates to verify requirements (uppercase, numbers, special characters) using Regex.

### 3. 🎨 Advanced UI/UX & Animations

This is where I spent the most time polishing the feel of the site.

* **Infinite Scrollers (The "About" Page):**
* *Vertical:* The certifications section scrolls endlessly.
* *Horizontal:* The "Values" section loops horizontally.
* *The Logic:* I used JS to clone the DOM elements on load (`initCertificationsSlider`) to create a seamless loop without that "jump" you usually get with CSS-only sliders.


* **Parallax & Observers:** Elements fade in and slide up as you scroll using the `IntersectionObserver` API, and images have a subtle parallax effect based on scroll position.
* **User Panels:** Settings, Favorites, and Account details live in side panels that overlay the content, keeping the user immersed.

### 4. 🔎 Search & Filtering

* **Advanced Filtering:** The products page (`shop.css`) features a sidebar with category filters and price sorting.
* **Layout Toggle:** Users can switch between a 2-column or 3-column grid view for the products.

---

## 📂 Project Structure

```bash
/
├── index.html          # Main entry (Home, Panels, Shop Modal)
├── about.html          # Story page (Infinite sliders, Parallax)
├── css/
│   ├── style.css       # Global vars & typography
│   ├── home.css        # Hero video & Navbar logic
│   ├── shop.css        # Cart logic, Filters, Modals
│   ├── login.css       # Auth forms & Wave animations
│   └── about.css       # Keyframes for timelines/sliders
└── js/
    ├── main.js         # Firebase Config
    ├── shop.js         # Cart calculations & DOM manipulation
    ├── login.js        # Auth logic & Form validation
    └── about.js        # Intersection Observers & Slider logic

```

---

## 💡 Cool Implementation Details

**The "Free Shipping" Bar:**
I wanted to encourage users to buy more, so the cart automatically calculates `(Threshold - CurrentTotal)`. If the result is positive, it updates the progress bar width via CSS `width: %`; if negative, it turns green and says "Free Shipping Unlocked."

**The Infinite Loop Hack:**
In `about.js`, simply animating CSS wasn't enough for a seamless loop. I wrote a function that takes the list of items, clones them, and appends them to the container. This way, when the animation resets to `0%`, the user can't tell because the cloned items look exactly like the start of the original list.

---

## 🚀 How to Run

Since this is a static site structure, it's easy to get running:

1. Clone the repo.
2. Open `index.html` in your browser (or use **Live Server** in VS Code for the best experience).
*Note:* The Authentication features require a valid Firebase configuration. You may need to create your own Firebase project and replace the keys in `js/main.js`.
