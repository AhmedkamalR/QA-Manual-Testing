# 🛒 Product & Catalog - Test Scenarios

This document outlines **comprehensive test scenarios** for the **Product & Catalog module** across API, Website, and Mobile App.  
It aims to ensure **end-to-end coverage** before writing detailed test cases.

---

## 1. API Scenarios

### ✅ Valid Scenarios
- Retrieve all active products with valid parameters.
- Retrieve product details by valid product ID.
- Fetch products by valid category ID.
- Filter by brand, tags, or price range.
- Fetch products sorted by price, rating, popularity.
- Support pagination (page & limit parameters).
- Retrieve related/upsell/cross-sell products.
- Retrieve featured products & best sellers.
- Retrieve recently viewed products (if API supports).
- Retrieve stock availability and quantity.

### ❌ Invalid Scenarios
- Invalid product ID (non-existing, string instead of int).
- Invalid category ID.
- Invalid filter values (e.g., negative price).
- Invalid pagination values (page = -1, limit = 0).
- Missing required parameters.
- Request without authentication (if required).
- Product not available in region (blocked response).
- API returns 500 instead of handled error.

### ⚠️ Edge Scenarios
- Product with very long description (DB max length).
- Product with 0 price (free / bug).
- Product with multiple overlapping discounts.
- Product without image(s).
- Product with 20+ variations (color, size, etc.).
- Requesting 1000+ products in one call.
- Product marked as archived/inactive but still retrievable.
- Product available in one language only.

---

## 2. Website Scenarios

### ✅ Valid Scenarios
- Navigate to category and see correct product listing.
- Apply filters (price, brand, rating, stock).
- Sort products (Low to High, Popularity, Newest).
- Search inside product catalog page.
- Open product details page and validate title, price, description, images.
- Verify product variations (color/size) selection works.
- Add product to cart from listing and from product details.
- Verify "Add to Wishlist" works correctly.
- Check breadcrumbs navigation on product details.
- Verify recently viewed products section appears.
- Verify related/upsell/cross-sell products section appears.

### ❌ Invalid Scenarios
- Try to access product details with invalid product ID in URL.
- Product page shows broken images.
- Product without translations in selected language.
- Add to cart for inactive product.
- Wishlist action without login (if not allowed).
- Incorrect SEO metadata for product page.
- 404 error not handled properly when product doesn’t exist.

### ⚠️ Edge Scenarios
- Product with 15+ images in gallery.
- Product with 5+ variations combined (color+size+material).
- Product with no stock (should disable Add to Cart).
- Product with countdown timer for offer (check behavior after expiry).
- Very high-priced product (e.g., 1M).
- Product with multi-currency display.
- Product with long name (UI alignment).
- Product with HTML/JS in description (XSS risk).

---

## 3. Mobile App Scenarios

### ✅ Valid Scenarios
- View products in category with infinite scroll.
- Open product details, swipe through images.
- Select product variation (dropdown/swatches).
- Add product to cart from list and from details.
- Wishlist & share product.
- Zoom functionality on product images.
- Verify recently viewed products appear.
- Check offline caching of previously opened product.

### ❌ Invalid Scenarios
- Open product with invalid product ID via deep link.
- Product with invalid image crashes app.
- Wishlist without login (if restricted).
- Product not available in region/language.

### ⚠️ Edge Scenarios
- Product with extremely long name breaks UI.
- Product with missing description field.
- Product with large hi-res images (slow load).
- Switching language (EN/AR) mid-product view.
- App offline mode (open product page).
- Multi-variant product with 30+ options.
- Product with AR/VR view (if supported).
- Push notification deep link opens inactive product.

---

## ✅ Key Values / Keywords
- **Entities:** Product, Category, Brand, Attributes, Variations, Images.  
- **Parameters:** product_id, category_id, brand_id, page, limit, language, price_range.  
- **States:** Active, Inactive, In Stock, Out of Stock, Archived, Discounted.  
- **Edge:** Long text, Missing translations, Multi-variation, Large pagination, Region restrictions.  

---
