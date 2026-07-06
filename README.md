# Sean & Brittany — Wedding Website

One-page site. Scroll-scrubbed video hero, countdown, story gallery, details, travel, registry, RSVP, FAQ.

## Open it

Double-click `index.html`, or for the smoothest video scrubbing serve it locally:

```
cd website && python3 -m http.server 8000
```

then visit http://localhost:8000. Any static host (Netlify, Vercel, GitHub Pages) works — upload the whole `website` folder.

## The things to edit (top of the `<script>` in index.html)

| Constant | Currently | Set it to |
|---|---|---|
| `RSVP_EMAIL` | `sean@example.com` | Sean's real email. Confirmed RSVPs are emailed here **directly and automatically** via FormSubmit (free, formsubmit.co) — guests never leave the page. **One-time activation:** the very first RSVP triggers an activation email from FormSubmit to this address; click the link in it and every RSVP after that arrives normally (as a tidy table: party, each guest's answer, note). Tip: submit a test RSVP yourself right after launching to trigger and complete activation. If FormSubmit is ever unreachable, the site falls back to opening the guest's mail app pre-filled. |
| `FUND_URL` | empty | The honeymoon fund link — the Contribute button activates automatically once set |
| `WEDDING_DATE` | `2027-07-24T00:00:00-07:00` | Add the ceremony time once decided (countdown target) |
| `GUEST_LIST` | 4 sample parties | **The real guest list.** Guests search any name in their party to find their invitation and confirm per guest. Format: `{ party: "Display name", guests: ["Full Name", "Full Name"] }` — one entry per invitation/household. |

## Still marked "coming soon" on the page (per CONTEXT.md)

- Day-of schedule times · RSVP deadline · Travel/lodging details · Our Story blurb
- Gallery currently shows stills from the hero film; swap in engagement/travel photos in `assets/` and update the `<figure>` tags in the gallery
- Couple's headline one-liner (HTML comment placeholder in the Welcome section)

## Notes

- `assets/hero.mp4` is re-encoded with dense keyframes (every 8 frames) + faststart specifically for smooth scroll-scrubbing; if you ever swap the film, re-encode the same way: `ffmpeg -i in.mp4 -c:v libx264 -crf 20 -g 4 -an -movflags +faststart hero.mp4`. The poster frame is `assets/poster.jpg`.
- Password gate intentionally omitted for this version (can be added later).
- Respects `prefers-reduced-motion`: shows a static hero instead of the scrubbed film.
