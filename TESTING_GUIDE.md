# Real-World Testing Guide
**Astrology Consultation Landing Page**  
**Date:** February 6, 2026

---

## 🚀 Quick Start - Local Testing

### **Option 1: Python HTTP Server (Recommended)**

A local server is currently running at:
```
http://localhost:8000
```

**To start the server manually:**
```bash
cd "c:\Users\Saransh\OneDrive\Documents\Astrology Consultation Landing Page"
python -m http.server 8000
```

Then open your browser and navigate to: **http://localhost:8000**

### **Option 2: Direct File Access**

Open the file directly in your browser:
```
file:///c:/Users/Saransh/OneDrive/Documents/Astrology%20Consultation%20Landing%20Page/index.html
```

**Note:** Some features (like fonts) may not work properly with file:// protocol. Use the HTTP server method instead.

### **Option 3: Live Server (VS Code)**

If you have VS Code with Live Server extension:
1. Right-click on `index.html`
2. Select "Open with Live Server"
3. Website will open at `http://127.0.0.1:5500`

---

## 📋 Step-by-Step Testing Instructions

### **Phase 1: Initial Visual Inspection** (5 minutes)

1. **Open the website** at http://localhost:8000
2. **First Impressions:**
   - Does the page load quickly?
   - Is the hero section visually appealing?
   - Are fonts loading correctly?
   - Is the color scheme (deep blue, gold, white) consistent?

3. **Scroll through all sections:**
   - Hero → About → Services → Process → Pricing → Testimonials → FAQ → Footer
   - Note any visual glitches, overlapping elements, or broken layouts

4. **Check images:**
   - Hero background image
   - Zodiac wheel in testimonials
   - Any broken image placeholders

### **Phase 2: Navigation Testing** (5 minutes)

1. **Test navigation links:**
   - Click "About" → Should smooth scroll to About section
   - Click "Services" → Should smooth scroll to Services
   - Click "Process" → Should smooth scroll to Process
   - Click "Testimonials" → Should smooth scroll to Testimonials
   - Click "FAQ" → Should smooth scroll to FAQ

2. **Test sticky navbar:**
   - Scroll down the page
   - Navbar should stick to the top
   - Navbar should get a subtle shadow when scrolling

3. **Test mobile navigation:**
   - Resize browser to mobile width (<768px)
   - Hamburger menu should appear
   - Click hamburger → Menu should expand
   - Click a link → Menu should close

### **Phase 3: Language Switching** (5 minutes)

1. **Test English (default):**
   - All text should be in English
   - Font should be Lato/Playfair Display

2. **Switch to Hindi:**
   - Click language dropdown → Select "हिंदी"
   - All text should change to Hindi (Devanagari script)
   - Font should change to Noto Sans Devanagari
   - Check all sections for proper translation

3. **Switch to Odia:**
   - Click language dropdown → Select "ଓଡ଼ିଆ"
   - All text should change to Odia script
   - Font should change to Noto Sans Oriya
   - Check for any broken characters

4. **Test persistence:**
   - Refresh the page
   - Selected language should be maintained

### **Phase 4: Booking Modal Testing** (10 minutes)

#### **Test Modal Opening:**

1. **From Hero Section:**
   - Click "Book Consultation" button
   - Modal should open centered on screen
   - Background should darken

2. **From Pricing Cards:**
   - Click "Book Now" on Standard package
   - Modal should open with "Standard" pre-selected
   - Close modal (click X or backdrop)
   - Click "Book Now" on Detailed package
   - Modal should open with "Detailed" pre-selected
   - Repeat for Premium package

3. **From Sticky CTA (Mobile only):**
   - Resize to mobile (<768px)
   - Sticky button should appear at bottom
   - Click it → Modal should open

4. **From Navigation:**
   - Click "Book Consultation" in navbar
   - Modal should open

#### **Test Step 1 - Personal Details:**

1. **Fill out the form:**
   - **Name:** Enter "Test User"
   - **Phone:** Try entering letters → Should not accept
   - **Phone:** Try entering special characters → Should not accept
   - **Phone:** Enter "1234567890" → Should accept
   - **Date of Birth:** Select any past date
   - **Time of Birth:** Enter hour (e.g., 10), minute (e.g., 30), select AM/PM
   - **Place of Birth:** Enter "Mumbai, Maharashtra"
   - **Package:** Should show pre-selected package

2. **Test validation:**
   - Leave all fields empty
   - Click "Next" → Fields should show red borders
   - Fill phone with only 9 digits → Should show error alert
   - Fill all fields correctly → Should proceed to Step 2

#### **Test Step 2 - Preferences:**

1. **Verify Step 2 appears:**
   - Step 1 should hide
   - Step 2 should show

2. **Test date picker:**
   - Click "Preferred Date" field
   - Try selecting yesterday's date → Should not be selectable
   - Select tomorrow's date → Should accept

3. **Test time slot:**
   - Select "Morning (9 AM - 12 PM)"

4. **Test Back button:**
   - Click "Back" → Should return to Step 1
   - All previously entered data should still be there
   - Click "Next" again → Should go back to Step 2

5. **Test form submission:**
   - Click "Proceed to Payment"
   - Should open WhatsApp in new tab
   - Check WhatsApp message contains:
     - Package name
     - Your name
     - Phone number
     - Date of birth with time
     - Place of birth
     - Preferred date and time
   - WhatsApp number should be: +91 99676 19656

6. **Test modal reset:**
   - After WhatsApp opens, modal should close
   - Re-open modal → Should start fresh at Step 1
   - Previous data should be cleared

