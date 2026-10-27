# ShopEase — Modern E-Commerce Web Application

**ShopEase** is a college-level software engineering and quality assurance portfolio project. Built with React 19, Vite, and modern CSS3, it offers an intuitive, accessible online shopping experience featuring dynamic catalog filtering, quantity steppers, discount promo codes, cart persistence via LocalStorage, form validation, and demo order generation.

---

## 🛍️ Live Features & Pages

### 1. Home Page (`/`)
- **Navigation Bar**: ShopEase logo, search input (routes to `/shop?search=...`), links to Home, Shop, Categories dropdown, Contact, and a dynamic shopping cart badge.
- **Hero Banner**: Compelling headline, call-to-actions ("Explore Shop", "Browse Categories"), trust stats, and an interactive Deal of the Day card.
- **Category Grid**: 4 curated categories (Electronics, Fashion, Accessories, Home & Living) with icons, counts, and direct links to filtered catalog views.
- **Featured Highlights & Best Sellers**: Handpicked product showcases with star ratings, INR (₹) prices, and quick Add to Cart buttons.
- **Promotional Banner**: Highlighting discount promo codes (`SHOPEASE10` for 10% off and `SAVE20` for 20% off).
- **Newsletter Section**: Subscriptions input with email regex validation and instant feedback.
- **Footer**: Trust badges (Free delivery, genuine products, 7-day returns, 24/7 support), category links, sample customer care details, and demo disclaimers.

### 2. Shop / Products Catalog (`/shop`)
- **Real-Time Search**: Instant filtering by product title, category, or description keywords.
- **Category Filter Pills**: Interactive buttons displaying dynamic item counts per category.
- **Sort Options**: Price (Low to High), Price (High to Low), Top Rated, Name (A to Z), and Featured.
- **Filter Reset**: Quick "Reset" button when filters are active.
- **Empty State**: Friendly illustration and "Clear All Filters" button when no products match.

### 3. Product Details Page (`/product/:id`)
- **Breadcrumbs**: Hierarchical navigation (`Home / Shop / Category / Product Name`).
- **High-Resolution Imagery**: Aspect-ratio constrained gallery with fallback image handling on load errors.
- **Specs & Highlights**: Key product bullet points, category pill, star ratings, and review counts.
- **Quantity Selector**: Stepper controls enforcing minimum bounds ($\ge 1$).
- **Actions**: "Add to Cart" with toast notification and "Buy Now" (direct to checkout).
- **Related Recommendations**: Dynamic recommendations of similar items in the same category.

### 4. Shopping Cart (`/cart`)
- **Itemized Table**: Product thumbnail, name, unit price, quantity stepper, line total, and delete button.
- **Free Delivery Progress Meter**: Visual progress bar indicating how much more is needed to reach the ₹999 free delivery threshold.
- **Promo Code Engine**: Test codes `SHOPEASE10` (10% discount) and `SAVE20` (20% discount).
- **Real-Time Totals**: Immediate recalculation of Subtotal, Delivery Fee, Discount, and Final Amount.
- **Empty Cart View**: Helpful message and CTA to return to the catalog.

### 5. Checkout Page (`/checkout`)
- **Empty Cart Guard**: Restricts checkout if no items are in the cart.
- **Customer Information**: Full Name, Email, 10-Digit Mobile Number, Delivery Address, City, State, and 6-Digit PIN Code.
- **Real-Time Validation**: Field validation on blur and submit with descriptive inline error messages.
- **Demo Payment Methods**: Choice between Cash on Delivery (Demo), Demo UPI / QR, and Demo Net Banking.
- **Order Review**: Itemized sidebar summary before final placement.

### 6. Order Success Page (`/order-success/:orderId`)
- **Unique Demo Order ID**: Generated in the format `SE-2026-XXXXXX`.
- **Confirmation Badge**: Animated success checkmark.
- **Order Breakdown**: Line items, quantities, subtotal, discount, delivery fee, and total.
- **Customer Summary**: Shipping address and estimated delivery date.
- **Post-Order Cart Clearing**: Clears the cart from LocalStorage only after the order is confirmed.
- **Print Receipt**: Uses browser print engine (`window.print()`) formatted cleanly for printing.

### 7. Contact Page (`/contact`)
- **Contact Details**: Support email, toll-free helpline, headquarters address, and sandbox hours.
- **Validated Contact Form**: Name, Email, Subject, and Message with error handling and success state.

### 8. User Authentication (`/login`)
- **Sign In & Registration**: Dual tab modes for existing user login and new member signup.
- **⚡ One-Click Demo Login**: Fast-track button to log in instantly as `Priyanshu Sharma` without manual typing.
- **Form Validation**: Real-time email validation and 6+ character password checks.
- **Navbar Profile Dropdown**: Displays user avatar badge, user full name, email, quick cart access, and single-click **Logout** button.
- **Session Persistence**: Persists user session in `localStorage` across page reloads.
- **Checkout Auto-Fill**: Automatically pre-populates name, email, phone, and delivery address on the Checkout page for logged-in users.

