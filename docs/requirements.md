# My Orbit (Hobbymaxx) v1.0: requirements for the App Store launch

**Status:** v4, 16 Oct 2026, for van to confirm. It folds in every prototype change van asked for on 14–16 Oct. The real app build waits until this is confirmed.
**Direction (agreed 14 Oct):** keep the product logic from spec v6 and use the **"My Orbit"** visual direction. The flames, hours and timer are dropped for v1.0.
**Clickable prototype:** https://vannymon.github.io/orbit-hobby-tracker/ (source: [../index.html](../index.html)). Section 7 lists where the prototype differs from this spec.
**Sources:**
- spec v6: source/spec.html (not in this repo)
- van's Orbit mock: source/my-orbit-home.png (not in this repo)
- design review: design-review.md (not in this repo)

---

## 1. Product rules

1. **One Focus that you choose.** It never changes or rotates on its own, and the app never suggests one.
2. **A few hobbies in orbit, the rest resting.** You get 3 slots by default (1–5). Resting hobbies are never lost.
3. **No clocks.** There's no hour tracking, no timers, no streaks and no daily lists.
4. **Nothing is ever overdue, missed or red.** Time is shown as neutral facts, for example "Last time 4 days ago".
5. **Size and colour don't rank hobbies on Orbit.** Size marks the Focus, and colour plus icon identify a hobby. The one deliberate exception is the Activity ranking on the Hobbies tab (2.5), which van chose and which needs checking in user testing.
6. **Logging is one tap.** The note, photos and date are optional.
7. **Every destructive or moving action can be undone** for 10 seconds (rest, swap, archive, delete). "Delete all data" is the exception: it asks first and can't be undone.

## 2. Screens

Three tabs: **Orbit · Hobbies · Settings**. Hobby, idea, log and other details open as bottom sheets.

### 2.1 Orbit (home)
- **Header:** "My Orbit", "3 in orbit · 3 resting", and a **+** button. The + asks **An idea** (a title and optional link) or **A hobby** (the New hobby form).
- **Centre:** the Focus hobby, as the largest bubble with a ring.
- **Inner ring:** the other hobbies in orbit, as medium bubbles, up to the slot count. Empty slots are dashed circles. Tapping one opens New hobby.
- **Outer ring:** resting hobbies, as small **grey** bubbles that keep their icon and name. Their colour returns when they come back into orbit. More than 6 collapse into a "+N" bubble.
- **Bubbles:** a tinted fill with a dark icon (contrast at least 3:1 for icons and 4.5:1 for text) and a name label, so a hobby is never identified by colour alone. Tapping a bubble opens its hobby page. A resting bubble opens the swap sheet.
- **Motion:** both rings turn slowly together, about one lap every 3 minutes, with Focus fixed in the centre. Rotation pauses while a sheet is open. Resting bubbles drift gently, and a bubble pulses once when you log it or make it Focus. All motion is off with Reduce Motion.
- **Below the orbit:**
  - At most **one surfacing card**: a bench check ("Guitar has rested 6 weeks. Still want it on the bench?" with Bring it back, Keep resting or Archive), a trial ending, or a revisit date.
  - **Next up:** the Focus hobby's card with its goal, progress dots, next step and **Log it**. With no Focus it says "No Focus right now". With no hobbies at all it says to tap + to add your first.
  - **In orbit:** a row for each other hobby in orbit, showing its next step (or when it was last logged) and a **Log** button.

### 2.2 Hobby page (tap a bubble, row or card)
- **Header:** the icon, name, "Last time 4 days ago · 3 logs" (or "Resting 6 weeks"), and a **pencil** at the top right to edit.
- **Status switch:** **Focus · In orbit · Resting**. It shows where the hobby is and changes it in one tap, on the same page. The page keeps its height and the switch stays usable throughout.
  - **Resting** opens a small panel under the switch with an optional pick-up note and **Rest / Cancel** buttons. Tapping another status cancels it.
  - **Focus or In orbit on a resting hobby:** it moves in at once if there's a free slot. If the orbit is full, the panel asks which hobby rests to make room.
  - **Focus on a hobby already in orbit:** it becomes the Focus, and the old Focus stays in orbit.
  - **In orbit on the Focus:** it stops being Focus, and nothing becomes Focus automatically.
