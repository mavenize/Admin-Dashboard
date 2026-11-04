# Admin Dashboard: Frontend Implementation Plan

## Context
The repo (`Admin-Dashboard`) only has a README ("Admin Dashboard to practice CSS Grid"), the design mockup `Admin Dashboard final look.png`, and the todo4vcode task file `.todo4vcode/shared-tasks.json`. The goal is to build the page in the mockup using only HTML and CSS:
- **All layout uses CSS Grid**: the page shell, header, cards, the card grid and the right column. Flexbox is not needed.
- **Icons:** SVGs from Material Design Icons (pictogrammers.com/library/mdi), which match the mockup's icon style.
- **Font:** Roboto from Google Fonts.
- **Avatars:** free illustrations downloaded from the web (DiceBear, for example) into `assets/images/`.
- **Responsive:** desktop to match the PNG, plus tablet and mobile breakpoints.

Each task below is one todo4vcode task (ID `AD-xx`) and ends with **one commit**, so work can be pushed and merged step by step.

## File structure
```
index.html
styles/
  reset.css        # minimal reset
  style.css        # tokens + layout + components + media queries
assets/
  icons/           # reference copies of the MDI .svg files
  images/          # avatar images (morgan, tegan, kendall, alex)
docs/
  implementation-plan.md   # this file
```
Icons are placed in the HTML as **inline `<svg>` with `fill="currentColor"`**, so CSS controls their color: white in the sidebar, dark gray on cards. The `.svg` files in `assets/icons/` are kept as the source copies.

## Design tokens (`:root` in style.css)
- `--blue: #4592d3` (sidebar and buttons, sampled from the PNG), `--accent: #e8b84b` (card left border, avatar background), `--bg: #e2e8f0` (main area), `--surface: #fff`, `--text: #111`, `--muted: #555`, `--search-bg: #e2e8f0`
- Radius: cards `8px`, buttons/search `999px`. Card shadow: `0 2px 6px rgba(0,0,0,.15)`
- Font: `Roboto`, weights 400/500/700

## Layout (grid)
- **Body:** `grid-template-columns: 280px 1fr; grid-template-rows: auto 1fr;` with areas `"sidebar header" "sidebar main"`.
- **Sidebar:** a grid of rows (logo, primary nav, gap, secondary nav). Each nav item is a grid `auto 1fr` (icon + label).
- **Header:** a 2-row grid.
  - Row 1: search (icon + input) and the bell, avatar and name.
  - Row 2: greeting avatar, "Hi there / Morgan Oakley (@morgan)" and 3 buttons.
- **Main:** `grid-template-columns: 1fr 360px`, with areas `"projects aside"`.
  - **Projects:** `repeat(auto-fit, minmax(300px, 1fr))`, which gives 2 columns at desktop width.
  - **Project card:** a grid with title, text and an actions row aligned to the end. Its yellow left border comes from `border-left: 8px solid var(--accent)`.
  - **Aside:** a grid stacking the Announcements card (3 items, separated by bottom borders) and the Trending card (4 rows, each a grid `auto 1fr`: avatar + handle/project).

## Icons needed (MDI names)
`view-dashboard`, `home`, `card-account-details`, `message`, `history`, `file-multiple`, `account-group`, `cog`, `help-box`, `shield-check`, `magnify`, `bell-ring-outline`, `star-plus-outline`, `eye-plus-outline`, `source-fork`

## Tasks (each = 1 todo4vcode task = 1 commit)
1. **AD-01 Project scaffold.** Create `index.html` (doctype, meta viewport, Roboto link, CSS links), `styles/reset.css`, `styles/style.css` with `:root` tokens, and `.gitignore` (`.DS_Store`).
   Commit: `chore(AD-01): scaffold html/css project with Roboto and design tokens`
2. **AD-02 Assets.** Download the 15 MDI SVGs into `assets/icons/` and the 4 avatars into `assets/images/`.
   Commit: `chore(AD-02): add MDI icons and avatar images`
