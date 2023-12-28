---
tags:
  - react
  - CSS
  - components
  - scope
---
# Vanilla CSS Styles are NOT Scoped
* If CSS files are split across components, multiple files, then importing certain files, the CSS rules are not scoped to that component
* Instead, you'll see that all the styles are injected into the Head section
* They're applied globally to the page, not necessary a problem but something to keep in mind for the future