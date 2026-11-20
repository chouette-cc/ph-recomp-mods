# Phantom Hourglass Recomp — Community Mod Catalog

Official community index for the **Built-in Mod Browser** in *Phantom Hourglass Recomp* (PC & Android).

## For Players

You do not need to download anything from this repository manually!

- **PC**: Press `F1` / `Esc` → **Mods** → **Browse Online** → click **Install** (verified via SHA-256 and loaded immediately).
- **Android**: Open the launcher → **Mods** → **Browse Online…** → select a mod → **Install**.

Raw catalog URL (used by default):
```text
https://raw.githubusercontent.com/chouette-cc/ph-recomp-mods/main/catalog.json
```

## Available Mods

| Mod | Type | Version | Description |
|---|---|---|---|
| [Single Screen (Modern HUD)](https://github.com/chouette-cc/ph-recomp-single-screen) | `lua` (Sandboxed) | `1.0.0` | Play Phantom Hourglass on one screen with a sleek minimap PiP, automatic clean map crop, and customizable top-screen peek. |

## For Mod Authors — How to Submit a Mod

1. Package your mod as a `.phmod` (a standard `.zip` archive containing `mod.json` + `res/` / `overlay/` / `textures/` / `lib/`, without your personal `config.json`).
2. Publish it as a **GitHub Release** on your mod's repository.
3. Compute its SHA-256 checksum:
   - **Windows PowerShell**: `(Get-FileHash -Algorithm SHA256 your-mod.phmod).Hash.ToLower()`
   - **Linux / macOS**: `sha256sum your-mod.phmod`
4. Open a **Pull Request** adding or updating your entry in [`catalog.json`](catalog.json):

```json
{
  "id": "com.yourname.my-mod",
  "name": "My Mod",
  "version": "1.0.0",
  "kind": "lua",
  "author": "Your Name",
  "description": "Short summary shown in the in-game Mod Browser.",
  "download_url": "https://github.com/you/repo/releases/download/v1.0.0/my-mod.phmod",
  "sha256": "<64-char-lowercase-sha256>",
  "tags": ["hud"],
  "regions": ["AZEE", "AZEP"],
  "homepage": "https://github.com/you/repo"
}
```

### Review & Security Rules
- **No copyrighted Nintendo ROM data, assets, or binaries.**
- `download_url` must be an `https://` link pointing to a versioned release asset.
- `sha256` must match the exact published `.phmod` archive.
- `kind` must accurately declare `"asset"`, `"lua"`, or `"native"`. Native C++ mods require source availability for review and trigger an explicit user confirmation warning in the Mod Browser.
