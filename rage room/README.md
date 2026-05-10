# RAGEZONE — Setup Guide

## Files
- `index.html` — Landing page
- `waiver.html` — The gate / consent page
- `room.html` — The main room (public board + submit form)
- `exit.html` — Cooling off / exit experience

---

## 1. Set up Google Forms (to receive submissions)

1. Go to forms.google.com and create a new form
2. Add one question: "Your vent" — Long answer (paragraph)
3. Click the three-dot menu → "Get pre-filled link"
4. Fill in a dummy answer and click "Get link"
5. Copy the link — it will look like:
   `https://docs.google.com/forms/d/e/XXXXX/viewform?entry.123456789=dummy`
6. From this link, copy:
   - `XXXXX` → this is your FORM_ID
   - `123456789` → this is your ENTRY_ID

7. Open `room.html` and replace these two values:
   ```
   const formBase = 'https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse';
   ...
   '?entry.YOUR_ENTRY_ID=' + encoded
   ```

Submissions will appear in the linked Google Sheet automatically.

---

## 2. Deploy to GitHub Pages

1. Create a new GitHub repository (public or private)
2. Upload all 4 HTML files to the repo root
3. Go to Settings → Pages
4. Source: "Deploy from a branch" → main → / (root)
5. Your site will be live at: `https://yourusername.github.io/reponame`

---

## 3. Your moderation workflow

When someone submits a vent:
1. You get it in your Google Sheet (linked to the form)
2. Read it
3. Remove: real names, specific places, any identifying detail
4. If it fits — copy the anonymized text into `room.html` as a new `.vent-card` block
5. Commit and push to GitHub — the site updates automatically

To add a new approved vent to the board, add this inside `<div id="ventBoard">` in room.html:

```html
<div class="vent-card">
  <p class="vent-text">YOUR ANONYMIZED VENT TEXT HERE</p>
  <p class="vent-meta">Anonymous — released</p>
</div>
```

---

## 4. Crisis resource — keep updated

The waiver page links to:
https://www.iasp.info/resources/Crisis_Centres/

This is the International Association for Suicide Prevention's directory of crisis centers worldwide. Check it remains accurate periodically.
