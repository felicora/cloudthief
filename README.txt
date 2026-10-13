CLOUD THIEF - upgraded build
============================

PLAY
  index.html                      open it in a browser (keep the assets/ folder next to it)
  cloud-thief-standalone.html     same game, every image + font embedded (just double-click)

CONTROLS
  A / D or Left / Right   move          Z or Shift   vacuum (face the cloud, hold)
  Space / W / Up          jump (again in the air = double jump)
  Esc                     pause
  Touch controls appear automatically on touch devices (Settings > Touch controls to force On/Off).

ASSETS (assets/)
  original-*.jpeg   your supplied artwork, untouched and referenced by its real file name:
                      A6C79EE1  title (masked hero)         6F43E075  Candy Cloud Kingdom
                      69C0CDDD  Enchanted Cloud Forest      7AFF2DF8  Sunset Sky City
                      7E851D6A  celebration art (final)     AFC41195  night city (final-screen fallback)
                    NOTE: several of your files are really WebP/PNG data with a .jpeg extension.
                    Browsers read them fine; rename them if you host them somewhere strict.
  sprites/*.webp    transparent sprites cut from your sheets:
                      player_*   8 hero poses (ground ellipse, labels and the baked suction blast removed;
                                 magenta chroma fringe cleaned). player_slide is kept but never triggered
                                 because the game has no slide mechanic.
                      drone_*    5 police drones   cloud_*  collectible/UI clouds   platcloud_*  cloud steps
                      ui_*       hearts, cloud icon, pause button
  fonts/*.woff      Poppins Bold/Medium subset (SIL OFL) so the UI looks identical offline

  Source sheets not used as-is: unmasked title art (non-canonical hero), effects sheet and power-up sheet
  (effects are generated in code), UI-kit panels/banners (their text is baked in, so the panels are rebuilt in CSS).

CODE MAP (one script inside index.html)
  ASSETS            file manifest (add "extraction": "assets/your-airship.png" to replace the built-in airship)
  LEVEL_DATA        platforms / clouds / drones / extraction in 1920x1280 painted-world coordinates
  Game.step()       fixed 60 Hz simulation (original movement values, unchanged)
  Render.frame()    interpolated rendering   |   UI.setScreen()   the only place a screen changes
  CFG               tuning: VISUAL_H (hero size), VAC_*, MIN_CHAR_PX ...
  Debug             add ?debug=1 to the URL, then press ` (backtick) to show collision bounds.
