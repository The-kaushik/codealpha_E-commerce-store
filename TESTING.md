# ShopEase — Software Testing & Quality Assurance Manual Test Plan

This document contains the comprehensive manual test suite for the **ShopEase** e-commerce application. It is structured for academic demonstration, software verification, and bug detection.

---

## System Under Test (SUT) Details
- **Application Name**: ShopEase E-Commerce Web Application
- **Platform**: Web (Desktop, Tablet, Mobile)
- **Frontend Stack**: React 19, Vite, React Router 7, Context API, LocalStorage, Lucide React, Vanilla CSS3
- **Test Execution Environment**: Local Development Server (`http://localhost:5173`)
- **Node Version**: v24.20.0
- **Currency Format**: Indian Rupee (₹, `en-IN`)

---

## Summary of Test Results

| Total Test Cases | Passed | Failed | Blocked | Pass Rate |
|:----------------:|:------:|:------:|:-------:|:---------:|
| 18               | 18     | 0      | 0       | 100%      |

---

## Detailed Test Cases

### TC-01: Home Page Loading & Initial State
- **Test Case ID**: `TC-01`
- **Test Scenario**: Verify the Home Page loads successfully with all major sections and initial cart count.
- **Preconditions**: Development server running at `http://localhost:5173/`. Browser cache and localStorage cleared.
- **Test Steps**:
  1. Open browser and navigate to `http://localhost:5173/`.
  2. Observe the page header, hero banner, category cards, featured products, promotional banner, newsletter section, and footer.
  3. Inspect the cart icon in the navigation bar.
- **Expected Result**:
  - The page loads without compilation or console errors.
  - ShopEase logo, navigation links (Home, Shop, Categories, Contact), and search bar are visible.
  - Hero banner with headline "Effortless Shopping, Exceptional Quality" and CTA buttons render properly.
  - Cart item badge is not shown or indicates 0 items when cart is empty.
- **Actual Result**: Home page rendered cleanly with all sections, hero visuals, and footer trust badges. Cart badge is empty.
- **Status**: **PASS**

---

### TC-02: Navigation Bar & Routing
- **Test Case ID**: `TC-02`
- **Test Scenario**: Verify client-side navigation links route to their respective destinations.
- **Preconditions**: User is on the Home page (`/`).
- **Test Steps**:
  1. Click "Shop" in the navigation bar.
  2. Verify URL updates to `/shop`.
  3. Click "Categories" dropdown and select "Fashion".
  4. Verify URL updates to `/shop?category=Fashion`.
  5. Click "Contact" in the navigation bar.
  6. Verify URL updates to `/contact`.
  7. Click the ShopEase logo to return home (`/`).
- **Expected Result**: All routes transition smoothly without full browser reloads; active navigation styling is highlighted.
- **Actual Result**: React Router navigates seamlessly between all routes (`/`, `/shop`, `/contact`, `/cart`). Active link classes applied.
- **Status**: **PASS**

---

### TC-03: Product Search Functionality
- **Test Case ID**: `TC-03`
- **Test Scenario**: Search for products by name and keyword on the Shop page.
- **Preconditions**: User is on the Shop page (`/shop`).
- **Test Steps**:
  1. Click on the search input on `/shop`.
  2. Enter keyword `"Watch"`.
  3. Verify the product grid updates to show only matching watch products.
  4. Enter an invalid keyword e.g. `"xyznonexistent"`.
  5. Verify the empty state message is shown.
  6. Click "Clear All Filters" or the search clear button.
- **Expected Result**:
  - Searching for `"Watch"` displays matching items (e.g. *Chronograph Classic Heritage Leather Watch* and *PulseFlow Smart Fitness Watch*).
  - Searching for invalid terms displays "No matching products found" empty state.
  - Clearing resets the grid to show all products.
- **Actual Result**: Real-time filtering responds immediately to queries; empty state with reset button displays correctly when no match exists.
- **Status**: **PASS**

---

### TC-04: Category Filtering
- **Test Case ID**: `TC-04`
- **Test Scenario**: Filter products using category buttons.
- **Preconditions**: User is on `/shop`.
- **Test Steps**:
  1. Click the "Electronics" category pill.
  2. Count displayed items and verify category names.
  3. Click "Fashion" category pill.
  4. Click "All Products" pill.
