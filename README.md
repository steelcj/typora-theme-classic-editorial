# Typora Theme, Classic Editorial

A Typora theme by Christopher Steel / UniversalCake.

## Installation

Typora loads every `.css` file it finds directly inside `~/.config/Typora/themes/`. Assets each theme depends on (fonts, sub-stylesheets) live in a subfolder with the same name as the `.css` file. The install procedure below copies only those two things and leaves everything else in the repository, including this file, untouched.

### Linux and macOS

```bash
cd /tmp
git clone https://github.com/steelcj/typora-theme-classic-editorial.git
cp typora-theme-classic-editorial/classic-editorial.css ~/.config/Typora/themes/
cp -R typora-theme-classic-editorial/classic-editorial ~/.config/Typora/themes/
rm -rf /tmp/typora-theme-classic-editorial
```

Restart Typora, then open **Themes** in the menu bar and select **Classic Editorial**.

### Windows

Replace `~/.config/Typora/themes/` with `%APPDATA%\Typora\themes\` in the commands above, or open that folder directly from Typora via **File → Preferences → Appearance → Open Theme Folder** and copy the two items there manually.

## Removal

Delete the two items that were installed:

```bash
rm ~/.config/Typora/themes/classic-editorial.css
rm -rf ~/.config/Typora/themes/classic-editorial
```

Restart Typora. The theme will no longer appear in the Themes menu.

## Updating

Pull the latest version and repeat the copy step. The `cp` commands overwrite existing files in place so no manual cleanup is needed first.

```bash
cd /tmp
git clone https://github.com/steelcj/typora-theme-classic-editorial.git
cp typora-theme-classic-editorial/classic-editorial.css ~/.config/Typora/themes/
cp -R typora-theme-classic-editorial/classic-editorial ~/.config/Typora/themes/
rm -rf /tmp/typora-theme-classic-editorial
```

## Tweaking the theme

Typora supports a personal override file that survives theme updates. Create it once and it will always be loaded on top of whatever theme is active.

### The override file

Create `~/.config/Typora/themes/base.user.css` if it does not already exist. Anything you put there overrides the theme without touching the theme's own files.

```bash
touch ~/.config/Typora/themes/base.user.css
```

Open it in any text editor and add your overrides. Typora picks up changes the next time it starts.

### Common tweaks

**Change the body font size**

```css
#write p {
  font-size: 17px;
}
```

**Change the writing area width**

```css
#write {
  max-width: 780px;
}
```

**Change the body typeface**

```css
#write {
  font-family: "Georgia", serif;
}
```

**Change the heading typeface**

```css
#write h1,
#write h2 {
  font-family: "Georgia", serif;
}
```

**Change the background colour**

```css
html,
body {
  background-color: #fafafa;
}
```

**Change heading colours individually**

```css
#write h1 { color: #111; }
#write h2 { color: #222; }
#write h3 { color: #444; }
```

**Change the blockquote style**

```css
#write blockquote,
#write blockquote p {
  font-size: 20px;
  border-left: 4px solid #aaa;
  color: #555;
}
```

**Change inline code appearance**

```css
#write code {
  background-color: #f4f4f4;
  color: #333;
  border-radius: 3px;
  padding: 0 4px;
}
```

### Inspecting elements

To find the exact CSS selector for anything you want to change, enable Typora's built-in DevTools:

- **macOS,** Help → Enable Debug Menu, then right-click any element → Inspect Element
- **Windows / Linux,** View → Toggle DevTools, or press `F12`

The DevTools panel works the same as a browser. Hover over elements to see their selectors, then add matching rules to `base.user.css`.

### Changing CSS variables

Classic Editorial uses CSS custom properties at `:root` level for its core design tokens. You can override them in `base.user.css` without touching individual selectors:

```css
:root {
  --page-bg: #f3f3f3;
  --card-bg: #ffffff;
  --ink: #222;
}
```

Refer to `classic-editorial.css` to see which variables are defined.

## File structure

```
typora-theme-classic-editorial/       ← repository root
├── classic-editorial.css             ← theme entry point (copy to themes/)
├── classic-editorial/                ← theme assets (copy to themes/)
│   ├── codeblock.css
│   ├── sourcemode.css
│   ├── mermaid.css
│   ├── credit.html
│   └── fonts/                        ← bundled woff2 files
└── README.md                          ← this file (stays in the repo)
```

Only `classic-editorial.css` and the `classic-editorial/` folder are installed. `README.md` is repository documentation and is never copied to the themes directory.

## Changelog

| Version | Status | Notes |
| ------- | ------ | ----- |
| 0.0.8 | Draft | Removed explicit font-weight from H2 to match mockup default heading weight |
| 0.0.7 | Draft | Reverted H1 to 48px canonical mockup value |
| 0.0.6 | Draft | H1 size calibration |
| 0.0.5 | Draft | Scoped all heading and body rules to #write with !important to pin against Typora scaling, reset html font-size to 100% |
| 0.0.4 | Draft | Scoped heading rules to #write, reset html font-size |
| 0.0.3 | Draft | Fixed blockquote p override for Typora inner paragraph wrapping |
| 0.0.2 | Draft | Font bundling, exact mockup values throughout |
| 0.0.1 | Draft | Initial build |

## License

This theme, *Typora Theme, Classic Editorial*, by **Christopher Steel**, is licensed under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

![CC BY 4.0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by.svg)
