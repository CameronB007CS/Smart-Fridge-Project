[README.md](https://github.com/user-attachments/files/27148425/README.md)
# FrostIQ — Smart Fridge OS
# Team Project, the coding section was assigned to me Cameron Brtoherton
> CST190.3 Agile Mini-Project · Sprint 4 Final Delivery

FrostIQ is a browser-based Smart Fridge management system built across four Agile sprints for CST190.3. It simulates an intelligent refrigerator operating system — tracking inventory, managing expiry dates, suggesting recipes based on what you currently have, generating a shopping list, and giving you a rough nutritional overview of your fridge contents. Everything runs client-side with zero backend and zero external dependencies beyond a Google Fonts stylesheet.

---

## Live Link to access the program here:

The entire application is a single `index.html` file. Open it in any modern browser and it works immediately — no build step, no installation, no internet required (except for the fonts). Easy stuff

Access Link to program is here: https://cameronb007cs.github.io/Smart-Fridge-Project/

---

## Features

# Dashboard
- Time-aware greeting (morning / afternoon / evening) with live clock
- Four KPI cards: total items, expiring soon, expired, and fresh
- Animated arc gauge showing fridge capacity as a percentage
- Status breakdown donut chart with legend
- Environment panel showing current temperature, interior light level, and door status
- Expiry timeline listing the next 7 items to expire, colour coded by urgency
- Quick-add strip for fast inventory entry without leaving the dashboard

# Inventory
- Full CRUD — add items with name, category, quantity, and expiry date
- Colour coded status badges: **Fresh**, **Expiring Soon** (within 5 days), **Expired**
- Filter by status and category; free text search
- Sort by name, expiry date, date added, or category
- Quantity increment/decrement controls on each card
- Disposal alert panel listing all expired items that should be thrown out

# Recipes
- Recipe database matched against current fridge contents
- Colour coded match bar showing what percentage of ingredients you have
- Filter by "Ready to Cook" (all required ingredients present) or partial match
- Clickable cards open a detailed modal with step by step instructions, per ingredient availability check, cook time, difficulty, serves, and calorie count

# Shopping List
- Manual item addition with High / Medium / Low priority levels
- One-click auto-populate from expired and expiring soon inventory
- Checkbox completion with live progress bar and percentage
- Rough cost estimate for remaining unchecked items based on category averages

# Nutrition Overview
- Estimated macro breakdown (protein, carbs, fat, fibre) from fresh fridge contents
- Category distribution donut chart rendered on canvas
- Auto-generated dietary tips based on what is and isn't in the fridge

# Settings & Utilities
- Kitchen countdown timer with 1m, 5m, 10m, 30m, 1h presets and a custom input
- Temperature, interior light, and freezer temperature sliders
- Toggles for power saving mode, door ajar alarm, and expiry notifications
- Dietary preference chips (Vegetarian, Vegan, Gluten free, etc)
- Household size setting



# Challenges Faced

| Concern       | Approach                                              |
---------------------------------------------------------------------------------------
| Language      | Vanilla HTML, CSS, JavaScript            
| Fonts         | Google Fonts — Syne (display), DM Sans (For body)                              
| Persistence   | Browser `localStorage`                                
| Build tooling | None - single self contained HTML file                
| Hosting       | GitHub Pages                    

No npm, no bundler, no framework. The whole application is one HTML file with inlined CSS and JS, which means deployment to GitHub Pages is quite literally just pushing the file and flipping the Pages switch.



Everything is bundled into `index.html` to eliminate the file linking issues that can occur with relative paths in certain hosting configurations. The CSS uses a `:root` block of custom properties for the full colour palette, and the JS is organised into clearly labelled sections (State, Boot, Navigation, Inventory, Recipes, Shopping, Nutrition, Settings, Helpers).



# Design Decisions

**Single file.** The original three file structure (index.html / style.css / app.js) worked perfectly in a local dev environment but introduced file no found issues when opened directly as a file in some browsers, and edge cases with relative path resolution on certain GitHub Pages configurations. Bundling everything into one HTML file eliminates all of that — it is the most robust delivery format for a static prototype with no build pipeline.

**No framework.** The scope of the project didn't justify the overhead. Bringing in React or Vue would have added a build step that slowed down sprint reviews. Vanilla JS meant: change a function, refresh, done.

**localStorage for persistence.** What we aimed for in the project was real persistence across page refreshes without any backend infrastructure. localStorage gives you that with two lines of code and no deployment complexity. On first load, the app seeds eight demo items so the dashboard is immediately populated and interactive — reviewers don't have to manually add data just to see what it does.

**Canvas for charts.** Chart.js is ~60KB. Drawing arcs is not complicated, and keeping it native means the app works fully offline after the fonts have loaded once.

**Boot sequence.** Smart appliances have some form of system initialisation feedback — it communicates that the product has weight and complexity. A blank page snapping to content doesn't do the same thing. The animated ring and progress bar serve a genuine UX purpose.



# Agile Context

Developed across four two week sprints for CST190.3.

| Sprint | Focus |
------------------
| 1 | Requirements gathering, user stories, initial wireframes (Kind of low quality) |
| 2 | Core inventory CRUD, expiry logic, basic UI scaffolding, (Wireframes using figma) |
| 3 | Recipe engine, shopping list, settings panel, Properly designed wireframes initially using python |
| 4 | Nutrition view, UI polish, boot sequence, single file delivery, Final piece using a mix of Javascript, CSS, and HTML |

Each sprint followed standard Agile ceremonies — planning, daily standups, review, and retrospective. The backlog was maintained in a shared board and refined at the start of each sprint based on feedback from the previous review.


# Ethical things to consider

**Data privacy.** All user data is stored exclusively in the browser's `localStorage` on the user's own device. Nothing is transmitted to any external server. There is no analytics, no tracking, and no third-party data sharing of any kind. Users can export their data as JSON or delete everything at any time from the Settings view.

**Food waste reduction.** The core purpose of FrostIQ is to reduce household food waste through better visibility into expiry dates and smarter recipe suggestions from what you already have. This aligns with broader sustainability goals around reducing the environmental impact of food disposal.

**Accessibility.** The interface uses colour contrast ratios that meet WCAG AA standards for the status indicators, and interactive elements are keyboard accessible. ARIA labelling could be expanded in a future sprint.

**Nutritional disclaimers.** The macro estimates are approximations based on food category averages, not precise per item nutritional databases. The application does not position itself as a dietary advice tool — the Nutrition view is explicitly framed as an estimate.


# Known Limitations

- Recipe ingredient matching is stringbased, so "Greek Yoghurt" won't match a recipe that calls for plain "Yogurt". A future sprint would normalise ingredient names through a lookup table or fuzzy matching.
- Nutrition figures are rough category averages, not verified nutritional data.
- No multiuser support — all data lives in a single `localStorage` namespace.
- The kitchen timer resets on page reload (intentional — it is a session utility, not a persistent alarm).

# Thanks for reading me :)


