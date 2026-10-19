# Shox Mobile — o‘rnatish qo‘llanmasi

## Nimalar bor?
- Premium qora-oltin internet-magazin (`public/index.html`)
- Savat va buyurtma formasi
- Server tomonda narxlarni tekshirish
- Buyurtmalarni serverda saqlash (`data/orders.json`)
- Telegram bot orqali buyurtma bildirishnomasi
- Himoyalangan admin paneli (`/admin`)
- Mahsulot qo‘shish, tahrirlash, yashirish
- Buyurtma holatini o‘zgartirish

## Telefonning o‘zida sinab ko‘rish
Bu loyiha oddiy HTML fayl kabi to‘g‘ridan-to‘g‘ri ochilmaydi: server ishga tushishi kerak. Telefonning brauzeri kod yozish uchun emas, tayyor saytni tekshirish uchun ishlatiladi. Eng oson yo‘l — internetdagi Node.js hostingga joylash. Telefon brauzeridan hosting boshqaruviga kirish mumkin, lekin birinchi sozlash kompyuterda qulayroq.

## Ishga tushirish (Node.js 18+)
1. Loyihani kompyuterga yuklab oling va ZIPni oching.
2. Node.js 18 yoki undan yangisini o‘rnating.
3. Terminalda loyiha papkasiga kiring.
4. `.env.example` faylidan nusxa olib, nomini `.env` qiling.
5. `.env` ichida `SESSION_SECRET`, `ADMIN_USERNAME`, `ADMIN_PASSWORD` qiymatlarini o‘zgartiring. Parol kamida 12 belgidan iborat bo‘lsin.
6. `npm install`
7. `npm start`
8. Brauzerda `http://localhost:3000` oching. Admin: `http://localhost:3000/admin`.

## Telegram bot sozlash
1. Telegramda rasmiy `@BotFather` ni oching.
2. `/newbot` yuboring va ko‘rsatmalar bo‘yicha bot nomi hamda username yarating.
3. BotFather bergan tokenni maxfiy saqlang. Uni hech kimga yubormang va frontend HTML ichiga yozmang.
4. Yangi botni ochib `/start` yuboring.
5. Shaxsiy chatga bildirishnoma kelishi uchun bot tokeni va chat ID kerak. Chat ID ni Telegram bot API orqali olish mumkin; tokenni faqat serverdagi `.env` fayliga yozing. Guruhga yuborish kerak bo‘lsa, botni guruhga qo‘shing va guruh chat ID sini ishlating.
6. `.env` ichiga `TELEGRAM_BOT_TOKEN=...` va `TELEGRAM_CHAT_ID=...` kiriting.
7. Serverni qayta ishga tushiring va test buyurtma yuboring.
8. Bot xabar yubormasa, token/chat ID va botga `/start` yuborilganini tekshiring. Tokenni ochiq joyda ulashmang.

## Muhim cheklovlar
- Hozirgi JSON saqlash usuli kichik sinov/do‘kon prototipi uchun. Hosting qayta o‘rnatilsa yoki disk vaqtinchalik bo‘lsa, buyurtmalar yo‘qolishi mumkin. Ishlab chiqarish uchun doimiy disk yoki PostgreSQL/Supabase kabi ma’lumotlar bazasi ishlating.
- Hostingda HTTPS ishlating va `NODE_ENV=production` o‘rnating. Aks holda secure cookie ishlamasligi mumkin.
- `express-session` ning standart MemoryStore'i ko‘p foydalanuvchi yoki production uchun mos emas. Productionda Redis yoki boshqa session store ulang.
- `.env` faylini GitHubga yoki ommaviy joyga yuklamang.
- Bu to‘lov tizimi emas; online karta to‘lovi ulanmagan.
- Android APK bu paketga kiritilmagan. Sayt avval internetda HTTPS bilan ishlashi kerak; so‘ng Android Studio/WebView yoki Trusted Web Activity orqali ilovaga o‘tkazish mumkin.
