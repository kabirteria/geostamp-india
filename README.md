# GeoStamp India

Turns iPhone photos into geo-tagged photos for MCA / ROC filings (MGT-7, MGT-7A, INC-22A).

- `index.html` – the standalone app. Host it on any https site (GitHub Pages, Netlify drop) and open it on your phone or computer.
- `app.html` – the same app, in the form used for the claude.ai artifact.

## What it does

1. Reads GPS latitude/longitude, capture date/time and time zone from the photo's own EXIF (HEIC or JPEG).
2. Refuses photos without GPS or capture time. Coordinates and time can't be typed in or edited.
3. Prints a stamp on the photo: map tile with a pin, area and address, lat/long, date and time with GMT offset, Plus Code, GPS accuracy, camera.
   - The address comes from OpenStreetMap, or from the "Office address to print" field (e.g. the registered office address as filed with MCA).
   - A typed address is printed only if it matches the photo's GPS: same state and within 5 km. Otherwise the photo keeps the OpenStreetMap address and shows why.
4. Saves a JPEG (under 2 MB by default) that keeps the original GPS, time and camera EXIF, and marks the file as processed by GeoStamp India.

## Notes

- The address and map need an https page. Opened as a local `file://` page or inside claude.ai, the stamp carries coordinates, time and Plus Code only.
- Photos never leave the device. Only the coordinates go to OpenStreetMap.
- If iOS strips the location when you pick from the Photo Library: in Photos tap Share › Options, turn on Location and All Photos Data, Save to Files, then pick the file with Browse.
