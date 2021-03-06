---
title: CSS Questions
layout: layouts/page.njk
permalink: /questions/css-questions/index.html
---

* What is CSS selector specificity and how does it work?
  - CSS selector specificity is what determines what CSS styling is applied.
  - 1000 - style attribute
  - 100 - for each ID
  - 10 - for each class, attribute, or pseudo-class
  - 1 - for each element name or pseudo element

* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
  - Resetting CSS aims to remove all built-in browser styling.
  - Normalizing CSS aims to make built-in browser styling consistent across browsers.
  - I generally choose to normalize CSS but with a little bit of CSS Reset for things such as setting padding and margins of html and body to 0. I choose this way because I believe I can incorporate the benefits of each method while making sure it works for my own application.

* Describe Floats and how they work.
  - Float is a CSS positioning property where floated elements remain a part of the flow of the web page whereas absolutely positioned page elements are removed from the flow of the webpage.
  - There are 4 valid values for the float property. Left and Right float elements those directions respectively. None (the default) ensures the element will not float and Inherit which will assume the float value from that elements parent element.

* Describe z-index and how stacking context is formed.
  - using z-index, the rendering order of certain elements is influenced by their z-index value.
  - There's a long list on MDN about different scenarios on how the stacking context is formed but essentially stacking contexts can be contianed in other stacking contexts, each stacking context is completely independent of its siblings (only descendant elements are considered when stacking is processed), and each stacking context is self-contained.

* Describe BFC (Block Formatting Context) and how it works.
  - A block formatting context is a part of a visual CSS rendering of a web page. It's the region in which the layout of block boxes occurs and in which floats interact with other elements.
  - Examples on how to use BFC include: the root element of the document (<html>), Floats, absolutely positioned elements, inline-blocks, etc.

* What are the various clearing techniques and which is appropriate for what context?
  - The Empty Div Method
  - The Overflow Method
  - The Easy Clearing Method

* How would you approach fixing browser-specific styling issues?
  - Reset CSS or Normalize CSS
  - Use libraries to automatically handle that
  - Vendor prefixes

* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?
  - Graceful degration or progressive enhancement
  - I tend to do graceful degration and vendor prefixes

* What are the different ways to visually hide content (and make it available only for screen readers)?
  - visibility: hidden. However the elemnt is still in the flow of the page, and still takes up space.
  - width: 0; height: 0. Make the elemtn not take up any space on the screen at all, resulting in not showing it.
  - position; absolute; left: -99999px. Position it outside of the screen.
  - text-indent: -9999px. This only works on text within the block elements.

* Have you ever used a grid system, and if so, what do you prefer?
  - float-based grid systems like flexbox and CSS grid. It's used in Bootstrap and even things like React-Native styling so it's proven to be a good solution.

* Have you used or implemented media queries or mobile specific layouts/CSS?
  - Yes. An example would be changing the flex direction from row to columns for mobile display.

* Are you familiar with styling SVG?
  - only by adding CSS classes

* Can you give an example of an `@media` property other than `screen`?
  - All, screen, print, and speech are the four different properties of media.
    - all: is Default
    - print: used for printers
    - screen: used for different screen sizes
    - speech: used for screenreaders that read the page out loud

* What are some of the "gotchas" for writing efficient CSS?
  - Firstly, understand that browsers match selectors from rightmost (key selector) to left. Browsers filter out elements in the DOM according to the key selector, and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector. Hence avoid key selectors that are tag and universal selectors. They match a large number of elements and browsers will have to do more work in determining if the parents do match.

* What are the advantages/disadvantages of using CSS preprocessors?
  - Advantages:
    - CSS is made more maintainable
    - Variables for consistent theming
    - Mixins to generate repeated CSS
    - easy to write nested selectors
  - Disadvantages:
    - requires tools for preprocessing
    - re-compilation time can be slow
  * Describe what you like and dislike about the CSS preprocessors you have used.
    - Sass, LESS, and Stylus are the most popular CSS preprocessors. Have not been able to use them yet.

* How would you implement a web design comp that uses non-standard fonts?
  - use @font-face and define font-family for different font-weights.

* Explain how a browser determines what elements match a CSS selector.
  - Browsers match selectors from rightmost (key selector) to left and top to down of CSS stylesheet.
  - For example with this selector p span, browsers firstly find all the span elements, and traverse up its parent all the way up to the root to find the p element. For a particular span, as soon as it finds a p, it knows that the span matches and can stop its matching.

* Describe pseudo-elements and discuss what they are used for.
  - A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). They can be used for decoration (:first-line, :first-letter) or adding elements to the markup (combined with content: ...) without having to modify the markup (:before, :after)

* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
  - The CSS box model is responsible for calculating:
    - how much space a block level element takes up
    - whether or not borders and or margins overlap or collapse
    - a box's dimensions
  - Adjust either width, height, padding, border, or margin.

* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
  - By default, elements have box-sizing: content-box applied, and only the content size is being accounted for.
  - box-sizing: border-box changes how the width and height of elements are being calculated, border and padding are also being included in the calculation.
  - The height of an element is now calculated by the content's height + vertical padding + vertical border width
  - The width of an element is now calculated by the content's width + horizontal padding + horizontal border width.

* What is the CSS `display` property and can you give a few examples of its use?
  - none, block, inline, inline-block, table, table-row, table-cell, list-item, grid, flex

* What's the difference between inline and inline-block?
  - block:
    - size: fills up the width of its parent container
    - positioning: start on new line
    - can specify width and height: Yes
    - can be aligned with vertical-align: Yes
    - Margins and paddings: All sides respected
  - inline-block:
    - size: depends on content
    - positioning: flows along with other content and allows other elements beside.
    - can specify width and height: yes
    - can be aligned with vertical-align: yes
    - margins and paddings: all sides respected
  - inline:
    - size: depends on content
    - positioning: flows along with other content and allows other elements beside
    - can specify width and height: no, will be ignored
    - can be aligend with vertical align: Only horizontal sides respected. Vertical sides, if specified, do not affect layout. Vertical space it takes up depends on line-height, even though the border and padding appear visually around the content.
    - Margins and paddings: becomes like a block element where you can set vertical margins and paddings.

* What's the difference between the "nth-of-type()" and "nth-child()" selectors?
  - nth-child(): p:nth-child(2) means select an element if:
    1. It is a paragraph element
    2. It is the second child of a parent
  - nth-of-type(): p:nth-of-type(2) means select the second paragraph child of a parent
  - the difference is nth-child will always look at the 2nd child no matter what and apply if it is a paragraph element to the 2nd child. But nth-of-type() will select as long as there are two paragraph child elements under a parent.

* What's the difference between a relative, fixed, absolute and statically positioned element?
  - static: the default position. The element will flow into the page as it normallly would. The top, right, bottom, left, and z-index properties do not apply.
  - relative: the element's position is adjusted relative to itself.
  - absolute: Allows you to literally place any element exactly where you want it. These values will be relative to the next parent element with relative (or absolute) positioning. If there is no such parent, it will default all the way back up to the html element.
  - sticky: a hybrid of relative and fixed positioning. The element is treated as relative positioned until it crosses a specified threshold, at which point it is treated as fixed positioned.

* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
  - Bootstrap: add a spinner component as it is widely used.
  - Haven't been using too many CSS frameworks lately because there are benefits for them as they are fast and reliable, but been focusing more on CSS itself to improve upon my CSS skills and learn more frameworks in the future.

* Have you used CSS Grid?
  - Yes, it's great. great way to set up overall strucutres of different components you have set up for your website.

* Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
  - A responsive website is reactive - the design moving fluidly to fit devices.
  - A mobile-first website is when the mobile website is planned adn designed in tandem with the desktop site, making proactive changes to the overall design to ensure the mobile experience is just as good as the desktop experience.

* Have you ever worked with retina graphics? If so, when and what techniques did you use?
  - The key thing to know is that using a pixel ratio means these displays are emulating a lower resolution screen in order to show elements with the same size.
  - When dealing with retina displays, you can use responsive images. This requires making available different resolution files of the same image to the browser and let it decide which image is best, using the html attribute srcset and optionally sizes.

* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?
  - translate() is a value of CSS transform. Changing transform or opacity does not trigger browser reflow or repaint, only compositions, whereas changing the absolute positioning triggers reflow.
  - transform causes the browser to create a GPU layer for the element but changing absolute positioning properties uses the CPU. Hence translate() is more efficient and will result in shorter paint times for smoother animations.
  - When using translate(), element still takes up its original space (sort of like position: relative), unlike in changing the absolute positioning.

* How is clearfix css property useful?
  - it solves a persistent bug that occurs when two floated elements are stacked next to each other. When elements are aligned this way, the parent container ends up with a height of 0, and it can easily wreak havoc on a layout.

* Can you explain the difference between px, em and rem as they relate to font sizing?
  - px: pixels are considered absolute units. It's fixed and does not change based on any other element.
  - em: relative to the parent element
  - rem: relative to the root element (HTML tag)

* Can you give an example of a pseudo class? Can you provide an example use case for a pseudo class?
  - A CSS psueo class is a keyword added to a selector that specifies a special state of the selected element.
  - For example: button:hover.

* What is the difference between a block level element and an inline element. Can you provide examples of each type of element?
  - block
    - always starts on a new line
    - takes up full width available
    - has a top and bottom margin, whereas an inline element does not.
    - examples: div, h1-h6, footer, form, section, p
  - inline
    - does not start on a new line
    - only takes up as much width as necessary
    - examples: a, span, img, input, textarea, strong, select

