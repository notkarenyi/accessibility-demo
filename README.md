# Accessibility on the Web

## Overview

Welcome to Karen's introduction to accessibility on the web! After this workshop, you should have a basic understanding of what kinds of needs we should be meeting as web developers, and how to look at a website from multiple angles using your knowledge of accessibility guidelines, as well as a few useful tools. 

For most web developers and many users, poor accessibility features are an inconvenience at worst or even unnoticeable at best. But many internet users experience a range of needs that limit what you may think of as "normal" web usage. These needs may include colorblindness, use of a screen reader (for blind people, people with motor disabilities, etc.), poor vision (for the elderly, people with visual impairments, etc.), susceptibility to seizures, and more. Why is it important to pay attention to all these needs?

1. Help people with all kinds of needs use and enjoy your website
1. Increase traffic and user satisfaction
1. Make the experience better for everyone else as well

What comes to mind when you think of the word "disabled" or the word "accessible"? Our assumptions about these words can be wrong or partially wrong, and in order to create the best experience on our websites, we should be comfortable with constantly adapting to the highest standards for accessibility. (This tends to be a theme across computer programming.) Everyone benefits from websites that follow accessibility guidelines. 

Here, we'll cover the basics (aka, bare minimum) of accessibility. Don't worry if you aren't familiar with some of this code yet--most of what is mentioned here has been introduced by Leo and Matt already, but some ideas are important to keep in the back of your mind for when you start to use more in-depth HTML and CSS.

## Table of Contents

