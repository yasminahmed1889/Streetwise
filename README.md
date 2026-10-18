# Streetwise

**A travel budget companion for Wise.** Plan a trip, see the budget, and set up a Wise Jar to save for it.

Built for the Wise **"Max Ease"** track at the IKU Womxn in STEM Hackathon (17-18 October 2026).

> **Unofficial prototype, not affiliated with Wise.** All Wise data (balances, Jars, fees, plans) is simulated.

**Open the final prototype:** [`prototype/streetwise-final.html`](prototype/streetwise-final.html)

**Full feature breakdown (MVP, extras, future iterations):** [`docs/FEATURES.md`](docs/FEATURES.md)

- **Team:** Helen, Yasmin, Manya

---

## Where to see it

The working prototype is a single HTML file. No install or build step is needed: download the repo and open the file in a browser.

| File                                  | What it is                                                         |
| ------------------------------------- | ------------------------------------------------------------------ |
| `prototype/streetwise-final.html`     | **Final version, the one used for judging**                        |
| `prototype/streetwise-wise-ds-3.html` | Earlier iteration (iteration 1), kept to show how the idea evolved |
| `prototype/streetwise-wise-ds-2.html` | First iteration (iteration 0)                                      |

Open it in a phone-sized window (or use your browser's device toolbar) for the intended mobile layout.

---

## The problem

Travel money stress happens at two moments. Before the trip, people guess a budget and don't know how much to save. During the trip, they stand in front of a price in an unfamiliar currency and wonder whether it's fair and whether they can afford it. Wise already helps with the money mechanics (fair exchange rates, the card, the Travel Hub). We think there is a gap between planning a trip and the moment you stand in front of a price, and Streetwise is a prototype of how to connect the two.

## What the prototype does (final version)

1. **Home:** two entry points, "Create new plan" and "View my plans", under the Travel tab of the bottom navigation (kept separate from Home, which is a simple placeholder for Wise's own dashboard).
2. **Create a plan in three steps:**
   - **Step 1:** choose "Wise recommended budget" or "Create your own budget". With your own budget, you set a daily target spend and the app works out the total trip cost for you (rather than asking you to work out a total yourself).
   - **Step 2:** trip details: destination, trip length, travellers and price range (standard, boost, luxury). Enter your current costs for flights and accommodation if you already know them, or leave blank for an estimate. Add attractions and restaurants to an itinerary list and the app estimates a price for each (including a small set of named landmarks, e.g. the Eiffel Tower, priced at its real ticket cost rather than a generic guess).
   - **Step 3:** set up a Wise Jar: a savings goal, either a weekly saving amount (with a slider showing your funded-by date) or a deadline (with the app working out the weekly and monthly amount needed). A currency toggle lets you view and save the goal in the destination currency (e.g. EUR) at the app's own exchange rate, converted live when toggled.
3. **My plans and trip detail:** each plan shows Jar progress, a budget breakdown, and a "+ Add £20 to Jar" button that updates the Jar live.
4. **Price confidence and live pace screens:** a price-scan screen and a live pace/warnings screen are reachable from the trip detail screen. These are included to show the direction of the product beyond the core planning and saving flow, and were presented live as a forward-looking part of the idea rather than a finished feature.

For the full list of what is core MVP, what we built beyond it, and what is still to come, see [`docs/FEATURES.md`](docs/FEATURES.md).

---

## Feedback we acted on

We showed the idea to Wise employees and used their feedback:

- **Convenience matters** ("one more click is one less customer"), so the flow was simplified to a short guided wizard with a minimal home screen, and we removed anything that didn't directly serve planning or saving (an advertising placeholder and a round-up toggle were both cut).
- **Avoid a chatbot**, since it would be limited and hard to run reliably, so planning is a guided form and not a chat.
- **Connect the savings goal to Wise's own saving feature**, so the plan ends in a Wise Jar. (Check Wise's current name for this feature before relying on it.)
- **Use mock data for the demo**, so all plans and prices are seeded sample data.
- **Wording should be unambiguous:** "travel style" became "price range", and the budget input was reworked so it's clear whether you're entering a daily figure or a trip total.

---

## What's real and what's simulated

| Real                                                                                                 | Simulated                                                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Budget totals, category splits and savings timelines are calculated by plain code in the page        | Wise account, balances and Wise Jars                                                                         |
| The planning flow and screens work and respond to input                                              | Cost estimates (flights, stays, itinerary items) come from fixed formulas and lookup tables, not live prices |
| The EUR currency toggle recalculates the Jar goal and savings amounts using the app's own rate table | Exchange rates are fixed sample values, not a live rates API                                                 |
|                                                                                                      | The three seeded example plans (Lisbon, Rome, Paris)                                                         |
|                                                                                                      | The scan and warnings screens use sample items, not a real camera or live data                               |

---

## AI usage and transparency

| Part                                                 | AI role                                        | Team role                                                     |
| ---------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------------------- |
| Prototype code (HTML, CSS, JavaScript)               | Generated with Claude ("vibe coded")           | Prompting, review, testing, choosing what to keep             |
| Concept, problem definition, feature list, user flow | Claude helped with brainstorming and planning  | Original idea, requirements, and decisions came from the team |
| Wise employee feedback                               | None                                           | Gathered and applied by the team                              |
| Budget and savings maths                             | None at runtime (plain JavaScript in the page) | Logic specified by the team                                   |
| README and feature documentation                     | Drafted with Claude's help                     | Reviewed and edited by the team                               |

The prototype itself makes **no live AI calls**. All numbers on screen come from deterministic code and seeded data, so figures a user relies on never come from a guess. Any estimate is labelled as an estimate.

---

## Repo map

| Path                     | Status                                                                                      |
| ------------------------ | ------------------------------------------------------------------------------------------- |
| `prototype/`             | **The prototype. This is what to look at.**                                                 |
| `docs/`                  | Feature documentation (`FEATURES.md`)                                                       |
| `unused-react-scaffold/` | Unused React + Vite starter, kept on purpose (see Challenges). It has its own short README. |
| `README.md`              | This file                                                                                   |

---

## Challenges we faced

- **Only one of us had coding experience.** We started by building the app by hand in React with Vite, and set up the project scaffold for it. As we planned the full feature set against the time available (about a weekend, with most of the team new to coding), we realised a hand-built React app with a camera scan, live exchange rates and a backend would not be feasible for us.
- **We changed approach.** We decided to put the time into getting the idea right and building a clickable prototype, so we used AI-assisted ("vibe") coding for the prototype and spent the team's effort on the concept, the flow and the feedback from Wise employees. The unused scaffold stays in the repo, in `unused-react-scaffold/`, as a record of that decision.
- **Scoping honestly.** We cut features we couldn't build reliably (real camera scan, live rates, the correction loop and the payment screen), and we repeatedly simplified the UI during build based on feedback: removing an advertising card and a round-up toggle, clarifying wording like "travel style" to "price range", and reworking the daily-spend input so it couldn't be misread as a total.
- **Keeping it believable.** With no access to real Wise data, we had to simulate balances and prices and be explicit about it.

## Known limitations

- Plans you create reset when the page is refreshed (nothing is saved).
- New plans use a fixed departure estimate, whatever deadline is chosen.
- The scan and warnings screens are prototypes using sample data, reachable from any trip but not wired into the main planning flow.
- The seeded example plan numbers are illustrative and not tuned to be fully consistent with each other.
- The itinerary pricing lookup only recognises a small set of keywords and named landmarks; anything else falls back to a generic estimate.
- The currency toggle uses the app's own fixed rate table, not a live exchange rate feed.

## What's next

1. Replace sample items with a real camera scan that reads a price and shows its effect on the budget.
2. Add a correction step, so if a scan misreads a price, the user fixes it and the app shows exactly what changed.
3. Add a simulated payment screen that warns when a card terminal offers to charge in the wrong currency.
4. Add a voice readout of results for people with low vision or low confidence in the language.
5. Use live exchange rates and persist plans between sessions (e.g. local storage, then a real backend).
6. Connect to real Wise data, with Wise's guidance on what's possible.
7. Move the prototype into a proper React app once the team has the time and skills, reusing the existing Vite scaffold in `unused-react-scaffold/`.
8. Expand the itinerary and landmark pricing from a fixed lookup table into a live pricing source, so any attraction or restaurant typed in gets a realistic estimate, not just the ones we've hard-coded.
9. Build out the Home tab into an actual Wise dashboard view, rather than a placeholder, so Streetwise sits naturally alongside the rest of the app.
10. Revisit round-up savings and any other feature we cut for time, if user feedback shows demand once the core planning-and-saving loop is validated.
11. Add accessibility passes (screen reader labels, larger touch targets, colour-contrast checks) across all screens, not just the ones built last.

---

_Built during the hackathon. Not financial advice. Estimates are illustrative._
