# Black Forest trip site

The site is a single-page Hebrew RTL `index.html`, published on GitHub Pages from the default branch `ccr-8e4e6093-8lwruz`.

- Answer the user in Hebrew.
- **Publish after every change.**
  1. Commit.
  2. `git fetch origin && git merge origin/ccr-8e4e6093-8lwruz`. The price bot commits there every 2 days.
  3. Push to the working branch and to `ccr-8e4e6093-8lwruz`.
- **Adding, replacing or removing an attraction:** follow the `add-attraction` skill (`.claude/skills/add-attraction`).
- **Any itinerary change** (times, order, days, lodging): run the `route-checker` agent (`.claude/agents/route-checker.md`), then fix 🔴 findings.
- Costs are by age: 2 adults and kids 3, 7, 10. The 3-year-old is not counted in meals.
- Departure at 09:00 every day. The flight on 29.8 is at 07:30.
