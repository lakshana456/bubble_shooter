# Bubble Bloom

A vibrant, indie-styled bubble shooter. Aim, fire colored bubbles into a hex grid, and pop clusters
of 3 or more matching colors — clear the whole board before the bubbles creep down and overrun
the shooter.

## Features

- Classic hex-grid bubble shooter mechanics: aim with mouse or touch, fire, and bubbles snap into
  the nearest valid hex slot on collision
- Match-3+ detection via flood-fill on the hex grid, with cascading "floating bubble" drops —
  clusters no longer connected to the ceiling fall away for bonus points, just like the genre classic
- Fair, dynamic bubble colors: the next bubble is always chosen from colors currently present on
  the board, so the game never hands you an unwinnable dead color
- Juicy feedback: particle bursts on every pop, floating combo-score text, glossy gradient bubbles
  with soft highlight shading
- Indie visual identity: hand-picked vibrant palette, playful rounded "Baloo 2" display font,
  softly drifting background color blobs, wobble-tilted UI text
- Persistent best score via `localStorage`
- Full touch support for mobile play, not just mouse

## Features breakdown for your portfolio write-up

- **Hex grid math**: offset-coordinate hex grid with alternating row lengths, custom neighbor
  calculation for both "shifted" and "unshifted" row parity
- **Collision + snapping**: moving bubble checks distance against every grid bubble each frame;
  on collision, it snaps to whichever empty neighboring hex cell is pixel-closest to the impact point
- **Flood-fill matching**: BFS/DFS over hex neighbors to find same-color connected groups
- **Support-check for floating bubbles**: BFS from the ceiling row (row 0) each time bubbles are
  removed; anything unreachable from the ceiling is disconnected and falls
- **Difficulty curve**: since the grid only grows downward when a shot doesn't land near a match,
  sustained bad aim naturally increases the challenge until the bubbles reach the shooter — no
  extra timer or forced row-push logic needed

## Run it

Open `index.html` in any browser. Click "Start Game," move your mouse (or drag on touch) to aim,
and click/tap to shoot.

## Possible extensions

- Add power-up bubbles (bomb bubble that clears a radius, rainbow bubble that matches any color)
- Add a timed "sudden death" mode where a new row is periodically pushed down
- Add sound effects and a background music loop for extra atmosphere
- Add level progression with increasing color count and grid density
