# How To Add More Songs To The Player

Cards are now generated automatically from the JavaScript `songs` array. You only add songs in ONE place (the array) and the UI updates itself. 🎉

Follow these steps.

---
## 1. Add / Prepare Your Files
Place your new audio file (MP3, etc.) in the `music/` folder, e.g.:
```
music/my-new-track.mp3
```
Place the cover image (JPG / PNG) in the `images/` folder, e.g.:
```
images/my-new-track.jpg
```
(You can reuse an existing image if you don’t have a custom one.)

---
## 2. Extend The `songs` Array (Only Step That Matters)
Open `index.html` and find the existing array:
```js
const songs = [
  { title: "Aankh", artist: "Sunidhi Chauhan, Rusha & Blizza", cover: "images/aankh.jpg", src: "music/AANKH  Official Music Video  Sunidhi Chauhan, Rusha & Blizza  Feat. Sanya Malhotra.mp3" },
  // ... more songs ...
];
```
Add a new object at the END (order matters):
```js
{ title: "My New Track", artist: "Artist Name", cover: "images/my-new-track.jpg", src: "music/my-new-track.mp3" }
```
Make sure to include a comma after the previous entry and NOT after the last one if it becomes the new final element.

---
## 3. No Manual HTML Needed Anymore
Song cards are built dynamically inside `renderSongCards()`. Just update the array—cards, like buttons, and click handlers appear automatically.

---
## 4. Reorder Songs
Just reorder objects inside the `songs` array. The rendered order & indexes update automatically.

---
## 5. Test It
1. Reload the page in the browser.
2. Click your new card → it should highlight and play.
3. Try the Like button (card + player + sidebar list should sync).
4. Use Next/Previous buttons to ensure the new song is in sequence.

If it doesn’t play:
- Open the browser console (F12) and look for a 404 (file not found) error → check paths.
- Ensure the filename & extension exactly match (case-sensitive on some systems).

---
## 6. (Optional) Persist Likes / Last Played
Currently, likes reset on refresh. To persist:
- Store `likedSongs` in `localStorage` after each toggle.
- On load, read it back and apply state.
(Ask if you want this implemented.)

---
## 7. Quick Reference Checklist
- [ ] Audio file in `music/`
- [ ] Cover image in `images/`
- [ ] Entry added to `songs` array
- [ ] Page reloaded & tested

---
## 8. Example Full Addition
Add this to the array:
```js
{ title: "Illusion", artist: "Nova K", cover: "images/illusion.jpg", src: "music/illusion.mp3" }
```
Reload → the new card appears automatically.

---
## 9. Edge Cases
- Missing file → console shows `Could not load audio file` or 404
- Wrong path / spelling → silent failure or auto-skip
- Very large file → may delay initial play event
- Spaces in filenames → safer to rename to simple forms (e.g. `aankh.mp3`)

You can also rename long files and update only the `src` in the array (and optional initial `<audio>` tag).

---
## 10. Further Automation Ideas
- Move `songs` array to `songs.js` and import
- Load songs from a JSON file via fetch
- Add drag-to-reorder & persist order to `localStorage`
- Add shuffle / repeat controls

---
Happy building! Let me know if you want persistence, auto-generation, or shuffle/repeat next.
