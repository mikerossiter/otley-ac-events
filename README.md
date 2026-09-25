# Otley AC Juniors — race list page

This is a simple web page that shows the races coming up for our junior runners.
Parents open a link. They do not need an account, an app, or a password.

**The live page:** https://mikerossiter.github.io/otley-ac-events/

There are only three files here:

| File | What it is |
| --- | --- |
| `index.html` | The page itself. Set up once. You should never need to touch this. |
| `events.json` | The list of races. **This is the only file you edit.** |
| `README.md` | These instructions. |

---

## Read this first: what must never go on the page

This repository is **public**. Anything you put in `events.json` can be read by
anyone in the world, including people who are not connected to the club. It can
also be found by search engines. Deleting something later does not reliably
remove it, because copies may already have been saved.

**Fine to put on the page:**

- Race names and the organiser's own entry page.
- Venue names and postcodes (for example "Temple Newsam, Leeds").
- Dates, start times and meeting times.
- A coach's first name ("ask Sarah at training").
- Age groups, distances and entry costs.

**Never put on the page:**

- Any child's name. Not first names, not nicknames, not "Emma's dad is driving".
- Any phone number or email address belonging to a parent, a child or a coach.
- Anyone's home address, including using a family's house as the meeting point.
  Meet at the venue, a car park, or the club, never at somebody's home.
- Photographs of children.
- Anything about a child's health, school or ability.

If you want to say who to contact, point people at training or at the WhatsApp
group instead of publishing a number. If you are not sure about something,
leave it out and ask first.

---

## Adding a race from your phone

This is the job you will do most often. It takes about a minute.

1. Open the **GitHub** app (or github.com in your phone's browser) and go to
   this repository.
2. Tap **`events.json`**.
3. Tap the **pencil** icon to edit it.
4. Find an existing race block — everything from one `{` to its matching `}` —
   and copy it. Paste the copy in, then change the details to the new race.
5. Tap **Commit changes**.
6. Wait about 30 seconds, then refresh the page. The new race will be there.

### The two mistakes everyone makes

**Commas.** Every race block needs a comma after its closing `}` — except the
very last one in the list, which must have no comma. Miss one out, or leave one
on the end, and the page will show an error instead of the races.

**Quote marks.** Every piece of text needs a `"` at each end. If you type an
apostrophe in a word like `don't`, that is fine. If you delete a `"` by accident,
the page breaks.

### What a race looks like

Only `name` and `date` are required. Every other line is optional — delete any
line you do not have, and it simply will not appear on the page.

```json
{
  "name": "West Yorkshire XC League - Race 1",
  "date": "2026-10-10",
  "time": "11:15",
  "venue": "Temple Newsam, Leeds",
  "distance": "2km (U11) / 3km (U13)",
  "ageGroups": "U11, U13, U15",
  "entryDeadline": "2026-10-01",
  "cost": "£4",
  "link": "https://the-organisers-entry-page",
  "notes": "Tell a coach by the deadline."
}
```

What each line does:

- **name** — what parents will see. Required.
- **date** — the day of the race, written as year-month-day: `2026-10-10`.
  Required. It must be in that exact shape, with the dashes.
- **time** — the start time on a 24 hour clock: `11:15`, or `14:30` for half two
  in the afternoon. Leave the whole line out if you do not know it yet, and the
  race shows as an all-day event.
- **venue** — where it is. This also turns on the **Map** button.
- **distance**, **ageGroups**, **cost** — free text, write whatever makes sense.
- **entryDeadline** — same date shape as above. The page works out how long is
  left and shows a warning as it gets close.
- **link** — the organiser's own entry or information page. It must start with
  `http`. This turns on the **Entry / details** button.
- **notes** — one short sentence. Good for "meet at the club tent".

You do not need to put the races in date order. The page sorts them itself, and
moves anything in the past into the **Past events** section at the bottom.

### Clearing out old races

Keep about two years of past races, then delete anything older. Each
September, at the start of a new season, remove the races from two seasons ago.
This keeps `events.json` short enough to edit safely. Deleted races are not
lost — git still has every earlier version of the file if you need one back.

### If you were sent the details as a screenshot or a messy message

Type the bits you can read into the block above and leave out the rest. A race
with only a name and a date is still useful — you can fill in the details later
by editing the same block again.

---

## When the page shows an error

If someone reports that the page is broken, it will be a typing mistake in
`events.json`, almost always a comma or a quote mark. The page will say so
rather than going blank.

**To fix it:**

1. Open `events.json` in GitHub and copy everything in it.
2. Go to **jsonlint.com**, paste it in, press **Validate**.
3. It will point at the line with the mistake. Go back to GitHub, fix that line,
   commit.

**Or, to undo it:** open the **Commits** list in the repository, find the change
that broke it, and revert it. The page goes back to how it was.

---

## Letting other coaches edit the list

1. In the repository, go to **Settings** → **Collaborators**.
2. Press **Add people** and enter their GitHub username or email.
3. They need a free GitHub account. They will get an invitation to accept.

Parents need nothing at all. They only ever open the link.

---

## Setting the page up (already done — here for reference)

1. Create a **public** repository on GitHub called `otley-ac-events`.
2. Put `index.html`, `events.json` and `README.md` in the top level of it.
3. Go to **Settings** → **Pages**.
4. Under **Source**, choose **Deploy from a branch**.
5. Set the branch to **main** and the folder to **/ (root)**. Press **Save**.
6. Wait a couple of minutes. The page appears at
   `https://mikerossiter.github.io/otley-ac-events/`.

---

## Previewing on your own computer

Opening `index.html` by double-clicking it will **not** work. Browsers block a
page opened that way from reading `events.json`, so you will see the error
message instead of the races.

Run a small web server from the folder instead:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser. Press `Ctrl+C` in the
terminal when you are finished.
