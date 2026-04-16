# Pastel Whimsy — AO3 Site Skin

A soft, pastel-themed site skin for [Archive of Our Own](https://archiveofourown.org), built on a structured base-theme architecture with a full CSS variable system. Includes a companion mobile add-on and Zerafina icon replacements.

**Author:** intothisshadow  
**Version:** 2.1.0  
**AO3 instructions:** https://archiveofourown.org/works/79008746  
**GitHub:** https://github.com/intothisshadow/AO3-SiteSkin_PastelWhimsy  
**Website:** https://www.so-obsessed.com

## Screenshots

<details>
<summary>Desktop</summary>
<p align="center">
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_desktop1.jpg" width="48%" alt="Front page 1" />
  &nbsp;
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_desktop2.jpg" width="48%" alt="Front page 2" />
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_desktop3.jpg" width="48%" alt="Recent" />
  &nbsp;
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_desktop4.jpg" width="48%" alt="Search" />
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_desktop5.jpg" width="48%" alt="User's Works" />
  &nbsp;
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_desktop6.jpg" width="48%" alt="Work Page" />
</p>



</details>

<details>
<summary>Mobile</summary>
<p align="center">
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_mobile1.jpg" width="30%" alt="Front page" />
  &nbsp;
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_mobile2.jpg" width="30%" alt="User's Work Page" />
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/head/main/screenshots/screenshot_mobile3.jpg" width="30%" alt="Recent" />
  &nbsp;
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_mobile4.jpg" width="30%" alt="Front Page 2" />
</p>


<p align="center">
  <img src="https://raw.githubusercontent.com/intothisshadow/AO3-SiteSkin_PastelWhimsy/refs/heads/main/screenshots/screenshot_mobile5.jpg" width="30%" alt="Work page" />
</p>


</details>

---

## File Structure

```
style_desktop.css  Desktop stylesheet
style_mobile.css   Mobile add-on (requires style_desktop.css as parent skin)
stylus_fonts.css   Optional: loads custom fonts via the Stylus browser extension
CHANGELOG.md       Version history
README.md          This file
```

---

## How to Install

### Fonts via Stylus (recommended)

AO3's skin system cannot load external fonts directly. For the best experience, load the fonts separately using [Stylus](https://add0n.com/stylus.html), a free browser extension.

1. Install Stylus for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) or [Chrome](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne)
2. Click the Stylus icon → **Manage** → **Write new style**
3. Paste the contents of `stylus_fonts.css` into the code editor
4. Under **Applies to**, select **URLs on the domain** and enter `archiveofourown.org`
5. Name it (e.g. `Pastel Whimsy Fonts`) and save

Without this step the skin falls back to Palatino/Georgia for headings and body text, which still looks good — the fonts just won't be exactly as designed.

### Desktop skin (required)

1. Go to **Hi, user! → My Dashboard → Create Site Skin**
2. Paste the contents of `style_desktop.css` into the CSS field
3. Set **Media** to `all`
4. Save — do **not** activate it directly if you are also using the mobile add-on

### Mobile add-on (recommended)

1. Go to **Hi, user! → My Dashboard → Skins → Create Site Skin**
2. Paste the contents of `style_mobile.css` into the CSS field
3. Set **Media** to all three of:
   - `handheld`
   - `only screen and (max-width: 42em)`
   - `only screen and (max-width: 62em)`
4. Under **Parent Skin**, select the desktop skin you created above
5. Save and **activate this skin** — AO3 will automatically apply the parent skin alongside it. You only ever activate the child.

### Desktop only (no mobile add-on)

If you don't want the mobile add-on, activate the desktop skin directly instead.

### Icon replacements

The Zerafina icon replacement set is built into `style_desktop.css` as Section 15 — no separate skin needed. The colours have been adapted to match the Pastel Whimsy palette. Based on [ZerafinaCSS's Replace the AO3 Icons 2.0](https://github.com/ZerafinaCSS/Replace-the-AO3-Icons-2.0).

To remove the icon replacements, delete Section 15 from `style_desktop.css`.

---

## Customising the Palette

All colours are defined as CSS variables in the `:root` block at the top of `style.css` (Section 0). To create a new colour scheme, **only edit that block** — all 341 variable usages throughout the file will update automatically.

The variables are grouped into three sections:

- **Backgrounds & borders** — page bg, card levels, accent shades, primary purple tones, alpha variants
- **Accent colours** — hot pink, soft pink, purple, periwinkle blue, shadows, icon glow
- **Extended palette** — cool mint tones, lavender, muted/deep purples, danger red

---

## Stylesheet Structure

The desktop stylesheet is divided into 15 sections:

| # | Section |
|---|---------|
| 0 | Root variables |
| 1 | Global / body |
| 2 | Typography |
| 3 | Links |
| 4 | Header & navigation |
| 5 | Sidebar & dashboard |
| 6 | Buttons & actions |
| 7 | Forms & inputs |
| 8 | Tag system |
| 9 | Work blurb cards |
| 10 | Work page |
| 11 | Notices & state indicators |
| 12 | Page-specific |
| 13 | Accessibility & utility |
| 14 | Footer |
| 15 | Replace the AO3 icons (Zerafina) |

Each section has labelled sub-sections (e.g. `/* 4c. Dropdown menus */`) matching the table of contents at the top of the file.

The mobile stylesheet is divided into three `@media` blocks (≤62em, ≤42em, ≤30em), each with internal section comments grouping rules by type.

---

## Fonts

Three custom fonts are used. Because AO3 site skins cannot load external fonts, use the included `stylus_fonts.css` with the Stylus browser extension (see install instructions above). Without it the skin falls back to Palatino/Georgia and monospace system fonts, which still looks reasonable.

- **Lora** (body text) — https://fonts.google.com/specimen/Lora
- **Playfair Display** (headings) — https://fonts.google.com/specimen/Playfair+Display
- **JetBrains Mono** (code/pre) — https://fonts.google.com/specimen/JetBrains+Mono

---

## Credits

- Base theme architecture by intothisshadow ([Moonlit Wisteria](https://github.com/intothisshadow/AO3-SiteSkin_MoonlitWisteria))
- Icon replacements based on [ZerafinaCSS Replace the AO3 Icons 2.0](https://github.com/ZerafinaCSS/Replace-the-AO3-Icons-2.0), included in Section 15 of the desktop stylesheet

---

## Version

Current: **V2.1.0** — see [CHANGELOG.md](CHANGELOG.md) for full history.

The changelog documents significant changes only — new features, architectural decisions, and notable bug fixes. Individual CSS tweaks, rule refinements, and minor mobile adjustments are not logged.
