# homeserverwebsite

Landingpage für den Homeserver der **Wird Geil WG**.
Statische Seite – kein Build nötig.

## Lokal ansehen

```sh
python3 -m http.server 8000
# -> http://localhost:8000
```

## Struktur

| Datei                    | Inhalt                                                                     |
|--------------------------|---------------------------------------------------------------------------|
| `index.html`             | SVG-Duoton-Filter, Marquee, Hero-Medium, 3-Spalten-Links, Footer           |
| `styles.css`             | Design (nur `#000` + `#EEE6C0`), Pixel-/Duoton-Look, Marquee, Responsive   |
| `assets/neanderthal.svg` | Platzhalter – wird durch das GIF/MP4 ersetzt                               |

Kein JS, kein Build.

## Neandertaler-GIF einsetzen

1. GIF (oder MP4) als `assets/neanderthal.gif` bzw. `assets/neanderthal.mp4` ablegen.
2. In `index.html` im `.hero__figure` die aktive Zeile auf die GIF-`<img>`-Zeile
   umstellen – oder bei MP4 den auskommentierten `<video>`-Block aktivieren.
3. Passt das Seitenverhältnis nicht, in `styles.css` bei `.hero__figure`
   `--hero-ar` setzen, z. B. `--hero-ar: 16 / 9;`.

Der Look (Graustufen → harte 2-Ton-Reduktion auf `#000`/`#EEE6C0` + Pixel-Raster)
kommt komplett aus CSS/SVG:
- **Farben:** `#duotone`-Filter in `index.html` (`feFuncR/G/B` = die zwei Zielfarben).
- **Pixelgröße:** in `styles.css` bei `.hero__media` das Paar `width/height: 12.5%`
  und `transform: scale(8)` – kleinerer Prozentwert + größerer Scale = grobere Pixel.

## Weiter anpassen

- **Links:** in `index.html` die `href`-Werte der `.cell`-Elemente auf die echten
  URLs setzen (aktuell `http://jellyfin.local` usw.). Weitere Dienste = weiterer
  `<a class="cell">`-Block; `grid-template-columns` in `styles.css` ggf. anpassen.
- **Marquee-Text:** beide `.marquee__item`-Spans in `index.html` mit demselben Text
  füllen (später Buch-Auszug). Tempo über `animation`-Dauer in `styles.css`.
