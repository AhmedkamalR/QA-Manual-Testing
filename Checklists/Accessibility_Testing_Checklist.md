# ♿ Accessibility Testing Checklist

This checklist ensures that the **E-commerce platform** is accessible to all users, including those with disabilities.  
It follows **WCAG (Web Content Accessibility Guidelines)** and **ARIA standards** for compliance.  

---

## ✅ Accessibility Testing Checks

### 1. General Accessibility
- [ ] All pages have meaningful and unique titles.  
- [ ] Proper use of semantic HTML elements (`<header>`, `<main>`, `<footer>`, `<nav>`).  
- [ ] Keyboard navigation works across all pages without mouse use.  
- [ ] Focus indicators are visible and consistent.  
- [ ] No keyboard traps (user can navigate freely using TAB/SHIFT+TAB).  

### 2. Screen Reader Compatibility
- [ ] Alternative text (`alt`) exists for all meaningful images.  
- [ ] Decorative images are marked with empty `alt=""`.  
- [ ] Form inputs have proper labels (`<label>` linked via `for` attribute).  
- [ ] ARIA roles and attributes are implemented correctly.  
- [ ] Dynamic content updates are announced by screen readers.  

### 3. Color & Contrast
- [ ] Text color contrast ratio meets **minimum 4.5:1** (WCAG AA).  
- [ ] Large text (18pt+) has at least **3:1 contrast**.  
- [ ] No information is conveyed **only by color** (e.g., error messages also have icons/text).  
- [ ] Background images or gradients do not hinder text readability.  

### 4. Forms & Inputs
- [ ] Required fields are marked clearly and programmatically.  
- [ ] Error messages are descriptive and linked to the input field.  
- [ ] Form validation works for assistive technologies.  
- [ ] Placeholder text is not used as a replacement for labels.  

### 5. Media & Multimedia
- [ ] Video content has captions/subtitles.  
- [ ] Audio content has transcripts.  
- [ ] Auto-playing media can be paused, stopped, or muted.  
- [ ] Flashing content complies with seizure safety guidelines (no >3 flashes/sec).  

### 6. Mobile Accessibility
- [ ] Touch targets are at least **44x44px**.  
- [ ] Responsive design works with zoom (up to 200%).  
- [ ] Orientation change (portrait/landscape) is supported.  
- [ ] VoiceOver (iOS) and TalkBack (Android) work properly.  

---

## 🎯 Purpose
The purpose of this checklist is to ensure the **E-commerce application is inclusive** and usable by people with disabilities, meeting accessibility compliance standards.

---

## 📌 Value
Having this checklist ensures:  
- Compliance with **WCAG & ADA standards**.  
- Better usability for all users, including those with disabilities.  
- Reduced risk of **legal issues** related to accessibility.  
- Improved overall **user experience and inclusiveness**.  
