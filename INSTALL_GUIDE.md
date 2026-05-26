# 🌑 Obsidian Command Center — Install Guide

Follow these steps to correctly install and apply the Obsidian Command Center theme and dashboard.

---

## Pre-reqs

- [ ] Have HACS installed and enabled
- [ ] Have File Editor add-on installed and enabled

### 1️⃣ STEP 1: Install card-mod

1. Open **HACS** → **Frontend**
2. Click the **+ Explore & Download Repositories** button (bottom right)
3. Search for `card-mod`
4. Click **card-mod** in the results
5. Click the **Download** button at the bottom right
6. Wait for the download to complete and the button to say **Downloaded**

---

### 2️⃣ STEP 2: Add themes include to `configuration.yaml`

1. Open your **File Editor** add-on (or VS Code add-on).
2. Navigate to `/config/configuration.yaml`.
3. Find or add the `frontend:` block and add the `themes` line:

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

> [!IMPORTANT]
> If you already have a `frontend:` block, just add the `themes` line inside it. Do not duplicate the `frontend:` key.

---

### 2️⃣ STEP 2: Create the themes folder

1. In the **File Editor**, create a new folder named `themes` inside the `/config/` directory.
2. If you are using the File Editor add-on, click the folder icon in the top bar to create the folder.

---

### 3️⃣ STEP 3: Upload the theme files

1. Copy and upload all three theme files into your `/config/themes/` folder:
   - **Obsidian Command Center** (Dashboard theme): [themes/obsidian.yaml](themes/obsidian.yaml)
   - **Obsidian Core Dark** (Dark settings & helper theme): [themes/obsidian_core_dark.yaml](themes/obsidian_core_dark.yaml)
   - **Obsidian Portal** (Light-slate settings & helper theme): [themes/obsidian_portal.yaml](themes/obsidian_portal.yaml)
2. You should have three `.yaml` files in `/config/themes/`.

---

### 4️⃣ STEP 4: Restart Home Assistant

1. Go to **Settings** → **System**.
2. Click the **Restart** button (top right) → **Restart Home Assistant**.
3. Wait for the system to come back online (~60 seconds on a Raspberry Pi 4).

---

### 5️⃣ STEP 5: Apply the themes

To get the absolute best experience across both your dashboards and Home Assistant portal screens, we recommend setting a dedicated portal theme for your profile and the Obsidian Command Center theme specifically on your dashboards.

#### **Option A: Set the Core theme for your user profile**
*This styles all settings, helper configuration pages, developer tools, and main panels*

1. Click your **avatar** (bottom left corner).
2. Under **Theme**, select **Obsidian Core Dark** (for a fully dark interface with dark dropdowns) OR **Obsidian Portal** (for a clean light slate theme with dark blue text).
3. Click **Done**.

#### **Option B: Set the Dashboard theme specifically**
*This keeps the gorgeous neon accents, glassmorphic UI, and white text for your cards on your visual dashboards*

1. Open your specific dashboard.
2. Click the **Edit** (pencil) icon.
3. Click the `⋮` menu (top right) → **Edit dashboard** details.
4. Set the **Theme** dropdown to **Obsidian Command Center**.
5. Click **Save**.

---

### 6️⃣ STEP 6: Reload Lovelace resources

1. Go to **Settings** → **Dashboards**.
2. Click the `⋮` menu (top right) → **Reload resources**.
3. Perform a **hard-refresh** in your browser:
   - **Mac**: `Cmd` + `Shift` + `R`
   - **Windows/Linux**: `Ctrl` + `F5` or `Ctrl` + `Shift` + `R`

---

## 🛠️ Troubleshooting

### **Fonts not loading?**

- Your Home Assistant instance needs internet access to reach `fonts.googleapis.com`.
- Check the browser console (`F12`) for any font loading errors.
- *Alternative*: Download the fonts (Outfit & JetBrains Mono) locally and serve them via `/config/www/`.

### **Theme not appearing in the list?**

- Check your `configuration.yaml` for indentation errors (use spaces, never tabs).
- Go to **Developer Tools** → **YAML** → **Check configuration** to validate.
- Restart again after fixing any errors.

### **card-mod styles not applying?**

- Ensure `card-mod` is installed and enabled via HACS.
- Clear your browser cache and perform a hard-refresh.
- Check the browser console for any `card-mod` related errors.

---

## 📄 configuration.yaml Snippet

*You can copy and paste this directly into your config file:*

```yaml
frontend:
  themes: !include_dir_merge_named themes
```
