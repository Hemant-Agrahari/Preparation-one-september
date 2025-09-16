Q.What is the use of doctype in HTML?
“The <!DOCTYPE> declaration in HTML is used to tell the browser which version of HTML the page is written in. It’s not an HTML tag, but an instruction for the browser.

In modern web development, we usually write <!DOCTYPE html> which indicates HTML5. Its main purpose is to ensure the browser renders the page in standards mode instead of quirks mode. Standards mode follows the official HTML and CSS specifications, while quirks mode tries to emulate old, non-standard behavior for legacy pages.

By declaring the doctype, we make sure our page is interpreted consistently across different browsers, which improves compatibility and prevents unexpected layout or styling issues.”

Q.What is the difference between HTML and html5?
Ans:HTML and HTML5 are both markup languages used to structure web pages, but they differ in features, syntax, and capabilities:

HTML (older versions, like HTML 4.01)
Primarily focused on structuring content.
Limited support for multimedia, semantic elements, and modern web APIs.
More reliant on external plugins (like Flash) for audio, video, and interactive content.
Syntax was more lenient, less strict.

HTML5 (latest standard)

Designed for modern web development with rich features.
Introduces semantic tags like <header>, <nav>, <section>, <article>, <footer> for better structure.
Natively supports audio, video, canvas, SVG, and offline storage without plugins.
Includes new APIs like Geolocation, Web Storage, Web Workers, and Drag & Drop.

Focuses on performance, accessibility, and cross-device compatibility.

In short:
👉 HTML = basic structure.
👉 HTML5 = modern, semantic, multimedia-rich, and API-enabled web standard.”

Q.WHat is the use of head tag?
The <head> tag in HTML is used to hold metadata and resources about the web page that are not directly displayed to the user. It can include things like the page <title>, links to CSS stylesheets, JavaScript files, meta tags for SEO and responsiveness, favicons, and other information needed for the browser and search engines.

In short, the <head> acts as the configuration section of the web page—helping with styling, behavior, and optimization—while the <body> is for the actual visible content

Q.What is the diff asyn and defer ?
“In HTML, both async and defer are attributes used when loading external JavaScript files with the <script> tag, and both help improve page performance by preventing the script from blocking HTML parsing.

async: The script is downloaded in parallel with the HTML parsing and executes immediately once it’s ready, even if the HTML is still being parsed. This means scripts load faster, but execution order is not guaranteed if multiple async scripts are used.

defer: The script is also downloaded in parallel but executes only after the HTML is fully parsed, and in the order they appear in the document. This ensures scripts don’t interfere with rendering and maintain predictable execution order.

So in short:
👉 Use async for independent scripts (like analytics).
👉 Use defer for scripts that rely on the DOM structure or need to run in sequence.”


Q.List of new HTML5 semantic tags?
HTML5 introduced several semantic tags that give meaning to the structure of a web page. Unlike generic <div> and <span>, these tags describe the role of the content, which improves readability, accessibility, and SEO.

Some of the important new semantic tags are:

<header> – Represents the top section of a page or a section.
<nav> – Defines navigation links.
<section> – Represents a thematic grouping of content.
<article> – For independent, self-contained content like blogs or news.
<aside> – For side content such as ads or sidebars.
<footer> – Defines the footer of a page or sect
<main> – Represents the main content of the document.
<figure> and <figcaption> – For images/illustrations with captions.
<mark> – For highlighting text.
<time> – For dates and times.

In short, these tags make the structure more meaningful for both browsers and developers.”

Q. What is the difference between block level and inline element in html?
“In HTML, elements are broadly classified as block-level and inline elements based on how they behave in the document flow.

Block-level elements:

Always start on a new line.
Take up the full width available (by default).
Can contain other block-level and inline elements.

Examples: <div>, <p>, <section>, <header>, <article>.

Inline elements:

Do not start on a new line.
Only take up as much width as their content requires.
Usually used for styling or small parts of text.

Examples: <span>, <a>, <strong>, <em>, <img>.

Q.What is the difference between HTML, XHTML, and HTML5?
HTML, XHTML, and HTML5 are all markup languages for structuring web pages, but they differ in syntax rules and features:

HTML (HyperText Markup Language)
The original standard for creating web pages.
More flexible and forgiving — browsers can still render pages even if the code has errors.

XHTML (Extensible HTML)
A stricter version of HTML that follows XML rules.
Tags must be properly closed, nested, and written in lowercase.
Example: <br /> instead of <br>.
Designed for cleaner, well-structured documents but was considered too rigid.

HTML5

The latest and current standard.
More flexible than XHTML but more structured than old HTML.
Introduced semantic tags (<header>, <nav>, <article>, etc.), multimedia support (<audio>, <video>), APIs (local storage, canvas, geolocation), and better support for modern devices.
Focused on performance, cross-platform compatibility, and reducing the need for external plugins like Flash.

In short:
👉 HTML = basic markup.
👉 XHTML = stricter, XML-based version.
👉 HTML5 = modern, feature-rich, semantic, and widely used today.

Q.What is the difference between <div> and <span>?
The main difference between <div> and <span> is that:

<div> (Division):

A block-level element.
Used to group larger chunks of content or layout sections.
Always starts on a new line and takes full width by default.
Example: wrapping a section of a webpage like a header or sidebar.

<span>:

An inline element.

Used to style or group small portions of text or inline content.
Does not start on a new line and only takes as much width as its content.
Example: highlighting a single word inside a paragraph.

In short:
👉 <div> = structural grouping (block).
👉 <span> = inline styling or grouping (inline).”

Q.What is the difference between block-level and inline elements?
Block-level and inline elements differ in how they occupy space and interact with other elements:

