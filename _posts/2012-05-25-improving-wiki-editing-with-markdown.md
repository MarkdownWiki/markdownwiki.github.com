---
layout: post
title: "Improving Wiki Editing with Markdown"
description: ""
category: 
tags: [
	markdown,
	wiki,
	refresh,
	github,
	editing,
	interface,
	design,
	code mirror,
	ui,
	design,
	markdown wiki,
	media wiki,
	editor,
	javascript,
	syntax,
	highlight,
	syntax highting,
	user experience,
	nodejs,
	html,
	parsing,
	ruby,
	sundown,
	robotskirt
]
---
{% include JB/setup %}

The other day, I was tasked with updating a page on a wiki. This wiki happened to be hosted using the classic MediaWiki platform. The page I was editing involved me creating a table for some test data that I had gathered. Immediately I found myself googling for the proper syntax for creating a table in the (archaic) wiki syntax. If the syntax was parsed in Markdown or pure HTML, creating a table would have been MUCH easier and wouldn't have required me to look up the proper syntax.

## Improving Wiki Editing

For the longest time, when you edit a wiki, be it on a MediaWiki platform, confluence, or even on Github using markdown, you are always editing a plain text document that has no syntax highlighting to help you decipher what you are typing. With MarkdownWiki, we are about to change ALL of that. Here is a screenshot of the MarkdownWiki editor:

[<img src="/assets/markdownwiki_editor_preview.png">](/assets/markdownwiki_editor_preview.png)

First thing to notice is that MarkdownWiki provides you with a complete, syntax-highlighted editor. This allows users to see exactly what they are creating and makes it much easier to catch errors and makes creating and editing pages much easier.

If you are a javascript developer, then you are probably familiar with [JSFiddle](http://jsfiddle.net) and its built in editor. The editor provided to you by MarkdownWiki is very similar - both use the [CodeMirror](https://github.com/marijnh/CodeMirror2) library, providing an editor that is browser agnostic. 

## If it ain't broke, don't fix it

Since the launch of Github, the [Markdown](http://daringfireball.net/projects/markdown/) syntax has caught on real fast. So fast that Github created their [own flavor of markdown](http://github.github.com/github-flavored-markdown/). To keep make it so that you don't need to potentially learn another "flavor" of the Markdown syntax, we have adopted the Github flavor of Markdown. To stay consistent with their syntax, that means we had to find a parsing library that was compatible. Luckily, other people had the same idea as us, and have begun to develop compatible libraries for all the popular languages. Github, being a site based on various Ruby libraries, uses the [redcarpet](https://github.com/tanoku/redcarpet) library to convert their Markdown to valid HTML. As it turns out, their parser is built around the C-based library, (sundown)[https://github.com/tanoku/sundown]. Since MarkdownWiki is built on top of [NodeJS](http://nodejs.org), it made sense to find a library compatible with Node. Thankfully we were able to find just that; a Markdown libarry that wraps sundown, built for NodeJS called [robotskirt](https://github.com/benmills/robotskirt). Why it's called that, I have no idea, but it works beautifully and works great with the Github flavored markdown.

Here's a preview of what a typical wiki page will look like (the sample content is the example Markdown from [Github's Markdown documentation](http://github.github.com/github-flavored-markdown/)\):

[<img src="/assets/markdownwiki_page_example.png">](/assets/markdownwiki_page_example.png)


## More syntax highlighting!

The icing on the cake here is the added support for code syntax highlighting within your markdown. Thanks to [highlight.js](http://softwaremaniacs.org/soft/highlight/en/) MarkdownWiki supports 46 languages out of the box. Heres a quick look at how to take advantage of it:

<pre>
```javascript
var foobar = function(){
	console.log("this is a function");
};
```
</pre>

Simply provide the name of the language the block of code is, and highlight.js will choose the correct highlighting stylesheet.

## Some editor features

One of the major gripes I have about the state of current wiki editors is that it is a real pain in the ass to preview the changes that you are making. To preview anything, for example in MediaWiki, you are brought to an entirely new page in either a new window or new tab. I don't like this as it breaks the flow of editing the page. Our solution to this is to show you the preview EXACTLY where it is going to be - on the page right in front of you. Through the magic of javascript, when you click the "preview" button, your changes in the editor are parsed into HTML and displayed to you as ig you just saved the page. No navigating to another page or tab. Everything is presented live right in front of you. Don't like the changes you just made? Thats okay. Simply press the "Discard Changes" button and you are rolled back to the last saved state. Satisfied with your changes? Click the "Save" button and your content is saved and then updated with in front of you without refreshing the page or taking you away from the editor.


We think that this interface will greatly improve the user experience, making it easier than ever to create and edit your wikis. If you disagree with us, we would love to hear why. If you absolutely love what we are doing, we also want to hear it! We are here to provide YOU with what will be easiest for YOU.


