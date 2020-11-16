---
id: 004-css-variables.md
title: CSS Variables
tags:
  - CSS
  - Variables
  - CSS Variables
author: Rabson J Phiri
meta-description: How to make use of CSS variables
date: 2020-10-26 17:27:18 +0100
template: post
categories:
  - other
cover: ../images/categories/other.png
---

# CSS Variables

Variables make our lives easy. For those not familiar with this word, a **variable** is simply a "storage container" whose value can change/vary, hence the name.

In CSS, you can also use variables, or custom properties, an extremely powerful feature. But why even use variables in the first place? Well, for a very small website, it might not matter that much. But imaging you're using, let's say, a color more than once in your document, and you later decide to change that color. You'd have to go in every place that has that color and manually change it. This can get messy and confusing.

With variables, you'd have to change the color in only one place, and it'll be updated everywhere where that variable is used.

#### Global Declaration

This makes the custom properties accessible throughout the document

```css
:root {
  --theme-color: blue;
  --default-font-size: 1rem;
}
```

You can also define them within a ruleset, like this:

```css
.article {
   --font-size: 2rem;
}
```

#### Usage
```css
body {
   font-size: var(--default-font-size);
}

button {
   background-color: var(--theme-color);
}

.navbar {   
   font-size: var(--default-font-size);
}
```

More on this topic [here](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)