Block-level elements

Always start on a new line.
Stretch to take the full available width.
Can contain both block and inline elements.
Common examples: <div>, <p>, <section>, <article>, <header>.

Inline elements

Do not start on a new line; they flow within the text.
Only take up as much width as their content requires.
Usually used for formatting or small pieces of content.
Common examples: <span>, <a>, <strong>, <em>, <img>.

In short:
👉 Block = layout/structure (like paragraphs or sections)

Q.What is the difference between HTML tags and attributes?
HTML tags and attributes are different but work together:

Tags

Define the structure and elements of a webpage.
Usually come in pairs: an opening tag <p> and a closing tag </p>.
Example: <h1>Heading</h1> — here <h1> is the tag that defines a heading element.

Attributes

Provide additional information or properties about an element.
Always written inside the opening tag as name="value".

Example: <img src="image.jpg" alt="My Image"> — here src and alt are attributes that describe the image.

In short:
👉 Tags = define the element.
👉 Attributes = define the element’s behavior or properties

Q.What is the difference between <id> and <class>?
“The difference between id and class in HTML is mainly about uniqueness and reusability:

id

Used to uniquely identify a single element on a page.
Should not be repeated within the same document.
Typically used for targeting specific elements (e.g., with JavaScript or anchor links).

Example: <div id="header"></div>.

class

Used to group multiple elements with the same style or behavior.
Can be applied to many elements on the same page.
Commonly used for styling with CSS or applying shared JavaScript functionality.

Example: <div class="card"></div> <p class="card"></p>.

In short:
👉 id = unique identifier (one element).
👉 class = reusable style/behavior (many elements).



Q.Why do we use meta tags in HTML? (e.g., viewport, charset, description)
Meta tags in HTML provide metadata — information about the web page that isn’t directly visible to users but is important for browsers, search engines, and social platforms.

Some common examples are:

charset → Defines the character encoding (e.g., UTF-8) so the page displays special characters correctly.
viewport → Controls how the page is displayed on mobile devices, making it responsive.
description → Provides a summary of the page content, often shown in search engine results.
keywords → (older use, less relevant now) specifies keywords for SEO.
author → Defines the author of the document.
In short, meta tags help with proper rendering, SEO optimization, accessibility, and responsiveness.

Q.What is the difference between <link> and <a> tag?
The <link> and <a> tags look similar but serve very different purposes:

1.<link> tag

Used to define a relationship between the current HTML document and an external resource.
Most commonly used to link external stylesheets (<link rel="stylesheet" href="style.css">).
Always placed inside the <head>.
It doesn’t create clickable links for users — it’s for the browser.

2.<a> tag (anchor)

Used to create hyperlinks that users can click to navigate to another page, section, or resource.
Example: <a href="about.html">About Us</a>.
Placed in the <body> since it’s part of visible content.

Q.Where should we place CSS and JavaScript files — head or body? Why?
Ans:Placement depends on whether it’s CSS or JavaScript, because they affect page loading differently:
CSS files → should always be placed in the <head> using <link>.

Reason: CSS is needed to style the page before it’s rendered.

If it’s loaded late, the user might see an unstyled or ‘flashy’ page (FOUC — Flash of Unstyled Content).

JavaScript files → usually placed at the end of the <body> or loaded with defer/async.

Reason: JavaScript can block HTML parsing. If scripts are in the <head> without defer/async, they delay page rendering.

Placing them at the end allows the HTML to load first, improving page performance.


Q.What is the diff px ,e m ,% and pixel?
In CSS, px, em, and % are different units used for sizing, and they behave differently:

1.Pixels (px)

Absolute unit — fixed size, does not change relative to anything else.
Example: font-size: 16px; → always 16 pixels, no matter the parent.
Use when you want precise, unchanging dimensions.

2.Ems (em)

Relative unit — relative to the font size of the parent element.
Example: if parent font is 16px, 2em = 32px.
Useful for scalable and responsive text sizing.

3.Percentage (%)

Relative unit — relative to the parent element’s size (width, height, or font size depending on the property).
Example: width: 50%; → half the width of the parent container.
Very useful for fluid layouts and responsiveness.

Q.How do you make a website mobile friendly
Ans.I will use flexbox or media query
===============================================================================================================
Q.What is the difference css grid and flexbox?
Ans:Both CSS Grid and Flexbox are layout systems in CSS, but they are designed for different purposes:
#-Flexbox (Flexible Box Layout)
Designed for one-dimensional layouts (either row or column).
Great for aligning and distributing space among items in a single line.
Examples: navigation bars, buttons in a row, or vertically centering elements.

Supports properties like justify-content, align-items, flex-wrap.

#-CSS Grid

Designed for two-dimensional layouts (rows and columns simultaneously).

Ideal for complex page layouts, like grids of cards or full web page layouts.

Supports properties like grid-template-columns, grid-template-rows, grid-gap.

In short:
👉 Flexbox = 1D (row or column), simpler alignment.
👉 Grid = 2D (rows + columns), complex layout control.

===============================================================================================================
Q.Why do we use semantic element instead of div?
Ans:
We use semantic elements instead of generic <div>s because semantic tags add meaning to the structure of a webpage.

1.Readability: Semantic tags like <header>, <nav>, <article>, and <footer> clearly describe their purpose, making the code easier to read and maintain for developers.

2.Accessibility: Screen readers and assistive technologies can better interpret the page structure, improving accessibility for users with disabilities.

3.SEO Benefits: Search engines use semantic elements to better understand page content, which can improve search rankings.

4.Best Practices: Reduces the overuse of <div>s (also called “div soup”) and leads to cleaner, more organized markup.