- **Expected Result**:
  - Selecting "Electronics" shows only 4 electronics products; product counter reads "Showing 4 of 16 products".
  - Selecting "Fashion" shows only 4 apparel products.
  - "All Products" restores the full 16-item catalog.
- **Actual Result**: Category selection immediately filters the list and updates the category count badges and active pill styles.
- **Status**: **PASS**

---

### TC-05: Price and Attribute Sorting
- **Test Case ID**: `TC-05`
- **Test Scenario**: Sort product catalog by price and customer ratings.
- **Preconditions**: User is on `/shop`.
- **Test Steps**:
  1. Click the "Sort by" dropdown.
  2. Select "Price: Low to High".
  3. Check the price of the first and last products.
  4. Select "Price: High to Low".
  5. Check the price of the first and last products.
  6. Select "Top Rated".
- **Expected Result**:
  - Low to High orders products starting from ₹799 (Scented Candle) upwards.
  - High to Low orders products starting from ₹4,999 (AcousticPro Headphones) downwards.
  - Top Rated sorts highest rating (4.9★) at the top.
- **Actual Result**: Sorting order is verified accurately according to numerical price and rating values.
- **Status**: **PASS**

---

### TC-06: Product Details Page & Information Accuracy
- **Test Case ID**: `TC-06`
- **Test Scenario**: View individual product details page and verify information integrity.
- **Preconditions**: User is on the Shop page (`/shop`).
- **Test Steps**:
  1. Click on the product card for "AcousticPro Wireless Noise-Cancelling Headphones".
  2. Verify route changes to `/product/prod-elec-1`.
  3. Check presence of large image, title, category pill, rating, price (₹4,999), original price (₹7,999), discount badge (38% OFF), description, feature highlights, and related products.
  4. Click "Back to Catalog".
- **Expected Result**:
  - Breadcrumbs display `Home / Shop / Electronics / AcousticPro Wireless Noise-Cancelling Headphones`.
  - All specifications and in-stock badges are displayed.
  - "Related In Electronics" section recommends other audio/gadget products.
  - "Back to Catalog" navigates back to `/shop`.
- **Actual Result**: Product details page loads all properties accurately with breadcrumb trail and related recommendations.
- **Status**: **PASS**

---

### TC-07: Adding Items to Cart
- **Test Case ID**: `TC-07`
- **Test Scenario**: Add a product to the cart from both Product Card and Product Details page.
- **Preconditions**: Cart is currently empty.
- **Test Steps**:
  1. From `/shop`, click "Add to Cart" on *Minimalist Relaxed Fit Organic Cotton Tee* (₹899).
  2. Observe button state and top-right notification.
  3. Observe header cart badge count.
  4. Navigate to details of *PulseFlow Smart Fitness Watch*, select quantity = 2, and click "Add to Cart".
- **Expected Result**:
  - Toast notification appears: `"Added to cart!"`.
  - Button momentarily changes to "Added".
  - Navbar cart badge immediately displays `3` (1 shirt + 2 watches).
- **Actual Result**: Toast alerts trigger smoothly and cart badge updates immediately across the application without reload.
- **Status**: **PASS**

---

### TC-08: Cart Quantity Increase
- **Test Case ID**: `TC-08`
- **Test Scenario**: Increase quantity of a line item on the Shopping Cart page.
- **Preconditions**: An item is in the cart with quantity = 1 (e.g. AcousticPro Headphones at ₹4,999).
- **Test Steps**:
  1. Navigate to `/cart`.
  2. Click the `+` button on the quantity stepper for AcousticPro Headphones.
  3. Observe the displayed quantity and line subtotal.
  4. Observe the order summary subtotal.
- **Expected Result**: Quantity increments to 2; item line total becomes ₹9,998; summary subtotal updates immediately to ₹9,998.
- **Actual Result**: Quantity and all dependent pricing fields recalculate instantly upon click.
- **Status**: **PASS**

---

### TC-09: Cart Quantity Decrease & Minimum Boundary Prevention
- **Test Case ID**: `TC-09`
- **Test Scenario**: Decrease quantity and verify it cannot drop to 0 or negative.
- **Preconditions**: AcousticPro Headphones in cart with quantity = 2.
- **Test Steps**:
  1. On `/cart`, click the `-` button once. Quantity becomes 1.
  2. With quantity at 1, observe whether the `-` button is disabled or prevents decrement.
  3. Attempt to click `-` again.
  4. Attempt to type `0` or `-5` manually into the quantity input.
