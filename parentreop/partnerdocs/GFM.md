# GitHub-flavored Markdown, Extensions, and HTML code

## GitHub-flavored Markdown (GFM) ##
Open Publishing supports authoring topics in GitHub-flavored Markdown (GFM)

Here are two great tutorials for Markdown and GitHub Flavored Markdown:

- [Introduction to Markdown by John Gruber](http://daringfireball.net/projects/markdown/syntax)
- [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/)

You can use any Markdown editor you would like to edit Markdown. Some suggestions: [MarkdownPad](http://markdownpad.com/), [Visual Studio Code](https://www.visualstudio.com/en-us/products/code-vs.aspx), [Markdown Mode](https://visualstudiogallery.msdn.microsoft.com/0855e23e-4c4c-4c82-8b39-24ab5c5a7f79). 

files. Most of them provide live preview functionality so that you can get a simple preview when writing the topic.

## Open Publishing Extensions ##

### File Include ###

A Markdown file can reference other files inside its content, such as images, code snippets, and another markdown file that is shared across multiple topics within the docset.

The following items are needed for a file include:
- Required: Folder path within the repo
- Optional: Repository Id, which includes: account name, collection name, project name, repository name. The repository of the file is used if it is not specified.

The format of a file include is `![Display text]({folderPath})`

An example for an image is `![Introduction](..\images\Introduction.png)`

## HTML whitelist ##

You can embed HTML code into your content, so long as it is within the GitHub WhiteLlist. **We also enable iframe element for video embedding even though it is not in the GFM whitelist**. HTML rendered by the various markup language processors gets passed through an [HTML sanitization filter](https://github.com/jch/html-pipeline/blob/master/lib/html/pipeline/sanitization_filter.rb) for security reasons. HTML elements not in the whitelist are removed. HTML attributes not in the whitelist are removed from the preserved elements.

The following HTML elements, organized by category, are whitelisted:

Type  |Elements  
---------|---------
Headings     |  h1, h2, h3, h4, h5, h6, h7, h8       
Prose     |  p, div, blockquote       
Formatted     |   pre      
Inline     |     b, i, strong, em, tt, code, ins, del, sup, sub, kbd, samp, q, var    
Lists     |   ol, ul, li, dl, dt, dd      
Tables     | table, thead, tbody, tfoot, tr, td, th        
Breaks     |   br, hr      
Ruby (East Asian)     |   ruby, rt, rp      
Video (not in GFM whitelist)    |  iframe
Comments | Comments

The following attributes, organized by element, are whitelisted:

Element  |Attributes  
---------|---------
a     |      href (http://, https://, mailto://, github-windows://, and github-mac:// URI schemes and relative paths only)   
iframe |  src, allowFullScreen, frameBorder, scrolling
img     |     src (http:// and https:// URI schemes and relative paths only)    
div     |     itemscope, itemtype    
All     |     abbr, accept, accept-charset, accesskey, action, align, alt, axis, border, cellpadding, cellspacing, char, charoff, charset, checked, cite, clear, cols, colspan, color, compact, coords, datetime, dir, disabled, enctype, for, frame, headers, height, hreflang, hspace, ismap, label, lang, longdesc, maxlength, media, method, multiple, name, nohref, noshade, nowrap, prompt, readonly, rel, rev, rows, rowspan, rules, scope, selected, shape, size, span, start, summary, tabindex, target, title, type, usemap, valign, value, vspace, width, itemprop    

Note that the id attribute is not whitelisted.
