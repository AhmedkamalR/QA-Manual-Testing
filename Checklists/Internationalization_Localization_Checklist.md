# 🌍 Internationalization & Localization Checklist

This checklist validates proper internationalization (I18n) support and localization (L10n) quality — languages, formats, currency, RTL support and cultural correctness.

---

## ✅ Internationalization (I18n) - Technical Readiness
- [ ] Ensure UI strings are externalized (no hard-coded text).  
- [ ] Use locale-aware libraries for date/time/currency formatting.  
- [ ] Support UTF-8 encoding across DB, API, and UI.  
- [ ] Implement locale switching mechanism and persist user locale.  
- [ ] Ensure layout adapts for RTL (Arabic, Hebrew) and LTR languages.  
- [ ] Verify text concatenation and placeholders support ordering per locale.

## 🌐 Localization (L10n) - Content Quality
- [ ] Validate translations for all UI strings (professionally translated).  
- [ ] Check locale-specific content (terms, legal text, measurement units).  
- [ ] Verify pluralization rules are correctly applied per language.  
- [ ] Ensure placeholders (e.g., "%s items") are localized correctly.  
- [ ] Verify currency symbols, separators, and decimal rules per locale.  
- [ ] Validate number formatting (thousands separators) per locale.

## 🖥 UI & Layout
- [ ] Check UI for text expansion (translated text length) — no overflow or cutoffs.  
- [ ] Verify date pickers and calendars match locale format (dd/mm/yyyy vs mm/dd/yyyy).  
- [ ] Confirm RTL mirrors UI correctly (icons, progress flows, breadcrumbs).  
- [ ] Validate sorting and collation rules for localized strings.

## 🧪 Functional Checks
- [ ] Validate checkout prices display correct currency & conversion (if applicable).  
- [ ] Test payments with localized payment methods and gateways.  
- [ ] Verify validation messages and error text localized.  
- [ ] Ensure email templates (order confirmation) are localized.  
- [ ] Check search behavior for localized content (accented chars, diacritics).

## 🔁 Edge Cases & QA
- [ ] Test mixed-language inputs (user enters Arabic+English).  
- [ ] Validate UI with very long translated strings.  
- [ ] Ensure fallback locale works when translation missing.  
- [ ] Test sorting, filtering and searching with locale-specific collation.  
- [ ] Validate SEO metadata (hreflang tags, localized URLs) if applicable.

---

## 📌 Value
Proper I18n/L10n testing ensures the product is usable and culturally correct in target regions — reducing user confusion, increasing trust, and improving conversion globally.
