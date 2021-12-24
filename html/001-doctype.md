---
id: 001-doctype.md
title: What is Doctype in HTML?
tags:
  - html
  - tags
  - doctype
author: Zoran Pandovski
meta-description: Simple introduction to the html <!DOCTYPE html>
date: 2020-06-17 22:56:16 +0200
keywords: html, tags, doctype
template: post
categories:
  - html
image: assets/images/webb.svg
---

The DOCTYPE as the name indicates describes the type of the document that would be used so the web browser, web crawler or other client tools can know what type to expect e.g 

```html
<!DOCTYPE html>
<html>
<head>
<title>Website Title</title>
</head>

<body>
 The website body
</body>

</html>
```

This means that it is HTML5. The `<!DOCTYPE html>` is not an HTML tag it is just the information to the consumer so it knows how to parses the HTML. 
Web browsers are also using `<!DOCTYPE html>` to found out which mode to use for rendering the web page (quirks mode, almost standards mode, and full standards mode). The main idea of the modes is to make old web pages compatible in the new browsers that are following W3C standards. Check out this https://en.wikipedia.org/wiki/Quirks_mode#Comparison_of_document_types article for the difference in the rendering modes. 
Sometimes you can find other `DOCTYPE` declarations. Those are for old versions of HTML, so other declarations were used e.g in HTML 4:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

This declaration looks more complicated because it contains the document type definition. For the full list of Doctype declarations check out [W3 list](https://www.w3.org/QA/2002/04/valid-dtd-list.html).