- **Goal card:** the goal title and progress dots, then the steps as **checkboxes**. Tap a step to tick or untick it. **Add a step** at the end adds one. Ticking the last open step shows "You did it!" with **Set the next goal** or **Just celebrate for now**. A "Just for fun" hobby shows "No goal. It grows just by doing it." The next step shows under the goal.
- **Log:** a "Log" heading with a small **+ Add new log** button beside it. Logs are newest first, each with its date, note and photo thumbnails. Tapping a photo shows it full size.
- **Bottom:** small links **Archive hobby** and then **Delete hobby**. There are no big action buttons on this page.

### 2.3 Edit hobby (pencil)
- Name, icon (about 40 in the app, 12 in the prototype), colour, **Has a goal / Just for fun**, the goal ("What would done look like?") and the next step.
- Rewording a goal keeps its ticked steps. Switching to Just for fun clears the goal and steps.

### 2.4 New hobby and new idea
- **New hobby:** name, icon, colour, Has a goal / Just for fun, the goal, the first small step, and **Put it: In orbit / Resting**. If the orbit is full, it goes to Resting with a note saying so. A vague goal such as "get better" gets a gentle hint.
- **New idea:** a title (required) and a link (optional).
- **Start it** on an idea opens New hobby prefilled with the idea's title. The idea is removed once the hobby is saved.

### 2.5 Log sheet
- **Save** logs today in one tap. Optional extras:
  - **Today / Yesterday**
  - a note
  - up to **3 photos** (camera or library)
  - **Finished the next step?**, which ticks the next open step and asks what's next
- In the app, photos are stored as files on the device, not in the database.

### 2.6 Swap sheet and Welcome back (tap a resting bubble)
- Shows the pick-up note and next step, with **Bring into orbit**. If the orbit is full, you choose which hobby rests and can leave it a pick-up note.
- Afterwards there's **Undo** for 10 seconds, and a **Welcome back** sheet shows the last photo, the pick-up note and "Does this goal still fit?" (**Keep it** or **Change goal**).

### 2.7 Hobbies tab (renamed from Ideas)
- **Title:** "Hobbies", with the line "Everything at a glance, plus ideas you might try one day."
- **Summary tiles:** in orbit (for example 3/3), resting, ideas, archived.
- **Activity · last 30 days:** every hobby ranked by how many logs it had in the last 30 days, each with a bar in its colour and its count. Above the list is the total ("5 logs across 4 hobbies"). Hobbies with nothing logged show 0 at the bottom, and resting bars are faded. Tap a row to open the hobby. *Deliberate exception to rule 5: check it in user testing.*
- **Your hobbies** with **+ Add Hobbies** beside the heading: one card per hobby, with Focus first, then in orbit, then resting (greyed). A card shows the state, goal progress ("2 of 4 steps" or "Just for fun"), up to 3 recent photos and the latest log with its note. Tap the card for the hobby page, or a photo to see it full size. Cards have no buttons on them.
- **Ideas** with **+ Add Ideas** beside the heading: the same card style, with a bulb icon, the title and "Idea · added 3 days ago". The section always shows, with "No ideas yet." when empty. Tap a card for the idea page.

### 2.8 Idea page
- **Header:** a bulb icon, the title, when it was added, and a **pencil** to edit the title and link.
- The link, if there is one.
- **"Ready to try it?"** with **Start it** (see 2.4).
- **Bottom:** small links **Archive idea** and then **Delete idea**.
- **Still curious?** (planned, not in the prototype): an idea older than 30 days occasionally shows on Orbit as the one surfacing card, with no day count.

### 2.9 Settings tab
- **Orbit**
  - **Hobbies in orbit at once:** 1–5. You can't go below the number already in orbit; it asks you to rest one first.
  - **Weekly check-in:** on or off, with a day (Monday–Sunday) and a time (8am, noon, 6pm, 8pm). It's a local notification that bundles that week's bench checks, revisits and trial ends, and stays silent if there's nothing to say.
- **Appearance:** Match phone, Light or Dark.
- **Resting:** every resting hobby, with how long it has rested. Tap one to open its page.
- **Archive:** archived hobbies ("Archived hobby" or "Finished hobby") and archived ideas, each with **Restore** and **×** to delete. A restored hobby comes back as resting, and a restored idea goes back to Ideas.
- **Your data:** "Everything stays on this phone."
  - **Export everything (JSON):** a full backup.
  - **Export logs (CSV):** one row per log, with hobby, status, date, note and photo count.
  - Both exports show a preview with **Download** and **Copy**.
  - **Delete all data:** a confirm screen with **Export first** offered. It can't be undone.
- **About:** **Privacy policy** and **Help and support**, which uses a placeholder email until launch.

## 3. Features (v1.0)

