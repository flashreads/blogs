---
id: 005-accessibility.md
title: Getting Started with Web Accessibility
tags: html, wcag, a11y, accessibility
date: 2021-10-22 23:50:42 +0200 
keywords: html, wcag, a11y, accessibility
categories: html
cover: ../../images/categories/html.png
author: Natalie Stroud
meta-description: A brief introduction into web accessibility
---

# Getting Started with Web Accessibility

Coding, writing, and designing your first webpage can be exciting. Like other web developers, I learned by copying and pasting code and testing different things out or even reading W3School pages so I can write my own code. But one thing that goes missing when web developers first learn to make website is web accessibility.

## What is Web Accessibility?

Chances are, regardless of where you spend your time on the internet, you've heard about web accessibility recently. The World Wide Web Consortium (W3C) defines web accessibility as "[when] websites, tools, and technologies are designed and developed so that people with disabilities can use them" [Introduction to Web Accessibility | Web Accessibility Initiative (WAI) | W3C](https://www.w3.org/WAI/fundamentals/accessibility-intro/#what). Disabilities can range anywhere from auditory, physical, visual, speech, to cognitive. Web accessibility can also benefit those without disabilities - whether you have a situational limitation, a temporary disability (like a broken arm), if you have limited bandwidth with your Internet connection, and even as you age.

## Things to Look For
So how does someone start implementing accessibility in their projects? Great question! First and foremost, web accessibility should be implemented from the start. Placing it at the end isn't impossible but this can cause more work and in some cases, it can be costly. 

### Color Contrast
Color contrast is one of the "low hanging fruit" when it comes to accessibility. If you place white text on a white background, will you be able to read it? What about black text on a black background?  One thing to keep in mind for color contrast is if your background is light, use dark text (and vice versa).  

Text on background color contrast must meet 4.5:1 and non-text color contrast must meet at least 3:1. (But these can be higher!)

Here's a link to a contrast checker!
[WebAIM: Contrast Checker](https://webaim.org/resources/contrastchecker/)

### Text Alternatives for Images
Creating alt text for images is another quick and easy way to add accessibility to your website.

```HTML
# <img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png">
```
What's wrong with the code example above? It seems correct, right? You have your image tag, it doesn't need to be closed, and you have a URL linking to the image.

We're missing alt text! Here's how we correct it:

```HTML
# <img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="Google logo">
```
There we go! In this example, we added the alt attribute and a text value to our image. So now, when screenreader users move over the image, they may hear something along the lines of "image Google logo". This is extremely beneficial for screenreader users who are blind. 

Here's a great article on image alt text
[WebAIM: Alternative Text](https://webaim.org/techniques/alttext/)

## Web Content Accessibility Guidelines (WCAG)
While I could write more and more about web accessibility, I'll leave the journey to you! There are some wonderful accessibility resources out there but the accessibility "source of truth" comes from W3C. It's called the [Web Content Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)