* [Which Site is Worse?](#which-site-is-worse)
* [What Does Accessibility Involve?](#what-does-accessibility-involve)
* [Appearance](#appearance)
 * [Fonts and Font Sizes](#fonts-and-font-sizes)
 * [Zooming In](#zooming-in)
 * [Color Contrast](#color-contrast)
* [Images and Videos](#images-and-videos)

## Which Site is Worse?

## What Does Accessibility Involve?

Every part of your website that you design or create will be used by all kinds of different people. So, we need to think about how these parts can meet the needs of our users. Many web developers (like me) love the design part of web development, but sometimes we get too caught up in what looks "cool" and not what is actually legible or usable. Good web design, like any kind of design, is a balance of both aesthetic and function.

Now we're ready to dive into the basic foundations of accessibility!

## Appearance
One of the most straightforward places to start is the visual appearance of your website, since most of us are familiar with what's "good" versus what's not so good. 

### Fonts and Font Sizes

Have you ever visited a mobile or desktop website with an uncomfortably small or weirdly large font? Pretty annoying, right? Fortunately, someone was smart enough to come up with standard font sizes for mobile and desktop:

```css
  @media screen and (max-width: 768px) {
    font-size: 16px;
  }
  
  @media screen and (min-width: 769px) {
    font-size: 18px;
  }
```
Fonts can still look too small or too large at these sizes, so adjust as needed. 

```css
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

Users with visual impairments, such as the elderly, often need to zoom in on 16px or 18px text in order to be able to read clearly. As you're developing your website, try zooming in up to 200% and see if the website is still usable. If elements are jumping around or hiding text at this zoom level, that's bad news and we should take steps to fix that. Avoid making the user have to scroll horizontally--the text should resize within the window.

```
```

### Color Contrast 

Another very important consideration in terms of appearance is color contrast. Always use a color-contrast checker to ensure that your text meets a good contrast ratio. Here's one of the most common examples of bad color contrast that I see around the web:

```css
  .bad {
    color: #ffffff
    background-color: #fee851
  }
  
  .good {
    color: #000000
    background-color: #fee851
  }
```

Similarly, use a color-blindness checker to simulate how your website would look to someone with color blindness. Fun fact: color blindness affects 1 in 12 men and 1 in 200 women worldwide. 

Be very careful when placing text over images. In fact, avoid placing text over images when the text is essential to basic understanding or function of the website.

```
```

## Images and Videos

Always, always, always provide alt text for images that have semantic meaning on your website. For example: a decorative background image of a stripe pattern probably does not need alt text, but a graph of average daily cups of coffee drunk by university students definitely does.

```html 
<!-- HTML file -->
 <img href="/images/graph.jpg" alt="Graph of average daily cups of coffee drunk by university students. Source: College University, 2008.">
```

If possible, provide closed captions or transcripts for embedded videos. 

```html

```

Disable autoplay for embedded videos. Auto-play can be disorienting for users, as well as annoying (have you ever tried to find that one tab that randomly starts playing music? Yeah).

```html
```

## Animations

Many people are prone to seizures and can be harmed by websites with too much animation. This means limiting the number of GIFs, and avoiding flashing elements at all costs (the w3 standard is three flashes or less per second).

Allow users to pause and navigate slideshows--it can be distracting to have a constantly sliding slideshow when you're trying to focus on a different part of the page. Plus, many slideshows move too fast for some users to read each slide.

```html
```

Also, complex scrolling (parallax scrolling is a popular one that developers should be careful with) can be disorienting.

## Supporting Screen Readers

This is probably the most important topic covered in this workshop--not because blind people and people with learning disabilities are the most important, but because consideration of screen readers is the hardest to spot. The following are invisible to the average user, but can make or break the site experience for a screen-reader user.

### Semantic HTML

You might have seen Matt and Leo use the `nav` tag or other interesting tags before. HTML has special tags for common structural elements on a website, from `nav` to `article` to `footer`. These exist for a reason! Screen readers rely on these tags to correctly navigate websites. You'll see that there's no visual difference between using many of these tags as opposed to a `div`, which is why I say that screen readers' needs are often invisible. But using the wrong semantic tags has a very real effect on potential users.

Did you know that `h1`, `h2`, etc. are actually semantic tags? It is very bad practice to use heading tags to control font size and weight--that's what CSS is for! Instead, only use heading tags as organizational tools for your website, such as making the page title an `h1`, and making subtitles `h2`.

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
```

### Language Specification

Screen readers are preprogrammed voices that read page content for users. They don't automatically know what language a website is written in (by language I mean human language, not programming language), which can result in some awkward pronunciation for foreign-language content. Specify the main language of a page using the appropriate language code:

```html
<!-- HTML file -->
<html lang = "en">
  <!-- Your website goes here -->
</html>
```

## Content Reading Level 

Although web developers often aren't responsible for writing site content, 1) they can be and 2) they are often asked for feedback on content.

English language learners, people with reading or language disabilities, and more are affected by unclear or complicated language. The standard for general-audience websites is to use language at an 8th-grade reading level. Avoid the passive voice and avoid convoluted sentence structure. Think about what words or phrases can be replaced with simpler ones. 

Correct spelling and grammar help make sure that everyone is on the same page and facilitates easy reading.

## Conclusion

Don't sweat it if you can't remember all of this. What's important is that you start looking at websites you use and websites you create with a critical eye, asking: "How does this meet accessibility needs?" "How might this website be hard for some people to use?" "What can I do to make my website functional and enjoyable for everyone?" 

Here are the topics we've covered:
* Fonts and font sizes
* Allowing zooming in
* Color contrast
* Alt text and video transcripts
* Disabling video autoplay
* Limiting animation and flashing effects
* Slideshow navigation
* Semantic HTML
* Tabindex and labeling links
* Content reading level

Accessibility should not be an afterthought. You'll make it easier for yourself and your users if you think about it early on: when you're picking your fonts and color palette, when you're creating elements in HTML, and when you're structuring the flow of your website. Keep learning and improving the experience for all users on all websites :) 

For more practice, check out our [portfolio task]()!

## Accessibility Checkers

Never rely on a machine to "check off" accessibility requirements. (See [this blog post](https://www.matuzo.at/blog/building-the-most-inaccessible-site-possible-with-a-perfect-lighthouse-score/) for an example of how machines can make mistakes sometimes.) But I highly recommend saving these resources for later--I use them all the time and they are great aids for checking how your website measures up. 

* [WAVE browser extension](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh)
* [w3 evaluation tools](https://www.w3.org/WAI/ER/tools/)
* [Color blindness checker](http://color-blindness.com/coblis-color-blindness-simulator/)
* [Color contrast checker ](http://webaim.org/resources/contrastchecker/)
* [Accessibility checker](http://wave.webaim.org)
* [Hemingway reading level checker](http://www.hemingwayapp.com/)

## Further Reading

* [Elsevier guidelines](https://www.elsevier.com/about/policies/accessibility)
* [Yale guidelines](https://usability.yale.edu/web-accessibility/articles/readability)
* [w3 guidelines](https://www.w3.org/TR/WCAG21/#reading-level)

## Reference Links

* [Semantic HTML (MDN)](http://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
* [Semantic HTML flowchart (HTML5 Doctor)](http://html5doctor.com/downloads/h5d-sectioning-flowchart.png)
* [Tabindex (MDN)](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex)
* [Hyperlink accessibility & tab index (Yale)](https://usability.yale.edu/web-accessibility/articles/links)
* [Font size guidelines (Learn UI)](https://learnui.design/blog/mobile-desktop-website-font-size-guidelines.html)