| Feature | v1.0 | Notes |
|---|---|---|
| Hobbies with one goal or Just for fun | ✅ | Goal steps are checkboxes and you can add more (2.2). |
| "Has an end" (project) | ✅ toggle | When its goal is hit, it offers "Finished" (archived as finished) or "Next goal". *Not in the prototype yet.* |
| Focus + orbit slots + resting | ✅ | Status switch on the hobby page (2.2). |
| Swap + pick-up note + undo | ✅ | |
| Bench checks and revisit dates | ✅ | 6-week default, one card at a time. *Revisit dates not in the prototype yet.* |
| Trial window | ✅ | "Is this for you?" with keep / rest / let go, and one extension. Started from the edit sheet. *Not in the prototype yet.* |
| Logging with photos | ✅ | Up to 3 photos per log (2.5). |
| Ideas | ✅ | Own section, own page, Start it, archive, delete (2.7, 2.8). |
| Edit hobby or idea | ✅ | Pencil on the hobby or idea page only, not on cards. |
| Archive + restore | ✅ | Hobbies and ideas, from their pages. Restore from Settings → Archive. |
| Delete hobby or idea | ✅ | Hobby: a confirm sheet saying how many logs and photos go, with "Archive instead". Both have Undo. |
| Hobbies tab: tiles, activity, cards | ✅ | 2.7 |
| Onboarding | ✅ | One screen explaining the idea, then add your first hobby. Goals optional. *Not in the prototype yet; it shows an empty orbit.* |
| Weekly local notification | ✅ | Settings 2.9. *The prototype saves the setting but sends nothing.* |
| Export / delete all | ✅ | 2.9 |
| Appearance | ✅ | Match phone / Light / Dark |
| Accessibility | ✅ | Name labels, VoiceOver, Dynamic Type, Reduce Motion, 44pt tap targets |
| Gentle motion | ✅ | 2.1 |
| Tonight picker | ⏸ v1.1 | The "Next up" card covers the main job. |
| Fixed dates | ⏸ v1.1 | Per design review |
| Hobby fields (energy, place, materials) | ⏸ v1.1 | |
| Stats page | ⏸ v1.1 | The Activity list covers the basics. |
| Sign-in, cloud backup, Profile tab | ⏸ v1.1+ | |
| Widgets, AI assist, Android | ⏸ later | |

## 4. Data model (changes from van's Expo prototype)

- **Hobby:** `id, name, icon, tint, status ('play' | 'resting'), focus, goal, logs[], restedAt, pickup, keeps, hasEnd, finished`. Add `icon` and `tint`, and remove `flameName` and the flame art fields.
- **Goal:** `kind ('goal' | 'just_for_fun'), title, next, steps[] {text, done}`.
- **Log:** `at, note, photos[]`. Photos are file paths in the app. Drop `kind` and `snack`.
- **Idea:** `id, title, link, addedAt`.
- **Archived** hobbies and ideas are kept in their own lists so they can be restored.
- **Settings:** `slots, weekly {on, day, time}, theme ('system' | 'light' | 'dark')`.
- **Drop:** growth points, stages, moods, accessories and the time-of-day scene.
- Everything else (sync fields, trial and revisit fields) is unchanged.

## 5. What happens to van's Expo prototype

**Kept:**
- the SQLite store
- the state logic for swap, rest, bench check, trial and promote
- the goal builder
- the ideas logic
- the sheet manager

**Replaced:** the scene, flames, feed and flame sheets, moments art and theme. The visuals follow the clickable prototype.

The work will be **branched, not deleted.** The flame version stays in git history.

## 6. Launch defaults

The app is free and iPhone-first, with an individual developer account. Data stays on the device with no accounts. There are no analytics, only anonymous crash reporting. It's English only.

## 7. Prototype vs. this spec

The clickable prototype covers sections 2.1–2.9, except:
- **Not built yet:** trials, revisit dates, "Has an end" / Finished, onboarding, the "Still curious?" card on Orbit, and a real notification.
- **Prototype only:** data is kept in the browser's storage, and photos there fill up after roughly 20–40. There is no reset button; Settings → Delete all data starts fresh.
- **Export on the claude.ai link** asks before saving the file. On a normal web host it downloads directly.

## 8. Still open

1. **Name.** "Hobbymaxx" or something calmer? The screen title is "My Orbit". Is that the app name, or just the home screen?
2. **The two-week Notes test from spec v6.** Did you run it?
3. **"Next:" line.** Should it follow the first unticked step automatically? Recommended: yes.

## 9. To confirm

Reply "confirmed", or tell me what to change.
