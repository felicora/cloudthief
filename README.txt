CLOUD THIEF — 7 missions
========================
Open index.html (keep the assets/ folder next to it).  cloud-thief-standalone.html is the same game with the
artwork, opening animation and start-screen music embedded in one file; both need no server and no internet.

START SCREEN
  * Your animation (assets/video/opening.mp4, with opening.webm as a fallback for browsers without H.264) plays muted
    on a loop, scaled to fit the whole window (never cropped; blurred bars fill any spare space).
  * The real, keyboard-accessible Play button sits exactly on the painted "[ Play Now ]" button; How to Play,
    Settings and Continue are normal buttons on top of the video.
  * Music on the start screen: Kevin MacLeod's "Pixelland" (see MUSIC below).
  * The animation file has a "CapCut Ai" mark burned into its top-left corner, so a friendly Sky Patrol drone hovers
    there to cover it (assets/video/cover_drone.webp, placed relative to the video frame, so it stays on the mark at any
    window size; How to Play sits next to the gear while the video is showing). Re-export the video without the mark
    and delete "cover" from MEDIA in index.html to drop the drone.
  * To swap the video: replace the files in assets/video/ (keep the 16:9 shape). If the painted Play button is
    elsewhere in a new video, edit OPENING.playRect in index.html (fractions of the frame: cx, cy, w, h).
  * If a browser refuses to play the video (autoplay blocked, low-power mode, previews that block media or Blob URLs),
    the same animation is played by the game itself from assets/video/frames/ (a 10 fps picture sequence) instead of a
    still picture. A first tap or key press also restarts the real video.
  * How to Play lists all 7 missions (with a tick on the ones you have finished).

MUSIC (assets/audio/, one track per part of the game; sound effects are separate)
  Start screen + final screen ..... Pixelland (Kevin MacLeod) from the beginning
  1 The Sugar Skies ............... Sweet Cafe (Stream Cafe)
  2 Whispering Canopy ............. Pixelland, a different part: the breakdown / bright / closing section (2:47-3:54), looped
  3 Lantern City Heist ............ intro chinatown
  4 Volcanic Skylands ............. Creative Commons "Cinematic Chinese / Asia" track
  5 Orbital Hideaway .............. fortunehouse
  6 Thundercloud City ............. Eric Skiff - A Night Of Dizzy Spells
  7 Bubble Reef Kingdom ........... bgm3 (plays 8% faster during the collapse escape)
  The tracks cross-fade, loop, dip while paused / on game over, and follow the Music on/off setting. All were
  re-encoded to 80 kbps at one loudness. Credits are listed in How to Play. Pixelland and A Night Of Dizzy Spells are
  CC BY (attribution required); please check the licence/attribution terms of the other tracks before publishing.

MISSIONS (played in order, saved automatically)
  1 Sugar Skies · 2 Lantern Forest · 3 Sunset City        (unchanged)
  4 Volcanic Skylands · 5 Orbital Hideaway · 6 Thundercloud City · 7 Bubble Reef Kingdom

DIFFICULTY (hard tuning, all 7 missions)
  * EVERY cloud on the map must be collected before the exit opens (the counter shows clouds, not cloud sizes).
    In Mission 7 the sealed Cloud Core comes after that, then the escape.
  * Sky Patrol drones fly 20% faster and chase 30% longer; you are protected for 1.5 s after a hit (was 2 s);
    hazards cycle 10% faster (every warning keeps its length); crumbling / dissolving platforms give you less time.
  * To soften it, edit CFG.HARD (and HURT_FRAMES) near the top of index.html: setting droneSpeed, droneChase,
    hazardTempo and platformTimers to 1 gives the earlier, gentler timing (clouds are always all required).

RULES THAT ARE NEW IN 4-7
  * Hearts: 3. Touching a hazard costs 1 heart. Lava / falling off costs 1 heart and puts you back on the latest
    checkpoint (lantern post). Activating a NEW checkpoint restores 1 heart.
  * Game over -> TRY AGAIN restarts at the latest checkpoint with your collected clouds kept. RESTART MISSION
    (pause menu) resets only that mission.
  * The exit opens when the cloud quota is full AND every switch / generator / beacon (and the Core) is done.
  * Progress (unlocked mission, best time per mission) is saved in the browser; "Continue" appears on the first screen.

JUMP TO A MISSION (for testing)  add ?mission=6 (or 1-7) to the page address, e.g. index.html?mission=7
SAFETY NETS  if something ever fails during play, a "Something went wrong" panel appears with RETRY (instead of a silent
  freeze). On slow devices the game switches decorative effects (rain, wind streaks, floating motes) to a cheaper
  version automatically.

DEBUG  add ?debug=1 to the URL, press ` (backtick) to see collision boxes, zones and checkpoints.
