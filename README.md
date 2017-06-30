# Client Friendly Accessibility Guide

This document intends to provide best practices in order to strive for (but not necessarily adhere to) WCAG 2.0 AA Accessibility Criteria. It attempts to avoid getting bogged down in technical details in order to be comprehensible by a wider audience.

This document is a work in progress. None of the authors or contributors, in any way whatsoever, can be responsible for your use of the information contained herein. Please take all steps necessary to ascertain that information contained is correct.


* Ensure that throughout the development stage the designers, front-end developers, and content authors follow the best practice accessibility guidelines set out in this document
* Ensure compliance using the WebAIM WAVE Chrome extension (http://wave.webaim.org/extension/)
* (Optionally – not included in current scope of accessibility) test with the NVDA or JAWS screen reader software to ensure that the site can be accessed by screen reader

Note that it is the responsibility of the customer to ensure that all "standard content" (that is client-authored content entered via a CMS) entered into the site is accessible based on the guidelines set out in this document (specifically note the [PDFs](#pdfs) and the [Language For Content Authors](#language-for-content-authors) sections within in this document).

The remainder of this document summarises our actions under each sectioned heading. These are based on best practices recommended by Vision Australia.

# Table of Contents

1. [Visual Design](#visual-design)
    1. [Colour Contrast](#colour-contrast)
    1. [Link Presentation](#link-presentation)
    1. [Moving Content](#moving-content)
    1. [Zooming](#zooming)
1. [Navigation System](#navigation-system)
    1. [Linking](#linking)
    1. [Buttons](#buttons)
    1. [Best Practice Wording](#best-practice-wording)
    1. [Skip Links](#skip-links)
1. [Content](#content)
    1. [Language For Content Authors](#language-for-content-authors)
    1. [Images](#images)
    1. [PDF Files](#pdf-files)
    1. [Data Tables](#data-tables)
    1. [Forms](#forms)
1. [Developing](#developing)
    1. [CSS](#css)
    1. [JavaScript](#javascript)
1. [Common Components](#common-components)
    1. [Modals](#modals)
    1. [Dropdowns](#dropdowns)
    1. [Carousels](#carousels)
    1. [Autocomplete Fields](#autocomplete-fields)
1. [Mobile Browsing](#mobile-browsing)
1. [Keyboard Usage](#keyboard-usage)
1. [Handy Tools](#handy-tools)



# Visual Design

Ensuring a site is accessible is not only the work of a developer. Care should be taken during the design stage to ensure the service has no barriers to those with visual, hearing, cognitive or motor impairments.

### Colour Contrast
* All body content and text below font size 18pt or 14pt bold will be compliant to a 4.5:1 contrast ratio (this is the difference of contrast between the background and the foreground colours)
* All Large text 14pt bold or 18pt and above will be compliant to a 3.0:1 contrast ratio.
* Logos or text within a logo have no contrast requirement

### Link Presentation
* Anchor links within body text must be underlined by default. The only exception is if the colour contrast of the link is 3.0:1 to the surrounding paragraph text AND 3.0:1 the background colour
* Underline links on mouse hover and keyboard focus

### Moving Content
* Moving content is distracting and is an issue for users with attention deficit disorders
* A stop, pause, or hide, option must be available
* The requirement is that “if it moves automatically, it must stop after 5 seconds, or have a pause/resume button”

### Zooming
* Every browser has inbuilt zoom functionality whether it be a touch devices pinch-to-zoom or +/- magnification buttons on a desktop browser
* All the content on a page must still be legible at 200% zoom. It doesn’t need to be as pretty, but the info must still be there



# Navigation System

### Linking
* You need at least 2 ways of finding a page; ie - Navigation, Sitemap, search, footer links
* For navigation lists, never change the order between pages. All pages need the same navigation
* Some "megamenus" also tab through the sub-level items too - this is a requirement if there’s no other way to access these sub-level pages. However, if you’ve got a landing page which contains these same links, then it’s not necessary to tab through them in the "megamenu"
* Links that direct a user away from the current site (external links) should inform users of this functionality via title, tooltip or content within the anchor (e.g. "link opens in new window")
* This affects both developers as well as content authors who can modify the website via a CMS

### Buttons
* All buttons need descriptive text, they cannot contain icons/symbols alone. The descriptive text doesn't need to be visible, it can be added using the aria-label attribute, eg `aria-label="This will be read by a screen reader"`
* All buttons and links will have both mouse-hover and keyboard-focus states

### Best Practice Wording
* Avoid link text like “click here”, “more”, etc, unless they are understandable within their context
* Avoid using URLs as link text
* Include document format and size, eg “View the Agreement 2016/17 (Word, 389kb)"

### Skip Links
* Used to bypass blocks of content (like the nav)
* You should include this if there is a block of content that is repeated across every page which the user may want to skip to get to the main page content. Not required but is a common practice



# Content

### Language For Content Authors
* Headings should be informative, clear, and identify their sections
* Avoid using UPPERCASE for complete words or sentences
* Reading should reach Flesch-Kincaid Grade level 9 or lower. This can be measured in MS Word

### Images
* The `<img alt="">` element should always include the `"alt"` attribute. If an image contains text (eg, a logo) the alt should contain the text. It’s also recommended to append the word ‘logo’. Logos should ideally be the only images on a site that contain text
* If an image is decorative and serves no additional information to the user it should be ignored by screen readers. To ensure this, give it an empty `alt=""`
* `alt` text must be equivalent and meaningful
* Only use CSS background images for decoration - they are often not displayed in an operating systems' high contrast mode
* Don't use background images for informative content
* Inline SVG's are fine, so long as the SVG content includes a descriptive `title` element with `id` attribute and a matching `aria-labelledby` attribute, eg;
```
<svg aria-labelledby="logo">
    <title id="logo">This will be read by a screen reader</title>
    ...
</svg>
```
https://www.sitepoint.com/tips-accessible-svg/

### PDF Files
* Content authors should note that the Australian Human Rights Commission (AHRC) advises that all PDF documents require an alternative format  which is optimised for accessibility, even if the PDFs are already perfectly accessible
* The alternative format could be html, docx, rtf, or txt, although html is regarded as the most accessible format
* Anchor links to PDF files `<a href="/filename.pdf">` must state within the anchor text that they are links to PDF files. This applies to all file formats (.doc, .xls, etc.)

### Data Tables
* Tables will only be used for tabular data (not layout) and if they are present will be structured correctly and identify row and column headers
* Complex tables should be avoided (tables with nested or merged cells). These cause confusion for screen readers and are difficult to navigate

### Forms
* Ensure forms can be used with keyboard
* Critical text should be avoided as input placeholder text
* Ensure labels are visually close to their inputs
* `<label>` elements will each have a corresponding `<input>` element using the `for` and `id` attributes. This helps screen readers and also allows clicking on the label to focus the input field
```
<label for="login-email" />
<input id="login-email" type="email" />
```
* Recommended, not required: Validation - on submission fail, render a list of error messages at the top of the form, and put keyboard focus on the message
* If time limits are required (eg purchasing tickets), user must have the option to extend the time limit up to 10 times
* If the form comprises several screens, it must include a confirmation page at the end
* Input fields must have the required format as part of the label, eg “dd/mm/yyyy”
* If the form contains a CAPTCHA ensure a text version provided. Eg 2+1=? is more accessible than an image containing text
* Labels will associate explicitly with their corresponding inputs/controls in forms
* Standard form elements (such as dropdown select boxes) will be used where possible
* All forms will use a submit button (no submissions on changing selection/options) as this can be problematic for keyboard users



# Developing

### CSS
* The site will semantically and logically ‘flow’ when CSS has been turned off where possible
* All clickable elements will have hover and focus states
* If content appears on mouseover, then it also must appear on keyboard focus (like tooltips)
* Skip to navigation/content/footer links will be provided to aid users who are using the site via a screen reader


### JavaScript
* Javascript must be enabled in order for the website to function correctly.
* If Javascript is disabled the website will prompt the user to re-enable it.
* When reaching for a JS plugin (eg carousel, autocomplete form, etc) ensure that the documentation mentions what kind of accessibility features are built-in. Avoid those which fail to provide these features



# Common Components

### Modals
* Given the complexity of making modal windows accessible they will generally be avoided if possible.
* If a modal is necessary, a number of features need to be built to make them accessible;
 * When the modal opens, keyboard focus should be put on the first element within the modal, usually a heading (using with `tabindex="0"`), or input field, button, etc.
 * Modals should be tab-locked, meaning that if a user tabs past the last tabbable element within the modal, tabbing should return to the first tabbale element within the modal. 

Further reading at [https://developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_dialog_role)

### Dropdowns
* Best practice is to avoid using custom dropdowns and to stick with the browser default using `<select>` and `<option>` elements. These are accessible out of the box and don't require any additional coding
* They also use the default styling of the browser or device which the user will already be familiar with

### Carousels
* Each slide of the carousel should be rendered as a list in the DOM
* Additional hidden text will be included to aid screen readers
    * Heading “Carousel”
    * Button text “slide 1”, “slide 2”
* Carousels should avoid auto-playing
* If the carousel must auto-play, each slide should have a minimum 5 second delay between rotations and provide a pause/resume button

### Autocomplete fields
* On focus of an autocomplete field, it should trigger the screen reader to read helpful information on how to use the feature. 
    * "Type at least 3 characters to begin searching"
    * "Use up/down on your keyboard to navigate the results"
* The component should also trigger the screen reader to notify the user that a search is currently in progress. If the site uses a visual indicator (often a spinner) then this can be accomplished by adding a `aria-live="polite"` attribute to the a spinner element

### Audio / Video
* Provide text alternative for non-text content
* Don’t play audio automatically
* All examples of non-text text must have a text alternative. Videos must have transcriptions. Embedded YouTube videos include this feature
* A video player should be workable by keyboard and controls/text should be read by screen readers



# Mobile browsing
* Best practice is to develop responsive sites rather than a separate mobile site - this ensures that if the desktop site has been developed following WCAG2.0 techniques, then mobile inherits them for free
* Mobile sites and apps are covered by the DDA and NTS - they must be accessible. All relevant WCAG 2.0 techniques must be applied to mobile sites
* The user must be able to zoom to a minimum 200%
Multimedia
* Captions are subtitles that convey important/useful information which a deaf user would otherwise miss out on.  "Sound of police sirens in background" would be helpful for a deaf user to understand the context of a video. They contain spoken as well as other auditory elements and are an accessible alternative to audio content for deaf users, and must be synchronised and equivalent
* Transcripts are text which represents the spoken words. Basically a subtitle. YouTube can do automatic spoken word transcripts (not always accurate, but better than nothing). It does not do captions
* Both transcripts and captions are required
* Users must be able to stop audio that plays automatically for longer than 3 seconds. Or it must stop by itself after 3 seconds. Or you need a pause button



# Page Structure & Semantics

* A semantic code structure will be employed for ease of use for screen reading technologies
* `<table>` will not be used for layout
* The main title for a given page should be within a `<h1>` element
* It is still best practice to ensure only one `<h1>` element appears per page
* Visual layout context - “use the search bar on the right” or "click the button below" is hard to understand for a screen reader user

# Keyboard Usage

* The site will be fully tested using a keyboard only (without mouse input) to ensure all information is still reachable
* Tabbing through the site will follow a logical order (left to right, top to bottom)




# Handy Tools
* tota11y 
* http://pa11y.org/
