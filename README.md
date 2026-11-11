# McGill Athletes in Business (ABS) website

The club website: a single static page with no build step.

- `index.html` holds the whole page: content, styles and a small script for the menu, scroll fade-ins and the placement filters.
- `assets/` holds images. Put real ABS photos here and point the `background-image` URLs in `index.html` at them. The current photos are stock images from Unsplash.

## Updating content

Each section in `index.html` starts with a comment (`<!-- EVENTS -->`, `<!-- TEAM -->`, and so on). Edit the text there.

- **New event:** copy one `<article class="card">` block in the Events section.
- **Company strip:** the scrolling list near the bottom (`<!-- COMPANIES -->`). Each company appears twice, once plain and once with `aria-hidden="true"`, so the loop is seamless. Add or remove a name in both places.
- **Team:** edit `team.js`. Each person has a name, role, portfolio, photo, and optional `email` and `linkedin`. Headshots go in `assets/team/` as 480×480 squares. People without a photo show red initials.

## Hosting

The site can be hosted for free with GitHub Pages. In the repo, go to Settings → Pages, then under "Build and deployment" choose "Deploy from a branch", with branch `main` and folder `/ (root)`.

## Managed from the exec portal (no code changes needed)

- **Team:** Team tab → Add a person / Edit. Set name, role, portfolio (type a new name to create a new portfolio), order, and **upload a headshot** right there. The headcounts on the homepage and the portfolio filters update automatically. To remove someone, open their card and choose Remove from site.
- **Calendar:** Calendar tab. Add the event name, date, optional start/end time (blank = all day), type, location, description and an RSVP link. A preview shows how it'll look. Events appear on the homepage calendar straight away; past events drop off the "Upcoming" list automatically. Visitors can add any event to Google Calendar.
- **Testimonials:** Testimonials tab. Add a quote, the person's name and a short detail line. Use ↑ to reorder. The homepage section only appears once there's at least one.
- **Club email:** absmcgilloperations@gmail.com is in the Join section and footer of `index.html`.

## Exec portal (edit.html)

Execs sign in with Google at `/edit.html` (also linked as "Exec login" in the footer) and can edit their own contact email, LinkedIn and bio. Changes appear on the Team section straight away.

- **Admins** can edit anyone's card, add or remove people, and manage who can sign in under "Who can sign in".
- **To add a new exec:** add them under Team ("Add a person"), then give their Google email access and link it to their card.
- **Headshots** are still files in `assets/team/`. Upload the photo to the repo, then set the file name on the person's card.
- **Replacing a headshot:** save it under a new file name (e.g. `emma-sutton-2.jpg`) and update the Photo file on their card. Reusing the old name can leave visitors seeing the old photo, because browsers keep images for a while. Photos must be real JPEGs: iPhone HEIC files named `.jpg` won't show in Chrome.
- If the database can't be reached, the Team section falls back to `team.js`. Keep it roughly in sync at handover.

## Members area (members.html)

Linked as "Members" in the main menu. Holds the **Alumni Directory** and **Resource Database**, visible only to approved accounts.

- **Getting in:** people create an account with Google or with an email and password, then wait. An admin approves or declines them in the exec portal under **Member requests**. Exec admins can always get in.
- **Alumni Directory:** anyone who signed up as an alum gets a "My directory profile" tab to add their grad year, sport, company, role, industry, city, LinkedIn, contact email, a short bio, and whether they're open to mentoring. They can remove their listing at any time; admins can remove any listing in the Firebase console.
- **Resource Database:** admins add links (Google Drive, Notion, websites) with a title, category and description in the exec portal under **Resources**. Check that each link's sharing settings let anyone with the link view it.

## Accounts & access

| What | Where | Owner |
|---|---|---|
| Website code and hosting | GitHub: `absmcgilloperations-lab/abswebsite` (GitHub Pages) | ABS operations GitHub account |
| Sign-in and team database | Firebase project `abs-website-2f2ea` (console.firebase.google.com) | Henry Jagger's personal Google account (2026–27). **Add the ABS Google account as an Owner** under Project settings → Users and permissions before handover. |
| Database security rules | `firestore.rules` in this repo, published in Firebase → Firestore → Rules | Paste and publish there after any change |

Keep at least two owners on each account, and store passwords and 2FA recovery codes somewhere the club controls.
