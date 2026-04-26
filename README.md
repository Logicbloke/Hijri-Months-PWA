# أَشْهُرُنَا الْهِجْرِيَّة — Hijri Months PWA for Kids

تطبيق ويب تقدّمي (PWA) لتعليم الأطفال أسماء الأشهر الهجرية الاثني عشر من خلال ثلاث ألعاب:

- **رَكِّبِ الشَّهْر** — يرتّب الطفل الحروف لتكوين اسم الشهر.
- **خَمِّنِ الشَّهْر** — يختار الطفل الشهر الصحيح من بين ثلاثة لإجابة سؤال.
- **رَتِّبِ الأَشْهُر** — يُعرَض شهران ثابتان تفصل بينهما خانةٌ فارغة، فيسحب الطفلُ الشَّهرَ المناسب لوضعه بينهما.

كل الأشهر الاثنا عشر مغطّاة بأسئلة، وكلّها تظهر في كلّ لعبة. تُحفظ النجوم محلّيًا في المتصفّح.

---

## الملفات / Files

| File                    | Purpose                                        |
|-------------------------|------------------------------------------------|
| `index.html`            | App shell + both games + UI                   |
| `manifest.webmanifest`  | PWA manifest (Arabic name, RTL, icons, theme) |
| `sw.js`                 | Service worker for offline use                |
| `icon.svg`              | Standard app icon                             |
| `icon-maskable.svg`     | Maskable icon for Android adaptive icons      |

## How to run locally

A service worker requires HTTP(S), so opening `index.html` directly with `file://` will not register the SW. Use any tiny static server from inside the project folder:

```bash
# Python 3
python3 -m http.server 8000

# Or Node
npx serve -l 8000
```

Then open <http://localhost:8000>. On Chrome/Edge you'll see an **Install** icon in the address bar; on iOS Safari, tap *Share → Add to Home Screen*.

## How to deploy

Drop the four files (plus the two SVG icons) on any static host: GitHub Pages, Cloudflare Pages, Netlify, Vercel, S3+CloudFront, Firebase Hosting, etc. The app needs no build step.

## Notes for kids' usage

- All taps trigger gentle audio feedback via Web Audio. The first tap unlocks audio (mobile autoplay policy).
- The app is portrait-locked and uses safe-area insets so it sits correctly on iPhones with notches.
- `prefers-reduced-motion` is respected — confetti and bobbing animations are disabled if the OS asks.
- Star count is saved across sessions in `localStorage`.

## Customization tips

- More trivia questions → push entries to the `QUESTIONS` array in `index.html` (each is `{ q: "…", a: <month number 1–12> }`).
- Change colors per month → edit the `c1`/`c2`/`cs` (gradient + shadow) fields in `MONTHS`.
- Translation/transliteration → edit each month's `name` (vocalized) and `plain` (used by the letter game).
