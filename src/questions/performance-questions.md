---
title: Performance Questions
layout: layouts/page.njk
permalink: /questions/performance-questions/index.html
---

* What tools would you use to find a performance bug in your code?
  - Artillery.io, Loader.io, New Relic, Chrome DevTools

* What are some ways you may improve your website's scrolling performance?
  - Use the correct size images instead of resizing them with CSS
  - Use less "expensive" styles like box-shadow
  - Avoid reflow and repaints
  - Render only part of the data
  - Debouncing: allows us to "group" multiple sequential calls into a single one. Sequential fast events will be represented by a single debounced event. But if the events are triggered with big gaps, the debouncing doesn't happen.

* Explain the difference between layout, painting and compositing.
  - Layout: Once browser know which rules to apply to an element it will determine how much space each element takes up and where to place it.
  - Painting: This is the process of filling in pixels. It involves drawing out elements on mulitple layers.
  - Compositing: Browser draws the different layers to the screen in the correct order so the page renders correctly.