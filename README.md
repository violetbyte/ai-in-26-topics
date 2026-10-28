# AI in 26 Topics

A plain-language website that explains AI through 26 topics, shown as a climb up a mountain trail. By Ishika Singh.

## How it works

The whole site is one file, `index.html`: HTML, CSS and JavaScript with no build step and no downloads. Open it in a browser to run it, or upload it to any static host. It uses the system font, so nothing else is needed.

Inside the file, the JavaScript is split into labeled blocks (`/* ==== name.js ==== */`):

| Block | What it does |
|---|---|
| `topics.js` | The ordered list of 26 topics (title, level, short summary) and the full text for Tokens and temperature. |
| `content1.js`, `content-more.js`, `content2.js` | The text of the other topics: explanation, analogy, three "what to remember" points. |
| `app.js` | Light and dark mode toggle, and saving progress in the browser. |
| `demo-tokens.js`, `demo-more.js`, `demo-last.js` | The nine interactive demos. |
| The last script | Builds the mountain and the 26 topic sections from the data above. |

## Mountain and progress

The mountain is an SVG drawn by JavaScript. The 26 stops sit on a hand-placed winding trail (the list `P` in the last script) drawn through a ridgeline. A flag marks the end of each of the four camps, which are the four levels, and a pin marks the next unfinished stop. "Mark as finished" saves the topic's key in the browser's localStorage and the mountain redraws, moving the climber to the next unfinished stop. Progress never leaves the visitor's browser. Nothing is locked, and visitors can jump to any stop.

## How to add or edit a topic

1. Add or change its entry in the `TOPICS` list. The order in the list is the order on the trail.
2. Add or edit its text under the same key (`p` for paragraphs, `a` for the analogy, `r` for the three points).
3. To give it a demo, write `DEMOS.KEY = function(el){...}`. The page calls it automatically and gives it a card to draw into.
4. If the number of stops changes, add or remove points in the list `P` and update the camp ends so the trail still fits.

## How each demo works

- **Tokens and temperature:** splits text into pieces of up to 5 characters (a simplification). Temperature divides the example scores before softmax, and "Pick a word" samples from the resulting probabilities.
- **Embeddings:** 12 words with made-up 2D positions. The three nearest by straight-line distance are outlined.
- **Attention:** fixed, made-up weights for the word "it" that shift when the last word changes.
- **RAG:** three made-up documents. Keyword overlap picks one, and the answer repeats it.
- **Hallucination:** five pairs of statements. One in each pair is written to be false. Each true one links to a source.
- **Context window:** items fill a 100-token pretend window. When one no longer fits, older items are dropped.
- **Neural network:** one unit learns an OR rule with the perceptron update rule.
- **Prompting:** hand-written example results for a weak and a strong prompt.
- **Overfitting:** fits a polynomial of the chosen degree to made-up noisy points by least squares, and reports error on training data and on held-out points.

All demo data is invented and labeled as such on the page.

## Deployment

Put `index.html` in a folder and drag the folder to Netlify Drop, or upload it to GitHub Pages or Vercel. No backend is needed.

## What I decided and checked

- I chose the topic list, the four levels, the mountain-trail layout, the paper-and-ink look and the site name.
- I checked the five true statements in the Hallucination demo against their linked sources.