- **Expected Result**:
  - Decrementing from 2 to 1 updates subtotal to ₹4,999.
  - At quantity = 1, `-` button is disabled.
  - Minimum boundary of 1 is strictly enforced; quantity never becomes 0 or negative.
- **Actual Result**: Quantity stepper restricts values to strictly $\ge 1$; manual inputs $\le 0$ are rejected.
- **Status**: **PASS**

---

### TC-10: Removing Item from Cart
- **Test Case ID**: `TC-10`
- **Test Scenario**: Remove an individual item from the shopping cart.
- **Preconditions**: Cart contains 2 distinct items.
- **Test Steps**:
  1. On `/cart`, click the red trash icon button for one of the items.
  2. Observe the item list, subtotal, and navbar badge count.
- **Expected Result**:
  - The item is removed from the cart table.
  - Toast notification alerts: `"Removed item from cart"`.
  - Navbar cart badge count decreases by the removed item's quantity.
  - Subtotal and total reflect only the remaining item.
- **Actual Result**: Item removed immediately from state and localStorage; totals adjust properly.
- **Status**: **PASS**

---

### TC-11: Cart Persistence After Browser Refresh
- **Test Case ID**: `TC-11`
- **Test Scenario**: Verify cart items and quantities persist across browser refresh and tab reloads.
- **Preconditions**: User has items in cart (e.g., 1 Watch, 1 Shirt).
- **Test Steps**:
  1. Check current items on `/cart`.
  2. Press browser Refresh (F5 / Ctrl+R).
  3. Check cart contents and navbar badge count after page reload.
  4. Close tab and reopen `http://localhost:5173/cart`.
- **Expected Result**: All cart items, quantities, and applied coupons persist identically from `localStorage`.
- **Actual Result**: Verified via `loadCartFromStorage()` and `saveCartToStorage()`; all cart state survives reloads intact.
- **Status**: **PASS**

---

### TC-12: Empty Cart Checkout Prevention
- **Test Case ID**: `TC-12`
- **Test Scenario**: Ensure user cannot checkout with an empty cart.
- **Preconditions**: Shopping cart is empty (`[]`).
- **Test Steps**:
  1. Navigate to `/cart`. Observe empty cart illustration and absence of checkout button.
  2. Manually enter `/checkout` in browser address bar.
- **Expected Result**:
  - `/cart` displays "Your Shopping Cart is Empty" with a "Start Shopping Now" CTA.
  - Direct navigation to `/checkout` displays a warning guard: "Your Cart is Currently Empty. You cannot proceed to checkout..." and provides a button to return to Shop.
- **Actual Result**: Checkout page guard activates and prevents form rendering or submission when cart is empty.
- **Status**: **PASS**

---

### TC-13: Checkout Form Validation (Invalid & Missing Data)
- **Test Case ID**: `TC-13`
- **Test Scenario**: Submit checkout form with invalid, missing, or malformed customer information.
- **Preconditions**: At least 1 item in cart; user navigates to `/checkout`.
- **Test Steps**:
  1. Leave all fields blank and click "Place Demo Order".
  2. Enter invalid email (e.g. `alex@invalid`).
  3. Enter 4-digit phone number (e.g. `1234`).
  4. Enter short address (e.g. `Road`).
  5. Enter 3-digit PIN code (e.g. `560`).
  6. Click "Place Demo Order".
- **Expected Result**:
  - Form submission is blocked.
  - Clear, user-friendly inline error messages are displayed under each invalid field:
    - *"Full name must be at least 3 characters long."*
    - *"Please enter a valid email address."*
    - *"Please enter a valid 10-digit mobile number."*
    - *"Please provide a complete delivery address (at least 10 characters)."*
    - *"PIN code must be exactly 6 digits."*
  - First invalid field receives focus.
- **Actual Result**: `validateCheckoutForm()` successfully catches all errors; red error outlines and message labels appear beneath all non-compliant inputs.
- **Status**: **PASS**

---