3. **AD-03 Page shell grid.** Body grid with sidebar, header and main areas, using placeholder backgrounds to check the layout.
   Commit: `feat(AD-03): add main page grid layout`
4. **AD-04 Sidebar.** Logo and the two nav groups (Home…Communities; Settings, Support, Privacy) with inline icons, white text and hover state.
   Commit: `feat(AD-04): build sidebar navigation`
5. **AD-05 Header, top row.** Search icon and rounded input, bell, avatar and user name.
   Commit: `feat(AD-05): build header search and user bar`
6. **AD-06 Header, greeting row.** Large avatar, greeting text, and the New/Upload/Share pill buttons with hover states.
   Commit: `feat(AD-06): build header greeting and action buttons`
7. **AD-07 Projects section.** "Your Projects" heading, auto-fit card grid, and 6 cards (title, text, star/eye/fork action icons).
   Commit: `feat(AD-07): build project cards grid`
8. **AD-08 Announcements.** Card with 3 announcements and dividers.
   Commit: `feat(AD-08): add announcements panel`
9. **AD-09 Trending.** Card with 4 users (avatar, handle, project).
   Commit: `feat(AD-09): add trending panel`
10. **AD-10 Polish pass.** Match spacing and sizes against the PNG; add focus-visible states for accessibility; use semantic tags (`nav`, `header`, `main`, `aside`, `section`), `alt` text and `aria-label`s on icon-only buttons.
    Commit: `style(AD-10): polish spacing and accessibility to match design`
11. **AD-11 Tablet (≤1024px).**
    - Main becomes one column, with the aside below the projects (Announcements and Trending side by side through a 2-column grid).
    - Sidebar narrows to icons only (labels hidden visually).
    - Commit: `feat(AD-11): add tablet responsive layout`
12. **AD-12 Mobile (≤640px).**
    - Body becomes a single column: the sidebar turns into a top bar with a horizontally scrollable icon nav.
    - Header rows stack and the buttons wrap within the grid.
    - Cards go to 1 column and the aside stacks.
    - Commit: `feat(AD-12): add mobile responsive layout`
13. **AD-13 README.** Screenshot, short description and credits (MDI, avatar source).
    Commit: `docs(AD-13): update README with preview and credits`

## Task tracking and linking code to tasks
Tasks live in `.todo4vcode/shared-tasks.json` (todo4vcode shared tasks, committed to Git). Every code change must be tied to its task:
- **Task ID:** each task has a fixed `id` (`AD-01` … `AD-13`), which also appears in its title.
- **Commits:** the scope of every commit message is the task ID, e.g. `feat(AD-04): build sidebar navigation`. If a change touches 2 tasks, it gets 2 commits.
- **Branches (optional):** `feat/AD-04-sidebar`, merged through a PR whose title starts with the task ID.
- **Code references:** when a task is done, add code-reference tags to it for the code it produced (e.g. `index.html:12-48`, `styles/style.css:60-110`). In todo4vcode these show as clickable badges. Editor selections can also be attached with *ToDo4VCode: Attach Selection to Existing Task*.
- **Status:** set the task to `In Progress` when work starts and to `Done` once its commit is made, and tick its subtasks along the way.

Workflow per task:
1. Set the task to In Progress.
2. Implement it.
3. Check it in the browser.
4. Propose the commit message (with the task ID) to you.
5. Commit after your OK, then push.
6. Add code-reference tags and set the task to Done.

## Verification
- Open `index.html` in a browser (or use the VS Code Live Server extension) and compare it with `Admin Dashboard final look.png` at about 1440px width.
- Use DevTools device toolbar at 1024px, 768px and 375px: there should be no horizontal page scroll and the layout should collapse as described.
- Check in DevTools that layout containers use `display: grid` and that there is no `display: flex`.
- Run the HTML through validator.w3.org; check keyboard tab order and the focus rings.
