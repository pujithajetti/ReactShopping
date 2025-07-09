# 🛒 React Shopping Cart

A modern e-commerce frontend built with **React**, **Firebase**, **Vite**, and **SCSS**—complete with authentication, product variants, cart & checkout simulation.

---

## 🚀 Features

- **Product Browsing**
  - Infinite scroll on product listings
  - Filter by categories or attributes
- **Variants & Inventory**
  - Multiple variants (e.g., color, size) per product
  - Per-SKU stock tracking and “on sale” pricing logic
- **Cart Functionality**
  - Add/remove/update quantities in the cart
  - Persist cart per user with Firestore
- **User Authentication**
  - Email/password login + anonymous browsing
- **Mock Checkout Flow**
  - Temporary checkout page and order history
- **Admin Interface**
  - Inventory and orders (for admin users)

---

## 🔧 Tech Stack

| Layer              | Tech             |
|-------------------|------------------|
| Frontend          | React, Vite, SCSS |
| Data & Auth       | Firebase Firestore & Auth |
| Storage           | Firebase Cloud Storage |
| Routing & State   | React Router, Context API, Hooks |

---

## 🛠️ Setup & Installation

1. **Clone the repo**  
   ```bash
   git clone https://github.com/pujithajetti/ReactShopping.git
   cd ReactShopping
   ```

2. **Install dependencies**  
   ```bash
   npm install
   ```

3. **Configure Firebase**  
   Create `src/firebase/firebase-config.js`:
   ```js
   export const firebaseConfig = {
     apiKey: "...",
     authDomain: "...",
     projectId: "...",
     storageBucket: "...",
     messagingSenderId: "...",
     appId: "..."
   };
   ```

4. **Initialize Firestore data**  
   - Create collections: `products`, `users`, `carts`, `orders`, `checkoutSessions`
   - Each `product` doc includes:
     - `price`, sub-collections `variants` & `skus`
   - Upload images in Cloud Storage under `product-images/<variantId>/…`
   - Seed data manually or via a script (see `dummy-products.json`)

5. **Run the app**  
   ```bash
   npm run dev
   ```

---

## 📦 Firestore Data Structure

- **products** → (product document)
  - Fields: `price`, `name`, `description`
  - **variants** subcollection
    - Fields: `images` (array of cloud storage paths), `variantPrice`
  - **skus** subcollection
    - Fields: `variantId`, `value`, `stock`, etc.
- **users**, **carts**, **orders**, **checkoutSessions** as separate collections

---

## 🎮 Admin Mode

- To enable admin features:
  1. Create or select a Firestore user.
  2. Add field `"isAdmin": true` to their user document.
  3. Comment/uncomment admin routes in `src/App.jsx` as needed.

---

## 🧩 Project Structure

```
ReactShopping/
├── public/
├── src/
│   ├── components/
│   ├── firebase/
│       └── firebase-config.js
│   ├── App.jsx
│   └── index.jsx
├── data/
│   └── dummy-products.json
├── firebase.json
├── firestore.rules
└── vite.config.js
```

---

## ✅ Roadmap & Future Plans

- Secure Firestore rules for users, carts & orders
- Optimize performance (caching, lazy-loading)
- Enhance admin dashboard (bulk uploads, stats)
- Integrate real payment gateway (Stripe, Razorpay)
- Add unit/integration tests and CI/CD pipeline

---

## 👐 Contributing

Contributions welcome! Feel free to:

- Open issues / feature requests
- Submit PRs for bug fixes or enhancements
- Suggest improvements to structure or architecture

---

## 💡 License

*(Add your preferred license here, e.g. MIT)*

---

## ❤️ Credits

Inspired by [jp‑quintana/react‑shopping‑cart](https://github.com/jp-quintana/react-shopping-cart)

---

## 📞 Contact

Let me know if you'd like help with:

- Deploying it (Netlify, Vercel, Firebase Hosting)
- Writing sample data migration scripts
- Adding user analytics or A/B testing
- Dockerizing or setting up CI/CD

Happy coding! 😊