# 🌐 Website – Product Catalog Test Cases

This document contains detailed **test cases** for the **Product Catalog on Website**.  
Covers **Valid, Invalid, and Edge Scenarios** to ensure comprehensive QA coverage.

---

## ✅ Valid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Navigate to homepage → open category (e.g., Electronics) | Correct category products are displayed | – |
| 2 | Apply filter by **brand** (Apple) | Only Apple products are shown | – |
| 3 | Apply filter by **price range** (100–500) | Products shown only within range | – |
| 4 | Apply multiple filters (brand + price + stock) | Combined filter applied correctly | – |
| 5 | Sort by **Price: Low to High** | Products are correctly sorted ascending | – |
| 6 | Sort by **Newest** | Latest products appear on top | – |
| 7 | Open product details from catalog | Correct product details page opens | Screenshot |
| 8 | Verify product variations (color/size) selection | Correct SKU/price/image updates | – |
| 9 | Add product to cart from listing | Product successfully added | – |
| 10 | Add product to cart from product details page | Product added to cart | – |
| 11 | Add product to wishlist (logged in) | Product added to wishlist | – |
| 12 | Breadcrumbs navigation works from product details | User is redirected correctly | – |
| 13 | Verify **Recently Viewed** products section | Recently visited items appear | – |
| 14 | Verify **Related/Recommended** products | Correct products displayed | – |
| 15 | Check SEO metadata (title, description, schema) | Metadata matches product info | – |

---

## ❌ Invalid Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Try opening product with invalid ID in URL (`/product/abc`) | 404 error page shown | – |
| 2 | Open product that is inactive/out of stock | Proper error or disabled actions shown | – |
| 3 | Apply filter with invalid values (price -100) | System rejects or shows no results safely | – |
| 4 | Apply filter combination returning empty result | “No products found” message appears | – |
| 5 | Wishlist action without login (if restricted) | Redirect to login page | – |
| 6 | Add inactive/archived product to cart (force URL) | System blocks with proper error | – |
| 7 | Product page loads with missing translations | Fallback text or handled gracefully | – |
| 8 | Product images missing/broken | Placeholder image displayed | – |
| 9 | Sorting parameter invalid in URL (`sort=xyz`) | Default sorting applied | – |
| 10 | Access unauthorized product (region restriction) | Error or empty state displayed | – |

---

## ⚠️ Edge Test Cases

| Step | Action | Expected Result | Attachments |
|------|--------|-----------------|-------------|
| 1 | Open product with **15+ images** | Gallery works without crash | – |
| 2 | Open product with **5+ variations** (color + size + material) | All variations selectable | – |
| 3 | Product with **0 stock** | “Out of stock” message, Add to Cart disabled | – |
| 4 | Product with **countdown offer** expired | Correct behavior after expiry | – |
| 5 | Product with **very high price (1M+)** | UI displays correctly | – |
| 6 | Product with **multi-currency display** | Currency switches correctly | – |
| 7 | Product with **long name (100+ chars)** | Name wraps properly, no UI break | Screenshot |
| 8 | Product with HTML/JS in description (`<script>`) | Script sanitized, no XSS popup | – |
| 9 | Pagination edge: last page | Proper navigation and empty state handled | – |
| 10 | Rapid filter apply/remove repeatedly | System stable, no crash | – |
| 11 | Simultaneous filters (brand + rating + availability + tags) | Correct behavior, no performance issue | – |
| 12 | Load testing: open category with 500+ products | Page performance within SLA | – |

---

## 📌 Coverage Achieved

- **Valid Scenarios**: Category navigation, filters, sorting, product details, variations, add to cart, wishlist, breadcrumbs, SEO, related/recently viewed products.  
- **Invalid Scenarios**: Broken links, invalid IDs, missing translations, empty filters, unauthorized wishlist, inactive products, missing images, invalid sort.  
- **Edge Scenarios**: Long names, high prices, multiple variations, many images, multi-currency, countdown offers, last page pagination, rapid actions, load handling.  
- **Security**: Handled XSS in descriptions, unauthorized wishlist/cart actions, restricted region products.  
- **Performance**: Verified catalog loads under SLA with filters, pagination, and high-volume products.  
- **Usability & Reliability**: Ensured clear error messages, proper placeholders, responsive UI handling for long text and many variations.  
