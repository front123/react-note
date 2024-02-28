### script defer and async
When the browser loads HTML and comes across a `<script>...</script>` tag, it can’t continue building the DOM. It must execute the script right now
#### defer
- `<script defer src="xxx">`: would ignore if no src
- Scripts with defer never block the page.
- Scripts with defer always execute when the DOM is ready (but before DOMContentLoaded event).
- Deferred scripts keep their relative order, just like regular scripts.

#### async
- `<script async src="xxx">`: would ignore if no src
- like defer, also non-block page
- script independent
- Other scripts don’t wait for async scripts, and async scripts don’t wait for them.
- DOMContentLoaded and async scripts don’t wait for each other