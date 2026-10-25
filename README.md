# POLARIS ורז-גל – הפנינג מכירות, אולמי נסיה

דף נחיתה סטטי (HTML + CSS בלבד, ללא build) שמוביל לוואטסאפ.
מבוסס על העיצוב והמבנה של דף הנחיתה `royal-enfield-test-ride-afula`.

## מבנה
```
index.html                      הדף כולו (סגנונות וסקריפט מוטמעים)
vercel.json                     הגדרות Vercel (cache, headers)
assets/images/event-poster.webp     מודעת האירוע המקורית (1080×1080), מוצגת בשלמותה ללא חיתוך
assets/images/event-poster-og.jpg  אותה מודעה ב-JPG לתצוגה מקדימה בשיתוף (WhatsApp/Facebook)
```

## הרצה מקומית
```
npx serve .
```

## פרסום ב-Vercel
לייבא את ה-Repository ב-Vercel, Framework Preset: **Other**, ללא Build Command ו-Output Directory.
אחרי הפרסום מומלץ לעדכן ב-`index.html` את `og:image` (ואת `image` ב-JSON-LD) לכתובת מלאה של הדומיין.

## Google Tag Manager ומדידת לחיצות
מזהה GTM עדיין לא הוגדר. כדי להפעיל: לעדכן ב-`<head>` של `index.html` את
`window.GTM_ID = '';` למזהה הקונטיינר (למשל `'GTM-XXXXXXX'`).

כל לחיצה אמיתית על כפתור וואטסאפ שולחת ל-dataLayer (אין שליחה בטעינת הדף):
`{ event: 'whatsapp_click', campaign: 'polaris-razgal-event', cta_location: 'main' | 'sticky' }`

ההגדרות של GA4 / Meta Pixel / Google Ads נעשות בתוך GTM:
Trigger מסוג Custom Event בשם `whatsapp_click`, ו-Data Layer Variables בשם `campaign` ו-`cta_location`.

## שינוי מספר / הודעה
הקישור נמצא פעמיים ב-`index.html` (כפתור ראשי וכפתור צף). פורמט: `https://wa.me/<מספר>?text=<הודעה מקודדת>`.
קידוד הודעה חדשה: `node -e "console.log(encodeURIComponent('ההודעה'))"`.
