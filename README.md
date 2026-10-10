# הטיול שלנו ליער השחור 🌲

אתר עם מסלול הטיול המשפחתי ליער השחור, לאלזס ולאגם קונסטנץ (15–29 באוגוסט 2027):
לו״ז יומי, אטרקציות בכרטיס האדום (Hochschwarzwald Card), לינה, קישורי ניווט, מזג אוויר, עלויות ומספרי חירום.

## צפייה
- לפתוח את `index.html` בדפדפן, או
- להפעיל GitHub Pages: Settings → Pages → Deploy from a branch → בוחרים את הענף ואת התיקייה `/ (root)`.

## להשלים
- **פרטי הטיסות:** ב־`index.html`, במערך `TRIP_FLIGHTS` (חברה, מספר טיסה ושעות). אחרי שממלאים אותם, האתר בודק את הטיסה מול לוח נתב״ג.
- **תמונות המלונות:** ראו `img/hotels/README.md`.
- **תמונת הרקע למעלה:** אם שמים תמונה בשם `img/hero.jpg` (רצוי ברוחב 1,600 פיקסלים לפחות), היא מוצגת במקום תמונות הנוף מוויקיפדיה.

## מעקב מחירים

`.github/workflows/prices.yml` רץ כל יומיים, מריץ את `scripts/check-prices.mjs` (בודק ב־Google Flights / Google Hotels דרך SerpApi) ושומר את התוצאות ב־`data/prices.json`. האתר מציג אותן בכרטיס "📉 מעקב מחירים".
כדי להפעיל: להוסיף ב־Settings → Secrets and variables → Actions סוד בשם `SERPAPI_KEY` עם המפתח מ־serpapi.com (ואם רוצים גיבוי דרך Booking.com, גם `RAPIDAPI_KEY`). אפשר להריץ ידנית מלשונית Actions → Price tracker → Run workflow.
