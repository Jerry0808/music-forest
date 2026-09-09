# Music Forest illustration assets

The track detail page uses a hybrid scene: a generated painted background, optional transparent character and foreground layers, HTML story copy, and lightweight CSS motion. Asset paths live in `ILLUSTRATION_ASSETS` inside `index.html`; the HTML template does not hard-code individual track paths.

## Folders

- `backgrounds/`: compressed WebP hero paintings.
- `characters/`: optional transparent character layers for future scenes.
- `foreground/`: transparent PNG foliage, reeds, aquatic plants, bubbles, and snow frames.
- `textures/`: optional raster paper textures. The current paper grain remains a very light CSS texture.

## Coverage

- Home hero: 1 WebP illustration.
- Track heroes: 40 / 40 WebP illustrations referenced through `ILLUSTRATION_ASSETS`.
- Supporting foreground layers: forest foliage, lake reeds and flowers, aquatic plants and bubbles, and winter snow.
- Total hero payload: about 13.3 MB; each hero is compressed separately and the largest file is below 500 KB.

The approved Vivaldi Spring, Saint-Saëns Swan, Saint-Saëns Aquarium, Rimsky-Korsakov Bumblebee, Beethoven Moonlight and Beethoven Für Elise images were preserved. The remaining track worlds were generated as original watercolor/gouache pages and compressed to WebP for reliable offline loading.

The former data-driven SVG scene remains only as a load-error fallback. Under normal operation all 40 track detail pages use raster picture-book illustrations.

## Generation direction

Built-in ImageGen was used with one prompt per musical world. The shared direction specified premium European children's picture-book watercolor and gouache, soft pastel pigments, subtle paper grain, organic brushwork, atmospheric depth, layered foreground/midground/background, natural HTML-safe visual space, and strict avoidance of flat vector, geometric SVG, CGI, game-mascot, text, logo, or watermark treatments.