### TC-14: Valid Demo Order Placement
- **Test Case ID**: `TC-14`
- **Test Scenario**: Complete demo checkout with valid customer information.
- **Preconditions**: Cart has items totaling $> ₹0$; user is on `/checkout`.
- **Test Steps**:
  1. Enter Full Name: `Priyanshu Sharma`
  2. Enter Email: `priyanshu@example.com`
  3. Enter Mobile Number: `9876543210`
  4. Enter Address: `Flat 402, Sunshine Residency, Outer Ring Road`
  5. Enter City: `Bengaluru`
  6. Select State: `Karnataka`
  7. Enter PIN Code: `560100`
  8. Select Payment Method: `Cash on Delivery (Demo)`
  9. Click "Place Demo Order".
- **Expected Result**:
  - Form validation succeeds.
  - Order object is compiled with unique demo ID, timestamp, items, customer info, and pricing breakdown.
  - Order is saved to `localStorage` under `shopease_orders`.
  - User is navigated to `/order-success/:orderId`.
- **Actual Result**: Order created seamlessly; redirect triggers to Order Confirmation page.
- **Status**: **PASS**

---

### TC-15: Order Confirmation & Post-Order Cart Clearing
- **Test Case ID**: `TC-15`
- **Test Scenario**: Verify order confirmation page display and confirm cart is cleared only after order creation.
- **Preconditions**: Just completed TC-14 demo order placement.
- **Test Steps**:
  1. Inspect the loaded `/order-success/:orderId` page.
  2. Check for unique Order ID format (e.g. `SE-2026-XXXXXX`).
  3. Verify purchased items itemized list matches items ordered.
  4. Verify shipping address and delivery date estimate.
  5. Check Navbar cart badge count.
  6. Click "Continue Shopping".
- **Expected Result**:
  - Order reference ID is clearly visible.
  - All purchased items, quantities, subtotal, and total are displayed.
  - Cart is cleared from storage and memory; Navbar cart badge displays 0.
  - "Continue Shopping" safely returns user to `/shop`.
- **Actual Result**: Unique ID generated properly (e.g. `SE-2026-920543`), itemized receipt matches, cart state successfully cleared upon confirmed placement.
- **Status**: **PASS**

---

### TC-16: User Login & One-Click Demo Authentication
- **Test Case ID**: `TC-16`
- **Test Scenario**: Verify user can log in via credentials or 1-Click Demo Login button.
- **Preconditions**: User is logged out.
- **Test Steps**:
  1. Click "Sign In" in the navigation bar. Verify route is `/login`.
  2. Click "⚡ One-Click Demo Login".
  3. Verify toast notification appears: `"Logged in as Priyanshu Sharma (Demo Account)"`.
  4. Inspect navigation bar.
- **Expected Result**: User session is saved in `localStorage`; Navbar replaces "Sign In" with user avatar and name pill.
- **Actual Result**: Instant demo authentication succeeds; user name and avatar render in header across all pages.
- **Status**: **PASS**

---

### TC-17: Checkout Customer Auto-fill for Logged-In User
- **Test Case ID**: `TC-17`
- **Test Scenario**: Verify customer shipping details auto-fill at Checkout if user is logged in.
- **Preconditions**: User is logged in as Priyanshu Sharma; cart contains at least 1 product.
- **Test Steps**:
  1. Navigate to `/checkout`.
  2. Inspect input fields: Full Name, Email, Phone, Address, City, PIN Code.
- **Expected Result**: All fields are automatically pre-populated with the logged-in user's stored profile info.
- **Actual Result**: Form fields populate automatically with profile values; user can place order in 1 click without retyping.
- **Status**: **PASS**

---

### TC-18: User Logout & Session Invalidation
- **Test Case ID**: `TC-18`
- **Test Scenario**: Verify user can log out from desktop profile menu or mobile drawer.
- **Preconditions**: User is currently logged in.
- **Test Steps**:
  1. Hover / click user profile menu in the navigation bar.
  2. Click "Sign Out (Logout)".
  3. Verify toast notification: `"You have been logged out successfully."`.
  4. Check `localStorage.getItem('shopease_user')`.
  5. Check Navbar user section.
- **Expected Result**: User session is completely purged from `localStorage`; Navbar restores the "Sign In" button; user is redirected to Home.
- **Actual Result**: Session removed cleanly; UI switches to logged-out state immediately.
- **Status**: **PASS**

---

## Conclusion
All 18 comprehensive test cases covering the entire user journey (Homepage, Navigation, Search, Filter, Sort, Details, Cart, Calculations, Persistence, Validation, Checkout, Order Confirmation, Login, Profile, and Logout) were executed, evaluated, and verified with a 100% pass rate.
