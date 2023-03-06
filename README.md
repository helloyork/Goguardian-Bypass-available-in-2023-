# Goguardian Bypass | available in 2023!

With all due respect, I tried for three whole months, from hiding Iframe onload events to Puppeteer creating snapshots of web pages, and what I finally found was so simple that I didn't even need to consume any server arithmetic, I could just bypass it on the client side alone.

If you know a little bit about HTML, you know that there is a tag in HTML5 called `<embed>`
Take a look at the explanation on the MDN community.

> The <embed> HTML element embeds external content at the specified point in the document. This content is provided by an external application or other This content is provided by an external application or other source of interactive content such as a browser plug-in.

I noticed that Goguardian listens to the onload event of the Iframe in some way and then changes the content of the iframe on top of it. I kept trying to hide the loading event of the iframe in various ways, but goguardian, as a browser plug-in, has a very strong global control I don't even understand how it does it all.

I tried using Puppeteer to create a simulated user page with some interactive features, and then Google Devloper to create a web page with mhtml for offline use, but this was not ideal and consumed server resources while being slow. This took me a lot of time and stalled my research.

Eventually, I discovered that embed tags can be embedded in web pages, and Goguardian hasn't found this ridiculous bug yet

I can also give you a hint that there are some other tags in html that can do the same thing, based on this idea, I tried to embed a website and it was very successful, goguardian didn't move at all and the resources on the page were displayed normally (which is weird, because most of the time the website hosting the images on the page will refuse to respond to embeds from unknown websites and return a 403 error), and the Javascript on the page is running successfully

Well, I think I'm getting ahead of myself, so let me give you a very simple example
### `<embed src="https://example.com">`
In its simplest form, you can see that the page is successfully displayed in your html, and you can change the src to something that is blocked from the site

I also have a copy of the html in the repository with a fairly simple structure that fills the whole body with a specific page, you save it, change the url, render, done! It's worth noting that in some cases, for example if you download it inside the file system and preview it using a browser, you get a lot of 403 errors, which won't happen if you place it on your web server

#### Serious disclaimer: This is all interesting stuff that I have unintentionally researched, I will not be responsible for any legal issues arising from its use, please do not use it in illegal ways
