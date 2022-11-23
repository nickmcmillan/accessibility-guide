# Client Friendly Accessibility Guide

This document intends to provide best practices in order to strive for (though not necessarily adhere to) WCAG 2.0 AA Accessibility Criteria. It avoids technical detail in order to be comprehensible to a wider audience.

This document is a work in progress. None of the authors or contributors, in any way whatsoever, can be responsible for your use of the information contained herein. Please take all steps necessary to ascertain that information contained is correct.

It's recommended that all team members (though specifically designers, front-end developers, content authors) follow the best practice accessibility guidelines set out in this document.

Note that it is the responsibility of the product owner to ensure that all "standard content" (that is client-authored content entered via a CMS) entered into the site is accessible based on the guidelines set out in this document (specifically note the [PDF Files](#pdf-files) and the [Language For Content Authors](#language-for-content-authors) sections within in this document).

# Table of Contents

1. [Visual Design](#visual-design)
    1. [Colour Contrast](#colour-contrast)
    1. [Buttons](#buttons)
    2. [Link Presentation](#link-presentation)
    3. [Moving Content](#moving-content)
    4. [Zooming](#zooming)
    5. [Geospacial Data](#geospacial-data)
2. [Navigation System](#navigation-system)
    1. [Linking](#linking)
    2. [Skip Links](#skip-links)
3. [Content](#content)
    1. [Language For Content Authors](#language-for-content-authors)
    2. [Images](#images)
    3. [PDF Files](#pdf-files)
    4. [Data Tables](#data-tables)
    5. [Forms](#forms)
    5. [Authentication](#authentication)
4. [Developing](#developing)
    1. [HTML](#html)
    2. [CSS](#css)
    3. [JavaScript](#javascript)
5. [Common Components](#common-components)
    1. [Modals](#modals)
    2. [Form Dropdowns](#form-dropdowns)
    3. [Carousels](#carousels)
    4. [Autocomplete Fields](#autocomplete-fields)
    5. [Date Pickers](#date-pickers)
    6. [Audio / Video](#audio--video)
6. [Mobile Browsing](#mobile-browsing)
7. [Handy Tools](#handy-tools)



# Visual Design

Ensuring a site is accessible is not only the work of a developer. Care should be taken during the design stage to ensure the service has no barriers to those with visual, hearing, cognitive or motor impairments.

### Colour Contrast
* All body text and text below font size 18px or 14px bold will be compliant to a 4.5:1 contrast ratio (this is the difference of contrast between the background and the foreground colours)
* All Large text 14px bold or 18px and above will be compliant to a 3.0:1 contrast ratio
* Note that logos or text within a logo have no contrast requirement

### Buttons
* All buttons need descriptive text; they cannot contain icons/symbols alone. The descriptive text doesn't need to be visible. It can be added using the aria-label attribute, eg `aria-label="This will be read by a screen reader"`
* All buttons and links need both pointer-hover and keyboard-focus states
* Focused v unfocused state colour changes must pass contrast of >= 3:1
* If you decide to do an outline on focus, aim for a width of >= 2px. The colour of the focus outline must:
  1) Be >=3:1 with the colour it replaces
  1) Be >=3:1 with the inside colour
  1) Be >=3:1 with the outside colour


### Link Presentation
* Anchor links within body text must be underlined by default. The only exception is if the colour contrast of the link is 3.0:1 to the surrounding paragraph text AND 3.0:1 the background colour
* Underline links on mouse hover and keyboard focus
* Targets must be minimum 24x24px (AA) or 44x44 (AAA) but try aim for the larger size for better usability. Inline elements are an exception.

### Moving Content
* Moving content is distracting and is an issue for users with attention deficit disorders, therefore a stop, pause, or hide option must be available
* Generally the requirement is that “if it moves automatically, it must stop after 5 seconds, or have a pause/resume button”
* Avoid flashing content. If it needs to be on your website, ensure it does not flash more than 3 times in any 1-second period. For photosensitive epileptic users it can set off seizures

### Zooming
* Every browser has inbuilt zoom functionality whether it be a touch devices pinch-to-zoom or +/- magnification buttons on a desktop browser. This functionality should not be disabled
* All the content on a page must still be legible at 200% zoom. It doesn’t need to be as pretty, but the info must still be there

### Geospacial Data
* Geospacial data is data that relates to a specific location on earth. Think maps and routing information
* Any information contained within a map (like the Google Maps JS API) requires a text alternative. Think about how Google Maps does this with the step by step directions list
* Communicating information via colours can interfaces inaccessible to colour blind users. Don’t rely on colours alone if the colours are similar, use figures or patterns as well. Think about online flight booking interfaces; typically seats are both colour-coded as well as include a symbol or pattern within each seat to aid colour blind users

### Consistency of location for support channels
* Support channels (think phone number, contact form, opening hours, chatbot, social media links) should be positioned consistently in the layout across all pages.

# Navigation System

### Linking
* You need at least 2 ways of navigating to a page, ie - navigation menu, sitemap, search results, footer links, etc
* For navigation menus, never change the sort order between pages. All pages need the same navigation system
* Some "megamenus" also tab through the sub-level items too - this is a requirement if there’s no other way to access these sub-level pages. However, if you’ve got a section landing page which contains these same links, then it’s not necessary to tab through them in the "megamenu". Example [Auspost](https://auspost.com.au/) you can tab through the primary navigation items, but the megamenu links are only accessible for mouse users - however this is OK because the sub-level page links within the megamenu are also available on each section landing page
* Links that direct a user away from the current site (external links) should inform users of this functionality via title, tooltip or content within the anchor (e.g. "link opens in new window"). This requirement concerns both developers as well as content authors who can modify the website via a CMS

### Skip Links
* These are hidden links that are only accessible via keyboard and are used to bypass blocks of content (like the nav)
* Most often these are "skip to content" and "skip to navigation"
* You should include this if there is a block of content that is repeated across every page which the user may want to skip to get to the main page content. While not required this is a recommended and common practice


# Content

### Language For Content Authors
* Headings should be informative, clear, and identify their sections
* Avoid using UPPERCASE for complete words or sentences
* Avoid link text like “click here”, “more”, etc, unless they are understandable within their context
* Avoid using URLs as link text
* Include document format and size, eg “View the Agreement 2016/17 (Word, 389kb)"
* Reading should reach Flesch-Kincaid Grade level 9 or lower. This can be measured in MS Word
* Content must not have a dependency on the visual layout context - eg “use the search bar on the right” or "click the button below" is hard to understand for a screen reader user. Not all users can perceive location
* Don’t use use ASCII characters out of context. For instance ‘II’ might look like a pause icon, but it is actually two capital “i” letters, and will be read as such. Square root icon might look like a tick but it isn’t

### Images
* The `<img alt="">` element should always include the `"alt"` attribute
* If an image contains text (eg, a logo) the alt should contain the text. It’s also recommended to append the word ‘logo’. Logos should ideally be the only images on a site that contain text
* If an image is decorative and serves no additional information to the user it should be ignored by screen readers. To ensure this, give it an empty `alt=""`
* `alt` text must be equivalent and meaningful
* Only use CSS background images for decoration - they are often not displayed in an operating systems' high contrast mode
* Complex images and diagrams need a longer description. For instance if a chart is inside an image, then there must be accompanying text on the page that describes the information within the image
* Don't use background images for informative content
* Inline SVG's are OK so long as the SVG content includes a descriptive `title` element with `id` attribute and a matching `aria-labelledby` attribute, eg;
```
<svg aria-labelledby="logo">
    <title id="logo">This will be read by a screen reader</title>
    ...
</svg>
```
Read more about SVG's and accessibility  [here](https://weboverhauls.github.io/demos/svg/) and
[here](https://www.sitepoint.com/tips-accessible-svg/).

### PDF Files
* Content authors should note that the Australian Human Rights Commission (AHRC) advises that all PDF documents require an alternative format which is optimised for accessibility, even if the PDFs are already perfectly accessible. The alternative format could be html, docx, rtf, or txt, although html is regarded as the most accessible format
* Anchor links to PDF files `<a href="/filename.pdf">` must state within the anchor text that they are links to PDF files. This applies to all file formats (.doc, .xls, etc.)

### Data Tables
* Tables will only be used for tabular data (not layout) and should be structured correctly and identify row and column headers
* Complex tables should be avoided (tables with nested or merged cells). These cause confusion for screen readers and are difficult to navigate
* The `scope` attribute identifies whether a `<th>` is a column header or a row header, eg: `<th scope="col">Name</th>` for column headers, and `<th scope="row">Jackie</th>` for row headers

### Forms
* A user must be able to fill out a form using only the keyboard
* Critical text should be avoided as "placeholder" text
* Ensure labels are visually close to their inputs
* `<label>` elements will associate explicitly with their corresponding input/controls. This helps screen readers and also allows clicking on the label to focus the matching input field, eg;
```
<label for="login-email" />
<input id="login-email" type="email" />
```
* Recommended though not required: Validation - on submission fail, render a list of error messages at the top of the form, and put keyboard focus on the message
* If time limits are required (eg. purchasing tickets) the user must have the option to extend the time limit up to 10 times
* If the form comprises several screens, it must include a confirmation page at the end
* Input fields must have the required format as part of the label, eg “dd/mm/yyyy”
* If the form contains a CAPTCHA ensure a text version provided. Eg 2+1=? is more accessible than an image containing text
* Standard form elements (such as dropdown `<select>` boxes) will be used where possible, and plugins which enable custom styling should be avoided
* All forms will use a submit button (forms should not submit upon changing selection/options) as this can be problematic for keyboard users
* Avoid redundant entry. A user shouldn't have to enter the same information twice. For example; some checkout forms have a checkbox labeled "Shipping address is the same as billing address". This is a great solution to avoid reduntant entry.

### Authentication
* Make it possible to authenticate without remembering, transcribing, or manipulating any information. What does this mean:
* If you have a 2FA input field, use the attribute `autocomplete="one-time-code"` which should allow the user to autofill the field when the 2FA code lands in their SMS inbox
* Allow biometrics to auto-fill login forms. Most smartphones have these built in. This saves the user having to remember their credentials.
* Let password managers and browser auto-fill do their thing. Ensure that input fields have the appropriate attributes to help facilitate this.
* Don't prevent the user from copying or pasting in the password field.
* Consider an OAuth login method (like login with Google, etc).
* 

# Developing

### HTML
* A semantic code structure will be employed for ease of use for screen reading technologies. Focus order will be logical. `tabindex` should be avoided
* The main title for a given page should be within a `<h1>` element. All headings will use an appropriate `<h*>` element
* It is still best practice to ensure only one `<h1>` element appears per page
* The site will be fully tested using a keyboard only (without mouse input) to ensure all information is still reachable
* Tabbing through the site will follow a logical order (left to right, top to bottom)
* The `<table>` element will not be used for layout
* ARIA landmark roles (such as 'banner', 'article', 'main', etc) are not a requirement and are not strictly needed. Recommendation is to just use HTML5 elements instead

### CSS
* The site will semantically and logically ‘flow’ when CSS has been turned off where possible
* If content appears on mouseover (such as a tooltip) then a version of the content should also be made available for a keyboard-only user. Remember that all content must be the same regardless of how the user is receiving it

### JavaScript
* In almost all cases JS must be enabled in order for the website to function correctly
* If Javascript is disabled the website will prompt the user to re-enable it
* As a developer when reaching for a JS plugin (eg carousel, autocomplete form, etc) ensure that the documentation mentions what kind of accessibility features are built-in. Avoid those which fail to provide such features


# Common Components

### Modals
* Modal windows are generally inaccessible and should be avoided
* If a modal is necessary, a number of features need to be built to make them accessible;
 * When the modal opens, keyboard focus should be put on the first element within the modal, usually a heading (using with `tabindex="0"`), or input field, button, etc.
 * Modals should be tab-locked, meaning that if a user tabs past the last tabbable element within the modal, tabbing should return to the first tabbable element within the modal
 * Upon closing the modal (with a close button or hitting the ESC key) focus should be returned to the element which activated the modal
 * Use `aria-hidden="true"` for all other content on the page while the modal is open (so the screen reader ignores everything below the modal)

Further reading about accessible modals [here](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_dialog_role)

### Form Dropdowns
* Best practice is to avoid customising the style of dropdowns (typically achieved using JS plugins) and to stick with the browser default using `<select>` and `<option>` elements. These are accessible out of the box and don't require any additional coding
* Browser default dropdowns also use the default styling of the browser or device which the user will already be familiar with

### Carousels
* Each slide of the carousel should be rendered as a list item in the DOM and should not be obscured or hidden for a keyboard-only user
* Additional hidden text should be included to aid screen readers
    * Heading “Carousel”
    * Button text “slide 1”, “slide 2”
* Carousels should avoid auto-playing
* If the carousel must auto-play, each slide should have a minimum 5 second delay between rotations and provide a pause/resume button

### Autocomplete fields
* On focus of an autocomplete field, it should trigger the screen reader to read helpful information on how to use the feature. 
    * "Type at least 3 characters to begin searching"
    * "Use up/down on your keyboard to navigate the results"
* The component should also trigger the screen reader to notify the user that a search is currently in progress. This can be accomplished by adding a `aria-live="polite"` attribute on a descriptive content element

### Date Pickers
* It doesn’t matter if a JS date picker widget is not accessible so long as the user can enter the date as plain text into an accompanying text input field. The point is that the user can still successfully enter a date

### Audio / Video
* Don’t play audio automatically, no one wants that
* All examples of non-text text must have a text alternative. Videos must have transcriptions
* A video player should be workable by keyboard and controls/text should be read by screen readers
* Captions are subtitles that convey important/useful information which a deaf user would otherwise miss out on. "Sound of police sirens in background" would be helpful for a deaf user to understand the context of a video. They contain spoken as well as other auditory elements and are an accessible alternative to audio content for deaf users, and must be synchronised and equivalent
* Transcripts are text which represents the spoken words. Basically a subtitle. YouTube can do automatic spoken word transcripts (not always accurate, but better than nothing). It does not do captions
* Both transcripts and captions are required
* Users must be able to stop audio that plays automatically for longer than 3 seconds. Or it must stop by itself after 3 seconds. Or you need a pause button


# Mobile browsing

* Develop a responsive site rather than a separate mobile site - this ensures that if the desktop site has been developed following WCAG2.0 techniques, then mobile inherits them for free
* Mobile sites and apps are covered by the DDA and NTS - they must be accessible. All relevant WCAG 2.0 techniques must be applied to mobile sites


# Handy Tools
It's impossible for an automated tool to test against all of the requirements set out in this document, but it can't hurt to use them anyway and often they're super helpful for identifying things like colour contrast issues or DOM issues such as multiple `<h1>` elements.
* [tota11y](http://khan.github.io/tota11y/)
* [WebAIM WAVE Chrome extension](http://wave.webaim.org/extension/)
* [HTML CodeSniffer](http://squizlabs.github.io/HTML_CodeSniffer/)
