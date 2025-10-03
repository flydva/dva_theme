# DVA Theme v3.0.1

A modern, glassy Bootstrap 5 theme for phpVMS v7 with dashboard‑style components, clean tables, and Blade utilities.  
**v3.0.1 is the ONLY version compatible with DisposableBasic (DBasic) and DisposableSpecial (DSpecial).**

> ⚠️ **Important Compatibility Notice**
>
> - **This theme version (v3.0.1) is the only release designed to work with both DBasic and DSpecial.**
> - The package **ships Blade overrides for DBasic and DSpecial** to visually match the theme.
> - You must also **update your DisposableBasic and DisposableSpecial modules to their latest stable versions** so the UI looks consistent and routes/components resolve correctly.

---

## ✨ What’s inside

- Refreshed “dashboard look” (glass cards, compact paddings, softer shadows)
- Themed tables for Fleet, PIREPs, Tours, Hubs, NOTAMs, Market, etc.
- Utility components (chips, header bars, stat tiles) used across pages
- **Bundled Blade overrides for DBasic & DSpecial** to match the theme
- Safer helpers/guards for optional modules and money formatting
- Dark‑blue accented variant for data tables (optional class `.table-dva`)

---

## ✅ Requirements

- **phpVMS v7** (latest recommended)
- **PHP** version per phpVMS requirements
- **DisposableBasic & DisposableSpecial (latest versions)** if you use those modules
- Composer/npm only if your installation flow needs it (theme itself is Blade/CSS only)

---

## 📦 Installation (fresh install)

1. **Backup your site** (files + database).
2. **Upload** the theme files from `dva-theme-v3.0.1.zip` into your project:
   - Usually under: `resources/views/layouts/dva/` and related `resources/views` assets used by your current setup.
3. In **Admin → Settings**, set your **Active Theme** to **DVA** (or update your theme setting if your app uses a theme switcher).
4. **Publish / copy the bundled Blade overrides** (already placed inside the theme package) for the modules you use:
   - `resources/views/vendor/DisposableBasic/**`
   - `resources/views/vendor/DisposableSpecial/**`
   - These will be picked up automatically by Laravel if the modules are installed.
5. **Update DBasic and DSpecial** modules to their **latest stable** versions (required for compatibility & matching look).
6. **Clear caches** (recommended):
   ```bash
   php artisan view:clear
   php artisan cache:clear
   php artisan route:clear
   php artisan config:clear
   ```

> 💡 If your installation keeps Blade overrides for modules **inside each module’s `/Resources/views`** instead of `resources/views/vendor/...`, copy the provided override folders accordingly and merge carefully with any local customizations.

---

## 🔁 Upgrading from v2.x → v3.0.1

1. **Backup first** (files + DB).
2. Remove or archive your previous DVA theme folder(s) to avoid stale files.
3. Extract **v3.0.1** and copy into your `resources/views/...` locations.
4. **Replace/merge the included DBasic/DSpecial Blade overrides** with your installation’s override path:
   - Prefer `resources/views/vendor/DisposableBasic/**` and `resources/views/vendor/DisposableSpecial/**`.
5. **Update DBasic & DSpecial** modules to their **latest stable** versions.
6. Clear caches:
   ```bash
   php artisan view:clear
   php artisan cache:clear
   php artisan route:clear
   php artisan config:clear
   ```

---

## 🧩 Using the bundled DBasic & DSpecial overrides

This theme **includes Blade files that restyle DBasic and DSpecial** UIs so they look native in DVA v3.0.1.

- Copy/confirm they exist under:
  - `resources/views/vendor/DisposableBasic/**`
  - `resources/views/vendor/DisposableSpecial/**`
- If you already have custom overrides, **diff/merge** to keep your changes.
- After updating, **clear caches** to ensure new views are used.

> If a route like `route('DSpecial.notams')` is missing, the module isn’t active. Guard those links in your navs/buttons with `@if(function_exists('check_module') && check_module('DisposableSpecial')) … @endif`.

---

## 🛠️ Theme Helpers & Safe Guards

Use defensive checks so pages work with or without DBasic/DSpecial installed:

```blade
{{-- Optional helpers include --}}
@includeIf('theme_helpers')

@php
  $DBasic   = $DBasic   ?? (function_exists('check_module') ? check_module('DisposableBasic')  : false);
  $DSpecial = $DSpecial ?? (function_exists('check_module') ? check_module('DisposableSpecial') : false);

  // Units fallback
  $units = $units ?? (
    function_exists('DT_GetUnits')
      ? DT_GetUnits()
      : ['currency' => 'USD', 'fuel' => 'kg', 'distance' => 'nm', 'weight' => 'kg']
  );
@endphp

{{-- Example guarded link --}}
@if($DSpecial)
  <a href="{{ route('DSpecial.notams') }}">NOTAMs</a>
@endif
```

**Money/Balance safety** (avoid “object could not be converted to float” errors):

```blade
@php($balance = optional($user->journal)->balance)
@if(!is_null($balance))
  <span class="text-success">{{ $balance }}</span>
@else
  <span class="text-muted">No Earnings Yet</span>
@endif
```

---

## 🎨 Optional Styles

- Tables: add `.table-dva` to get the dark‑blue accented look used by the theme.
- Chips / header bars / stat tiles are included in the theme partials; reuse them across pages for consistency.

---

## 🧪 Post‑Install Checklist

- ✅ Theme is selected in **Admin → Settings**  
- ✅ DBasic/DSpecial updated to latest stable (if you use them)  
- ✅ Bundled Blade overrides are in place under `resources/views/vendor/...`  
- ✅ Caches cleared  
- ✅ Nav items for DBasic/DSpecial are wrapped in `@if($DBasic)` / `@if($DSpecial)`

---

## ❓ Troubleshooting

- **Undefined variable `$DSpecial`**  
  Ensure you define `$DSpecial` via the guard snippet above before you reference it in views.

- **Route `[DSpecial.something]` not defined**  
  The module isn’t enabled/installed. Wrap links/components in `@if($DSpecial)`.

- **Money conversion error**  
  Print the money object directly or via its formatter method (avoid `number_format` on money objects). See the **Money/Balance safety** example above.

- **Theme not applying**  
  Confirm the active theme setting and that Blade overrides live under `resources/views/vendor/DisposableBasic|DisposableSpecial` (or your installation’s expected override path). Clear caches.

---

## 📄 License

This theme is released under the license bundled with the package. By installing, you agree to that license.

---

## 🙌 Credits

- DVA Theme by Russ P.
- phpVMS v7
- DisposableBasic & DisposableSpecial modules (Faith Koz)
