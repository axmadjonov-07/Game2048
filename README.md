# 2048 Qizil-Qora — mobil ilova

Bu papkada 2048 o'yinining to'liq tayyor Android/iOS loyihasi (Capacitor asosida) joylashgan. O'yinning o'zi `www/index.html` faylida — boshqa hech narsaga muhtoj emas (server, internet kerak emas, butunlay offline ishlaydi).

## ENG OSON YO'L: GitHub Actions orqali tayyor APK olish (kompyuterga hech narsa o'rnatmasdan)

1. github.com saytida bepul hisob oching (agar yo'q bo'lsa).
2. Yangi repository yarating (masalan `game2048`), **Public** qilib qo'ying.
3. Shu papkadagi barcha fayllarni o'sha repositoryga yuklang (GitHub saytida "Add file → Upload files" orqali, yoki `git push` bilan).
4. Repository ichida tepada **Actions** bo'limini oching.
5. "Build APK" workflow paydo bo'ladi — agar avtomatik ishga tushmagan bo'lsa, **Run workflow** tugmasini bosing.
6. 3-5 daqiqada build tugaydi (yashil belgi chiqadi). Workflow natijasini oching, pastda **Artifacts** bo'limidan `2048-android-apk` faylini yuklab oling — bu zip ichida `app-debug.apk` bor.
7. Telefoningizga shu APK'ni o'tkazib, oching — "Noma'lum manbalardan o'rnatish" so'ralsa ruxsat bering. O'yin o'rnatiladi va ishlay boshlaydi.

Bu usul to'liq bepul, kompyuterga hech narsa o'rnatish kerak emas, faqat GitHub hisobi kifoya.

## Agar o'z kompyuteringizda build qilmoqchi bo'lsangiz (Android Studio orqali)

1. [Android Studio](https://developer.android.com/studio) ni o'rnating.
2. Bu papkani Android Studio'da `android` papkasi sifatida oching (File → Open → shu loyihaning `android` papkasini tanlang).
3. Studio avtomatik Gradle sinxronizatsiyasini boshlaydi (birinchi marta Android SDK kerakli qismlarini yuklab oladi — internet kerak).
4. Tugagach, yuqorida **Run** (yashil uchburchak) tugmasini bosing — ulangan telefon yoki emulyatorda ochiladi.
5. Haqiqiy APK fayl olish uchun: Build → Build Bundle(s) / APK(s) → Build APK(s). Tayyor fayl `android/app/build/outputs/apk/debug/app-debug.apk` da bo'ladi.

## iOS uchun (.ipa)

iOS ilovasini compile qilish va imzolash faqat **macOS + Xcode + Apple Developer hisobi** orqali mumkin — bu Apple'ning o'zining qoidasi, hech qanday onlayn xizmat buni Mac'siz qila olmaydi.

1. Mac kompyuterda Xcode o'rnating.
2. Terminalda shu papkada: `npx cap add ios` so'ng `npx cap open ios`.
3. Xcode ochiladi. O'z Apple ID'ingiz bilan "Signing & Capabilities" bo'limida team tanlang.
4. Run tugmasini bosib ulangan iPhone'ga o'rnatishingiz mumkin (bepul Apple ID bilan ham ishlaydi, faqat 7 kunda qayta imzolash kerak bo'ladi — Apple cheklovi).
5. App Store'ga chiqarish uchun esa pullik Apple Developer hisobi ($99/yil) kerak bo'ladi.

## Loyiha tarkibi

- `www/index.html` — o'yinning o'zi (HTML/CSS/JS, hech qanday tashqi bog'liqlik yo'q)
- `android/` — to'liq Android Studio loyihasi
- `capacitor.config.json` — ilova nomi, ID va ranglari
- `.github/workflows/build-apk.yml` — GitHub orqali avtomatik APK build qiluvchi sozlama
