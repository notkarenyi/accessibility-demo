# accessibility-demo

#Workshop Notes

Welcome to Karen's introduction to accessibility on the web! After this workshop, you should have a basic understanding of what kinds of needs we should be meeting as web developers, and how to look at a website from multiple angles using your knowledge of accessibility guidelines, as well as a few useful tools. 

#Why Accessibility?

1. Help people with all kinds of needs use and enjoy your website
1. Increase traffic and user satisfaction
1. Make the experience better for everyone else as well

For most web developers and many users, poor accessibility features are an inconvenience at worst or even unnoticeable at best. But a large fraction of internet users experience a range of needs that limit what many think of as "normal" web usage. These needs may include colorblindness, use of a screen reader (for blind people, people with motor disabilities, etc.), poor vision (for the elderly, people with visual impairments, etc.), susceptibility to seizures, and more. What comes to your mind when you think of the word "disabled" or the word "accessible"? Our immediate assumptions about these words can be wrong or partially wrong, and in order to create the best experience on our websites, we should be comfortable with constantly adapting to the highest standards for accessibility. (This tends to be a theme across computer programming.) Everyone benefits from websites that successfully follow accessibility guidelines. 
 
#Which Site is Worse?

#What Does Accessibility Involve?

Every part of your website that you design or create will be used by all kinds of different people. So, we need to think about how these parts can meet the needs of our users. Many web developers (like me) love the design part of web development, but sometimes we get too caught up in what looks "cool" and not what is actually legible or usable. Good web design, like any kind of design, is a balance of both aesthetic and function.

Now we're ready to dive into the basic foundations of accessibility!

#Appearance
One of the most straightforward places to start is the visual appearance of your website, since most of us are familiar with what's "good" versus what's not so good. Have you ever visited a mobile or desktop website with an uncomfortably small or weirdly large font? Pretty annoying, right? Fortunately, someone was smart enough to come up with standard font sizes for mobile and desktop:

<code>
  @media screen and (max-width: 768px) {
    font-size: 16px;
  }
  
  @media screen and (min-width: 769px) {
    font-size: 18px;
  }
</code>

Users with visual impairments, such as the elderly, often need to zoom in on 16px or 18px text in order to be able to read clearly. As you're developing your website, try zooming in up to 200% and see if the website is still usable. If elements are jumping around or hiding text at this zoom level, that's bad news and we should take steps to fix that. Avoid making the user have to scroll horizontally--the text should resize within the window.

<code>
</code>

On the same note, do not use display (aka fancy) fonts in body text. This is painful for everyone. Micro typography lesson: serif fonts like Times New Roman are often used in body text, because serifs aid the eye in reading text. (Serifs are the little hooks on the ends of letters, like the curve on the ends of the Ts in this document.) Sans serif fonts like Arial are also popular because they look sleek and modern. A good rule of thumb is to copy a paragraph of an article into your chosen font, and see if you can easily scan the paragraph. If not, it's probably not a good choice for your website.

Another very important consideration in terms of appearance is color contrast. Always use a color-contrast checker to ensure that your text meets a good contrast ratio. Here's one of the most common examples of bad color contrast that I see around the web:

<code>
  .bad {
    color: #ffffff
    background-color: #fee851
  }
  
  .good {
    color: #000000
    background-color: #fee851
  }
</code>

Similarly, use a color-blindness checker to simulate how your website would look to someone with color blindness. Fun fact: color blindness affects 1 in 12 men and 1 in 200 women worldwide. 

Be very careful when placing text over images. In fact, avoid placing text over images when the text is essential to basic understanding or function of the website.

#Images and Videos