### **Phase 5: Interactive Elements** (5 minutes)

1. **Test FAQ Accordion:**
   - Click first question → Should expand
   - Click second question → Should expand
   - Click first question again → Should collapse
   - Chevron icon should rotate when expanding/collapsing

2. **Test WhatsApp Links:**
   - Click "WhatsApp Chat" in hero section
   - Should open WhatsApp with correct number
   - Click WhatsApp button in footer
   - Should open WhatsApp with correct number

3. **Test hover effects:**
   - Hover over service cards → Should lift slightly
   - Hover over buttons → Should change color and lift
   - Hover over navigation links → Should change to gold

### **Phase 6: Responsive Design Testing** (10 minutes)

Test at these breakpoints:

1. **Desktop (1920x1080):**
   - Full layout with all elements side-by-side
   - Pricing cards in a row
   - About section in 2 columns

2. **Laptop (1366x768):**
   - Similar to desktop but slightly compressed
   - All elements should fit

3. **Tablet (768x1024):**
   - About section should stack
   - Pricing cards might wrap
   - Navigation should still be horizontal

4. **Mobile (375x667):**
   - Hamburger menu appears
   - All sections stack vertically
   - Sticky CTA appears at bottom
   - Pricing cards stack
   - Hero text is smaller but readable
   - Modal is full-width with padding

**How to test responsive:**
- Use browser DevTools (F12)
- Click "Toggle Device Toolbar" (Ctrl+Shift+M)
- Select different devices from dropdown
- Or manually resize browser window

### **Phase 7: Performance Testing** (5 minutes)

1. **Open DevTools (F12)**
2. **Go to Network tab**
3. **Refresh the page (Ctrl+R)**
4. **Check:**
   - Total page size (should be ~2.5MB currently)
   - Number of requests
   - Load time (DOMContentLoaded, Load)
   - Largest files (images are likely biggest)

5. **Run Lighthouse Audit:**
   - Open DevTools → Lighthouse tab
   - Select "Desktop" or "Mobile"
   - Click "Generate report"
   - Review scores for:
     - Performance
     - Accessibility
     - Best Practices
     - SEO

6. **Test with throttling:**
   - Network tab → Throttling dropdown
   - Select "Slow 3G"
   - Refresh page
   - Note load time (should be slower)

### **Phase 8: Cross-Browser Testing** (15 minutes)

Test the same website in different browsers:

1. **Chrome:** http://localhost:8000
2. **Firefox:** http://localhost:8000
3. **Edge:** http://localhost:8000
4. **Safari (if on Mac):** http://localhost:8000

**Check for:**
- Layout differences
- Font rendering
- Color accuracy
- Animation smoothness
- Modal behavior
- Form functionality

---

## 🐛 Bug Reporting Template

If you find any issues, document them like this:

```
**Bug Title:** [Short description]
**Severity:** Critical / Medium / Minor
**Browser:** Chrome 120 / Firefox 121 / etc.
**Device:** Desktop / Mobile / Tablet
**Screen Size:** 1920x1080 / 375x667 / etc.

**Steps to Reproduce:**
1. Step 1
2. Step 2
3. Step 3

**Expected Result:**
What should happen

**Actual Result:**
What actually happened

**Screenshot:** [Attach if possible]
```

---

## ✅ Testing Completion Checklist

After completing all phases, verify:

- [ ] All sections load and display correctly
- [ ] Navigation works smoothly
- [ ] Language switching works in all 3 languages
- [ ] Booking modal works end-to-end
- [ ] WhatsApp integration works
- [ ] All forms validate correctly
- [ ] Responsive design works on all breakpoints
- [ ] No console errors (check DevTools Console tab)
- [ ] Performance is acceptable (Lighthouse score >70)
- [ ] Cross-browser compatibility verified

---

## 📊 Expected Results

### **What Should Work:**
✅ All navigation and smooth scrolling  
✅ Language switching (EN/HI/OD)  
✅ Booking modal with 2-step form  
✅ Phone number validation (10 digits only)  
✅ Date validation (no past dates)  
✅ WhatsApp redirect with formatted message  
✅ FAQ accordion  
✅ Responsive design on all devices  
✅ Sticky navbar with shadow on scroll  
✅ Mobile hamburger menu  
✅ Sticky mobile CTA  

### **Known Limitations:**
⚠️ Images are large (~2.5MB total) - will slow down on slow connections  
⚠️ No image compression yet  
⚠️ Calendly integration is placeholder only  
⚠️ Razorpay payment not integrated  
⚠️ Social media links are placeholders (#)  

---

## 🎯 Next Steps After Testing

1. **Document all bugs found** using the template above
2. **Prioritize fixes** (Critical → Medium → Minor)
3. **Implement fixes** one by one
4. **Retest** after each fix
5. **Run final regression test** to ensure nothing broke
6. **Proceed with Phase 2 optimizations** (image compression, minification)

---

## 💡 Pro Tips

- **Use Incognito/Private mode** to test without cache
- **Clear browser cache** between tests (Ctrl+Shift+Delete)
- **Test with different user personas** (tech-savvy vs. non-tech)
- **Test on actual mobile devices** if possible (not just DevTools)
- **Take screenshots** of any issues you find
- **Check browser console** for JavaScript errors (F12 → Console)
- **Test with slow internet** to see real-world performance

---

## 🚀 Ready to Test!

**Current Status:** Local server is running at http://localhost:8000

**Start Testing Now:**
1. Open your browser
2. Navigate to http://localhost:8000
3. Follow the testing phases above
4. Document any issues you find
5. Report back with results!

---

**Happy Testing! 🎉**
