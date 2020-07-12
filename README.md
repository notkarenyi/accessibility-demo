# Accessibility on the Web

## Overview

Welcome to Karen's introduction to accessibility on the web! After this workshop, you should have a basic understanding of what kinds of needs we should be meeting as web developers. You should be able to use your familiarity with accessibility guidelines, in conjunction with some convenient tools, to evaluate websites on whether those needs are being fulfilled.

This workshop assumes an intermediate working knowledge of HTML and CSS. However, it's less about coding, and more about seeing the tools you've learned in a new way. Don't worry if you aren't familiar with some of this code yet - most of what is mentioned here has been introduced by Leo and Matt already, but these ideas are important to keep in mind when you start to use more in-depth HTML and CSS.

## Table of Contents

* [What Does Accessibility Involve?](#what-does-accessibility-involve)
  <!-- * [Josie Bruin's Story](#josie-bruins-story) -->
* [Appearance](#appearance)
  * [Fonts and Font Sizes](#fonts-and-font-sizes)
  * [Zooming In](#zooming-in)
  * [Color Contrast](#color-contrast)
* [Supporting Screen Readers](#supporting-screen-readers)
  * [Semantic HTML](#semantic-html)
  * [Tabindex](#tabindex)
  * [Language Specification](#language-specification)
* [Images and Videos](#images-and-videos)
  * [Alt text](#alt-text)
  * [Transcripts](#transcripts)
  * [Autoplay](#autoplay)
* [Animations](#animations)
* [Content Reading Level](#content-reading-level)
* [Conclusion](#conclusion)
* [Accessibility Checkers](#accessibility-checkers)
* [Further Reading](#further-reading)
* [Reference Links](#reference-links)

## What Does Accessibility Involve?

What comes to mind when you think of the word "disabled" or the word "accessible"? Our assumptions about these words can be wrong or partially wrong, and in order to create the best experience on our websites, we should be comfortable with constantly adapting to the highest standards for accessibility. (This tends to be a theme across computer programming.) 

For most web developers and many users, poor accessibility features are an inconvenience at worst or even unnoticeable at best. But for many internet users, these features can make or break their experience with your website. These users experience a range of needs, including colorblindness, use of a screen reader (for people with visual impairments, people with learning disabilities, etc.), poor vision (for the elderly, people with visual impairments, etc.), susceptibility to seizures, and more. Why is it important to pay attention to all these needs, you ask?

1. Help people with all kinds of needs use and enjoy your website
1. Increase traffic and user satisfaction
1. Everyone benefits from accessible websites

Each website element that you design or create will be used by all kinds of different people. So, we need to think about how these parts can meet the needs of our users. Many web developers (like me) love the design part of web development, but sometimes we get too caught up in what looks "cool" and not what is actually legible or usable. Good web design, like any kind of design, is a balance of both aesthetic and function.

<!--
### Josie Bruin's Story

To start thinking about what I mean by "different needs," let's take an example of one hypothetical user's experience. 

Of the two sites below, which is better?

![]()
![]()

Without knowing how users can interact with the websites, it's hard to say for sure. But let's assume that Josie Bruin, who uses a screen reader because she is legally blind, visits Website A. If Website A uses semantic tags, alt text, and language specification, and Website B does not, then Josie's experience on Website A is going to be much better than her experience on Website B. 

But what do all these terms mean? Good question--we're ready to dive into the foundations of accessibility.
-->

## Appearance
One of the most straightforward places to start is the visual appearance of your website, since most of us are familiar with what's "good" versus what's not so good. 

### Fonts and Font Sizes

Have you ever visited a mobile or desktop website with an uncomfortably small or weirdly large font? Pretty annoying, right? Fortunately, someone was smart enough to come up with standard font sizes for mobile and desktop:

```css
/* CSS file */
  @media screen and (max-width: 768px) {
    font-size: 16px;
  }
  
  @media screen and (min-width: 769px) {
    font-size: 18px;
  }
```
Fonts can still look too small or too large at these sizes, so adjust as needed. 

```css
/* CSS file */
  .serif {
    font-size: 16px;
    font-family: Times New Roman;
  }
  
  .sans-serif {
    font-size: 16px;
    font-family: Helvetica;
  }
```

On the same note, do not use display (aka fancy) fonts in body text. This is painful for everyone. Micro typography lesson: serif fonts like Times New Roman are often used in body text, because serifs aid the eye in reading text. (Serifs are the little hooks on the ends of letters, like the curve on the ends of the Ts in this document.) Sans serif fonts like Arial are also popular because they look sleek and modern. A good rule of thumb is to copy a paragraph of an article into your chosen font, and see if you can easily scan the paragraph. If not, it's probably not a good choice for your website.

### Zooming In

Users with visual impairments, such as the elderly, often need to zoom in on 16px or 18px text in order to be able to read clearly. As you're developing your website, try zooming in up to 200% and see if the website is still usable. If elements are jumping around or hiding text at this zoom level, that's bad news and we should take steps to fix that. 

Avoid making the user have to scroll horizontally--the text should wrap to fit the window size. `whitespace: normal` should be the default, but if text is not wrapping correctly, try explicitly setting this property.

```css
/* CSS file */
p {
  whitespace: normal;
}
```

### Color Contrast 

Color blindness affects 1 in 12 men and 1 in 200 women worldwide. Use a color-blindness checker to simulate how your website would look to someone with color blindness. 

Always use a color-contrast checker to ensure that your text and visual elements meet a good contrast ratio, in order to help people read and see content clearly. Here's one of the most common examples of bad color contrast that I see around the web:

```css
/* CSS file */
  .bad {
    color: #ffffff
    background-color: #fee851
  }
  
  .good {
    color: #000000
    background-color: #fee851
  }
```

![image]()
![image]()

Be very careful when placing text over images. In fact, avoid placing text over images when the text is essential to understanding or using the website.

![image]()

## Supporting Screen Readers

This is probably the most important topic covered in this workshop - consideration of screen readers is almost impossible to spot visually. The following are invisible to the average user, but can make or break the site experience for someone using a screen reader.

### Semantic HTML

HTML has special tags for common structural elements on a website, from `button` to `article` to `footer`. These exist for a reason! Screen readers rely on these tags to  navigate websites. You'll see that there's no visual difference between using many of these tags as opposed to a `div`, which is why I say that screen readers' needs are often invisible. But using the wrong semantic tags has a very real effect on potential users.

Did you know that `h1`, `h2`, etc. are actually semantic tags? It's bad practice to use heading tags to control font size and weight - that's what CSS is for! Only use heading tags as organizational tools for your website, such as making the page title an `h1`, and making subtitles `h2`.

```html
<!-- bad -->
<div class = "nav">
 <a href= "/home">
 <a href= "/about">
</div>
   
<!-- good -->
<nav>
  <a href= "/home">
  <a href= "/about">
</nav>
```

### Tabindex

Tabindex refers to tabbing through the buttons or links (or "focusable" elements) on a page using the Tab key on the keyboard. This feature can be used by people navigating by keyboard, as well as people using screen readers. Because of this feature, always organize links and button in a meaningful order.

This also means that button and link text should be descriptive. Avoid "click here" and other phrases without context, since they can be confusing to people who are only reading the links on a site.

```html
<!-- HTML file -->

<!-- bad -->
<p>
  Create an account below!
</p>
<button>
     Click here
</button>

<!-- good -->
<button>
     Create account
</button>
```

### Language Specification

Screen readers are preprogrammed voices that read page content for users. They don't automatically know what language a website is written in (by language I mean human language, not programming language), which can result in some awkward pronunciation for foreign-language content. Specify the main language of a page using the appropriate language code:

```html
<!-- HTML file -->
<html lang = "en">
  <!-- Your website goes here -->
</html>
```
## Images and Videos

Embedded media can be difficult to consume for many populations and for many reasons. Visual elements usually require a text alternative.

### Alt text

Alt text is displayed when an image file fails to load. It is also read by screen readers (see [Supporting Screen Readers](#supporting-screen-readers)). 

Always, always, always provide alt text for images that have semantic meaning. For example: a decorative background image of a stripe pattern probably does not need alt text, but a graph of average daily cups of coffee drunk by university students probably does. A good rule of thumb is if the image adds context to the page that isn't already present in text, then alt text is needed. If nothing new is added, then `alt = ""` is okay. 

```html 
<!-- HTML file -->
 <img href = "/images/graph.jpg" alt = "Average daily cups of coffee drunk by university students. Source: College University, 2008.">
```

![image]()

Writing good alt text takes a little thought. The same image might have different alt text in different contexts. Think of it as similar to a caption, only as brief as possible. For example, do not write "Image of..." or "Graphic of..." since it's usually obvious what the element is, even to screen readers. However, "Painting of..." may be used since the user would not know this if the image had failed to load. 

Be accurate when describing its content--don't provide information that is not present in the media. 

Write alt text for icons in the same way you would for images, since some icons (such as file-type icons) add context, while decorative icons do not.

The only instance in which alt text can be redundant with surrounding text is when an image functions as a link. In that case, the alt text must be present to act as a link, so an empty `alt` attribute is not allowed. Again, do not write "Link to..." as it is clear that the image is a link.

Videos do not support `alt` attributes. Use `title` instead or provide an external link to the video. 

### Transcripts 

People with hearing impairments and English language learners often have difficulty following audio or video elements. Others also find transcripts and subtitles useful in noisy environments or when skipping through a media element to find a specific part. 

WebVTT files are the standard for synchronized closed captions. Include these with the `track` tag. Specify `kind = subtitle` and `label` using the appropriate language. 

`srclang` uses a language code to specify the type of data used (see [Language Specification](#language-specification)), while `label` is meant to help the user choose the correct subtitles.

Include the `controls` attribute to allow access to volume controls, video pause and playback, existing subtitles and transcripts, and more.

```html
<!-- HTML file -->
<video controls width = "500">
  <source src = "/resources/video.mp4" type = "video/mp4">
  <track src = "/resources/english.vtt" kind = "subtitles" srclang = "en" label = "English">
  <track src = "/resources/spanish.vtt" kind = "subtitles" srclang = "sp" label = "Spanish">
</video>
```

### Autoplay

Disable autoplay for embedded videos. Autoplay can be disorienting for users, as well as annoying (have you ever tried to find that one tab that randomly starts playing music? Yeah).

The `autoplay` attribute for `video` tags is an "opt-in" feature. If for some reason this attribute is present in your code, you have to delete it in order to disable autoplay. Setting `autoplay = false` will not work.

Similarly, allow users to pause and navigate slideshows - it can be distracting to see a constantly sliding slideshow when you're trying to focus on a different part of the page. Plus, many slideshows move too fast for some users to read each slide. 

Since slideshows are usually made using JavaScript, we won't cover how to do it here.

## Animations

Many people are prone to seizures and can be harmed by websites with too much animation. This means limiting the number of GIFs, and avoiding flashing elements at all costs (the w3 standard is three flashes or less per second).

## Content Reading Level 

Although web developers often aren't responsible for writing site content, 1) they can be and 2) they are often asked for feedback on content.

English language learners, people with reading or language disabilities, and others are affected by unclear or complicated language. The standard for general-audience websites is to use language at an 8th-grade reading level. Avoid the passive voice and avoid convoluted sentence structure. Think about what words or phrases can be replaced with simpler ones. 

Correct spelling and grammar help make sure that everyone is on the same page and facilitates easy reading.

## Conclusion

It might seem that there are suddenly a million things to worry about that you didn't think about before. Don't sweat it if you can't remember everything. What's important is to start looking at websites you use and the websites you create with a critical eye, asking: "How does this meet accessibility guidelines?", "How might this website be hard for some people to use?", and "What can I do to make my website functional and enjoyable for everyone?" Once you've identified a problem, you can always Google the solution to jog your memory.

As a review, here are the topics we've covered:
* Fonts and font sizes
* Accommodating zooming in
* Color contrast
* `alt` and `track`
* Disabling `autoplay`
* Limiting animation and flashing effects
* Semantic HTML
* Tabindex and labeling links and buttons
* Content reading level

One final note: accessibility should not be an afterthought. You'll make it easier for yourself and your users if you think about it early on: when you're picking your fonts and color palette, when you're creating elements in HTML, and when you're structuring the flow of your website. Keep learning and improving user experience for all audiences on all websites :) 

Want to put your new knowledge into practice? Start out by turning a critical eye on your [portfolio task](https://github.com/uclaacm/learning-lab-crash-course-su20/blob/master/task-1-portfolio/README.md) from earlier in this course, as well as any other websites you may have made. Use the tools below to help you make your website beautiful *and* accessible! 

## Accessibility Checkers

Never rely on a machine to "check off" accessibility requirements. (See [this blog post](https://www.matuzo.at/blog/building-the-most-inaccessible-site-possible-with-a-perfect-lighthouse-score/) for an example of how machines can make mistakes sometimes.) But I highly recommend saving these resources for later--I use them all the time and they are great aids for checking how your website measures up. 

* [WAVE browser extension](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh)
* [w3 evaluation tools](https://www.w3.org/WAI/ER/tools/)
* [Color blindness checker](http://color-blindness.com/coblis-color-blindness-simulator/)
* [Color contrast checker ](http://webaim.org/resources/contrastchecker/)
* [Accessibility checker](http://wave.webaim.org)
* [Hemingway reading level checker](http://www.hemingwayapp.com/)

## Further Reading

Want to learn about AA versus AAA standards, input errors, and more? Check out these comprehensive accessibility guides from top-tier institutions.

* [Elsevier guidelines](https://www.elsevier.com/about/policies/accessibility)
* [Yale guidelines](https://usability.yale.edu/web-accessibility/articles)
* [w3 guidelines](https://www.w3.org/TR/WCAG21)

## Reference Links

These articles will save you some googling on the topics we've covered today. (Mozilla Developer Network has been abbreviated as MDN.)

* [Semantic HTML (MDN)](http://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
* [Semantic HTML flowchart (HTML5 Doctor)](http://html5doctor.com/downloads/h5d-sectioning-flowchart.png)
* [Tabindex (MDN)](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex)
* [Hyperlink accessibility & tab index (Yale)](https://usability.yale.edu/web-accessibility/articles/links)
* [Font size guidelines (Learn UI)](https://learnui.design/blog/mobile-desktop-website-font-size-guidelines.html)
* [Video attributes (MDN)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)
* [WebVTT files (MDN)](https://developer.mozilla.org/en-US/docs/Web/API/WebVTT_API)
* [Track tag for subtitles (w3)](https://www.w3schools.com/tags/tag_track.asp)
* [Alt text (WebAIM)](https://webaim.org/techniques/alttext/)