### 9. Not Found 404 (`*`)
- Custom 404 page with buttons to return home or browse the product catalog.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **React 19** | Component-driven UI architecture |
| **Vite 8** | High-performance build tool and dev server |
| **React Router 7** | Client-side routing and deep linking |
| **Context API** | Global cart state management and toast alerts |
| **LocalStorage** | Persistence of shopping cart and demo orders |
| **Lucide React** | Modern, lightweight UI icons |
| **Vanilla CSS3** | Custom design system with CSS custom properties and responsive grids |

---

## 📁 Project Structure

```
task 1/
├── index.html                   # HTML entry point with Google Fonts & favicon
├── package.json                 # Project dependencies & scripts
├── vite.config.js               # Vite configuration
├── README.md                    # Project documentation
├── TESTING.md                   # 15+ comprehensive manual test cases
├── BUG_REPORT.md                # Standardized bug reporting template
├── scripts/
│   └── verify-logic.js          # Automated business logic verification suite
└── src/
    ├── main.jsx                 # React root mount
    ├── App.jsx                  # Main application routing & layout
    ├── index.css                # Design system styling & responsive rules
    ├── components/
    │   ├── Navbar.jsx           # Responsive header, search & mobile drawer
    │   ├── Footer.jsx           # Trust badges, links, and customer care
    │   ├── ProductCard.jsx      # Reusable card with rating & add-to-cart
    │   ├── ProductGrid.jsx      # Responsive grid with empty state
    │   ├── SearchBar.jsx        # Search component with clear button
    │   ├── CategoryFilter.jsx   # Filter pills with count badges
    │   ├── CartItem.jsx         # Cart row with quantity stepper
    │   └── Toast.jsx            # Dynamic notification alerts
    ├── context/
    │   └── CartContext.jsx      # Global cart state, coupons & order engine
    ├── data/
    │   └── products.js          # 16 sample products in 4 categories
    ├── pages/
    │   ├── Home.jsx             # Hero, categories, featured, promo & newsletter
    │   ├── Shop.jsx             # Product catalog with search, filter & sort
    │   ├── ProductDetails.jsx   # Details, specs, quantity & related items
    │   ├── Cart.jsx             # Cart management, totals & coupons
    │   ├── Checkout.jsx         # Customer address form & validation
    │   ├── OrderSuccess.jsx     # Order confirmation & receipt printing
    │   ├── Contact.jsx          # Contact info & validated inquiry form
    │   └── NotFound.jsx         # 404 Not Found page
    └── utils/
        ├── storage.js           # LocalStorage helpers for cart and orders
        └── validation.js        # Form validation utilities
```

---

## 🚀 Installation & Running Instructions

### Prerequisites
- Node.js (v18.0.0 or higher recommended)
- npm (v9.0.0 or higher)

### Steps to Run

1. **Install dependencies for Frontend & Backend:**
   ```bash
   npm install
   cd server && npm install && cd ..
   ```

2. **Start the Frontend development server:**
   ```bash
   npm run dev
   ```
   Open `http://localhost:5173/` in your browser.

3. **Start the MongoDB Backend API server (Port 5000):**
   ```bash
   npm run server
   ```
   *Health check:* `http://localhost:5000/api/health`

4. **Seed Sample Products into MongoDB (Optional):**
   ```bash
   cd server && npm run seed
   ```

5. **Run automated logic verification suite:**
   ```bash
   node scripts/verify-logic.js
   ```

6. **Build for production:**
   ```bash
   npm run build
   ```

---

## 🧪 Testing & Verification Summary

The project includes an extensive test plan documented in `TESTING.md`. All 15 required core scenarios were executed and verified:

1. **Home Page Loading** (Logo, hero, categories, featured, promo banner, cart badge)
2. **Navigation Links** (Seamless client-side transitions via React Router)
3. **Product Search** (Real-time keyword matching and empty-state handling)
4. **Category Filters** (Electronics, Fashion, Accessories, Home & Living)
5. **Price Sorting** (Low to High, High to Low, Top Rated, Name)
6. **Product Details** (Breadcrumbs, specs, imagery, in-stock indicators)
7. **Adding Items to Cart** (Toast feedback, instantaneous navbar badge counter update)
8. **Cart Quantity Increase** (Immediate line total and subtotal adjustment)
9. **Cart Quantity Decrease** (Strict boundary enforcement: values cannot drop below 1)
10. **Removing Item from Cart** (Immediate removal, badge update, subtotal adjustment)
11. **Cart Persistence** (Items and quantities preserved across page reloads via LocalStorage)
12. **Empty-Cart Checkout Prevention** (Guard screen blocks checkout when cart is empty)
13. **Checkout Validation** (Input checks for name, email, 10-digit phone, address, and 6-digit PIN)
14. **Valid Demo Order Placement** (Order compilation with simulated payment options)
15. **Order Confirmation** (Unique ID `SE-2026-XXXXXX`, item summary, cart cleared only upon order creation)

---

## ⚠️ Known Limitations & Demo Scope

- **Frontend-Only Scope**: In adherence to the requirements, there is no real backend server, database, or payment gateway. All data is persisted in browser `localStorage`.
- **Demo Transactions**: Checkout and payment options (COD, UPI, Net Banking) are simulated demo processes. No financial data is collected or charged.
- **Mock Contact Form**: Inquiries submitted through the Contact page and Newsletter are validated in the frontend and displayed in state; no live email server is connected.
