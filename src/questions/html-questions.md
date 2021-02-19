---
title: HTML Questions
layout: layouts/page.njk
permalink: /questions/html-questions/index.html
---

* What does a `doctype` do?
  - It informs the web browser about the type and version of HTML used in building the web document. This helps the browser to handle and load it properly.

* How do you serve a page with content in multiple languages?
  - First, need to recognize what language is preferred by current user
    - User can either specify the preferred language or make your best guess on based on existing data about the user.
      - First way to allow user to choose the language of the page is to include locale segment into the url. Alternatively, you can add some add some language selection mechanism that will store the picked language in current session, for example in cookies. So you'll be able to serve the localized version of your page, based on that information.
      - There is a Accept-Language request header that you can use to get the language preference. You can go to preferences in your brwoser to set that up. This information will end up in the Accept-Language request header.
  - After we know what language is preferred, we need to serve the page properly, which includes specifying the proper encoding, and also providing the meta information in headers and html tags, telling what is the language of the content we are serving.
    - Set the charset. You can do this by using a meta or a lang tag. The first thing the browser will check when trying to get the correct charset is the Content Type header.
    - Can optimize for SEO by specifying the canonical url with the default/main language and specify localized versions of the page as alternatives with languages specified in hreflang field so that you don't have duplicated content serving the same page in multiple languages which can hurt SEO.

* What kind of things must you be wary of when designing or developing for multilingual sites?
  - Don't rely on defaults. Always use the lang and the dir attributes in all your HTML.
  - Right and Left sides, make sure they are on the correct side for that language
  - Don't translate anything manually, use CLDR instead
  - Don't use flags in your langauge selector, sometimes have political connotations or can be offensive
  - Don't concatenate translated strings, use template parameters instead

* What are `data-` attributes good for?
  - JavaScript access
    - you can access the data-* in JavaScript and rewrite the values
  - CSS access
    - you can access the data-* in CSS and use it for styling
    - you can also use attribute selectors in CSS to change styles according to the data

* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
  - Semantics: Allowing you to describe more precisely what your content is.
  - Connectivity: Allowing you to communicate with the server in new and innovative ways
  - Offline and storage: Allowing webpages to store data on the client-side locally and operate offline more efficiently
  - Multimedia: making video and audio first-class citizens in the Open Web
  - 2D/3D graphics and effects: allowing a much more diverse range of presentation options.
  - Performance and Integration: Providing greater speed optimization and better usage of computer hardware
  - Device access: Allowing for the usage of various input and output devices
  - Styling: Letting authors write more sophisticated themes.

* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
  - Cookie: Expiration is manually set. Initiated by a Client or a Server. Sent to server with every HTTP request.
  - sessionStorage: Expires on browser or tab close. Initiated by Client.
  - localStorage: lasts however long until manually deleted. Initiated by Client. Persists across browser sessions. Has the highest capacity for storage (5MB per domain)

* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
  -  `<script>`: HTML parsing is blocked, the script is fetched and executed immediately, HTML parsing resumes after the script is executed.
  - `<script async>`: The script will be fetched in parallel to HTML parsing and executed as soon as it is available. Use async when the script is independent of any other script on the page.
  - `<script defer>`: The script will be fetched in parallel to HTML parsing and executed when the page has finished parsing. If there are multiple of them, each deferred script is executed in the order they were encountered in the document. There's not much difference from putting a normal `<script>` at the end of the body.

* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
  - Placing `<link>`s in the head allows the page to render progressively which improves user experience. Not doing so may result in flash of unstyled content.
  - `<script>`s block HTML parsing while they are being downloaded and executed. Downloading the scripts at the bottom will allow the HTML to be parsed and displayed to the user first. One possible workaround is to put the script in the head and use the defer attribute.

* What is progressive rendering?
  - Progressive rendering is the name given to techniques used to improve performance of a webpage (in particular, improve perceived load time) to render content for display as quickly as possible.

* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
  - you would use the srcset attribute when you want to serve different images to users depending on their device display width.
  - the first value is the image name and the second is the width of hte image in pixels.
  - based on the client's resolution, it will display the image with the closest resolution to it.

* Have you used different HTML templating languages before?
  - I've used Underscore's templating before for a small project.
  - I know that the typical usage is when you render something on the server side. The usual use-case is when you have to add dynamic content to your website, so when you fetch something from your database, you will have to replace some parts in your original template.

* What is the difference between `canvas` and `svg`?
  - svg element is a container for SVG graphics.
    - XML-based image format
    - has better scalability, can be printed with high quality at any resolution
    - can be modified through script and CSS
    - vector based and composed of shapes
  - canvas element is used to draw graphics, via JavaScript.
    - modified through scripts only
    - The element is only a container for graphics

* What are empty elements in HTML ?
  - an element from HTML that cannot have any child nodes (i.e. child elements or text nodes)
  - examples are img, input, meta, link, br tags
