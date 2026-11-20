# Website Scorecard for Renovators & Builders

A free 2-minute website check for renovation and construction businesses (renovators, general contractors, builders and trades), made by **Makepeace Web Design**.

Homeowners check a contractor's website before they call. The scorecard asks 7 quick questions to show whether that website turns homeowners into quote requests. It then gives the contractor their score and top fixes, and offers a free personal audit.

## How it works

1. **Intro.** "Is your website winning you jobs?"
2. **Type of work.** The contractor picks every type that applies: Kitchens & bathrooms, Basements, General contracting, Decks, fences & landscaping, Roofing, HVAC, plumbing or electrical, or Other.
3. **7 questions**, each answered *Yes*, *Not sure* or *No*:
   1. A "Get a Free Quote" button visible without scrolling
   2. A tap-to-call phone number on mobile
   3. A quote form that asks about the project
   4. Before & after photos of real projects
   5. Service areas listed by name
   6. A Google Business Profile linked to the website
   7. Reviews, years in business, and licensing or insurance on the homepage
4. **Results**
   - A score out of 7, with a message for each level: 6 to 7, 3 to 5, or 0 to 2.
   - One personalized line based on the first type of work they picked.
   - A fix card for every question not answered *Yes*. The fixes that matter most for their type of work go first.
   - A form to request a free personal audit.

Only *Yes* answers count toward the score. *Not sure* answers get a fix card marked "Worth checking".

All copy is written in trade language: homeowners, jobs, quote requests, projects. It avoids marketing jargon.

## What's collected

When a contractor requests an audit, the form sends this to [Formspree](https://formspree.io), which emails it to Makepeace Web Design and saves it in the Formspree dashboard:

| Field | Source |
| --- | --- |
| Name | Typed by the visitor |
| Email | Typed by the visitor |
| Business name | Typed by the visitor |
| Website URL | Typed by the visitor |
| Type of work | Hidden field, from the first question (all selections, comma-separated) |
| Score | Hidden field, for example `4/7` |
| Answers | Hidden field, the answer to each of the 7 questions |

Nothing is sent until the visitor submits the audit form. Their score is shown without asking for any details.

## Setup

Everything lives in one file, `website-scorecard.html`. It needs no build step and no dependencies apart from the Outfit font, which loads from Google Fonts.

**Form endpoint.** Submissions go to the Formspree form set in `FORM_ENDPOINT` near the top of the script:

```js
var FORM_ENDPOINT = 'https://formspree.io/f/xjywegkv';
```

To send submissions somewhere else, replace this with another Formspree endpoint, or any endpoint that accepts a `POST` of form data and returns JSON.

## Putting it online

Choose one:

- **Framer:** add a page such as `/scorecard`, drop in an **Embed** element, and paste in the contents of `website-scorecard.html`.
- **GitHub Pages:** in this repository go to **Settings → Pages**, choose the `main` branch, and save. The page will be at `https://matthew-makepeace.github.io/website-scorecard/website-scorecard.html`. Rename the file to `index.html` if you want the shorter `/website-scorecard/` address.

After it's live, send one test submission and confirm the form in the email Formspree sends the first time.

## Editing the content

Everything you'd want to change is in the `<script>` near the bottom of the file:

- **`WORK_TYPES`:** the type-of-work options. Each one has the personalized results line (`line`) and the question whose fix it moves to the top (`priority`, 1 to 7).
- **`QUESTIONS`:** each question's wording, its hint, the fix card title and copy, and its icon (`i-hammer`, `i-house`, `i-ruler` or `i-hardhat`).
- **Results messages:** the three score levels are set in `renderResults()`.

Colours are CSS variables at the top of the `<style>` block: navy `#0B1120` and yellow `#F5C518`.

## Accessibility

- Works with a keyboard, with visible focus outlines.
- Answer buttons report whether they're selected to screen readers.
- Progress is announced as you go, and animation turns off for anyone who has reduced motion set on their device.
- Laid out for phones first, with no sideways scrolling.

---

Makepeace Web Design · Websites for renovators & builders · [matthewmakepeace.framer.website](https://matthewmakepeace.framer.website/)
