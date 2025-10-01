# ✈️ DVA Theme v2.2.1

A custom **phpVMS 7.x theme** for **DVA** — built with **Bootstrap 5 + TailwindCSS** for a clean, modern pilot dashboard.

---

## ✨ Features
- 🚀 Responsive layout (Bootstrap 5 + TailwindCSS utilities)
- 🌈 Gradient hero headers & glass-style dashboard cards
- 🛠 Modular Blade widgets for easy customization
- 🎨 Emoji-enhanced navigation icons:
  - 📜 Policies
  - 🛫 Flights
  - 👤 Profile
  - 🌦️ Live Weather
- 🏆 Pilot profile styling: avatar ring, chips, progress bar, awards grid
- 📊 Built-in widgets:
  - Rank Progress (“Captain in 23 hrs”)
  - Average Scores Chart + Sparklines
  - Pending PIREPs & PIREP History
  - Live Weather iframe
- 📍 Optional support for **Hubs** and **Tours** modules

---

## 📂 File Structure
```
DVA Theme v2.2.1/
├── resources/
│   ├── views/
│   │   ├── layouts/
│   │   │   ├── seven/        # Main theme layout
│   │   │   │   ├── app.blade.php
│   │   │   │   ├── dashboard/
│   │   │   │   │   └── index.blade.php
│   │   │   │   └── partials/ # Navbar, footer, etc.
│   │   └── pages/            # Example pages (Policies, Terms, Weather)
│   └── public/               # CSS/JS/images
├── README.md
└── composer.json             # Theme definition
```

---

## ⚙️ Installation
1. Extract `DVA Theme v2.2.1.zip`.
2. Copy the `resources/views/layouts/` folder into your phpVMS project.
3. In phpVMS Admin → Settings → **Theme**, select **dva_v2.2.1**.
4. Run:
   ```bash
   php artisan view:clear
   ```
5. (Optional) Add module routes for **Hubs** or **Tours** pages.

---

## 📝 Customization
- ✏️ Edit gradients & card styles in the embedded `<style>` blocks or link your own `theme.css`.
- 🔧 Add new widgets in `resources/views/layouts/dva/dashboard/widgets/`.
- 🎨 Update emoji/nav icons in `partials/navbar.blade.php`.

---

## 🚀 Roadmap
- [ ] Dark mode toggle 🌙
- [ ] Flight map widget with ACARS integration
- [ ] Pilot leaderboard & hub statistics
- [ ] Policy acknowledgement system (versioned, middleware-enabled)

---

## 📜 License
This theme is released under the **phpVMS license**.  
Attribution to phpVMS is required unless you have a commercial license.  
See [phpVMS Docs](https://docs.phpvms.net/#license) for details.

---

## 🤝 Contributing
Want to help improve the theme?  
- Fork this repo  
- Add your feature/fix  
- Submit a Pull Request 🚀  

---

## 🛡️ Credits
- Built for **GTN Virtual Airline / Georgia Transparency Network**
- Powered by **phpVMS 7.0.5**
- Styled with **Bootstrap 5** + **TailwindCSS**
- Emojis via [Twemoji](https://twemoji.twitter.com/)

---

## 🔗 Links 
- 📖 [phpVMS Documentation](https://docs.phpvms.net)  
