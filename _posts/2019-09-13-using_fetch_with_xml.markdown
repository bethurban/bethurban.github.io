---
layout: post
title:      "Using `fetch` with XML"
date:       2019-09-13 19:40:33 +0000
permalink:  using_fetch_with_xml
---


When I was building my final Flatiron project, a web app with a React/Redux front-end and a Rails API, I found myself struggling with the data returned from Zillow's API via `fetch`. I was used to using the `json()` method to parse API returns into neat, easy-to-use JSON, but quickly realized that wouldn't work with XML, the only format that Zillow's API returns.

## Using `text()` for the initial parse
Since I couldn't use the `json()` parser, I turned to [`text()`](https://developer.mozilla.org/en-US/docs/Web/API/Body/text), which returned a Promise that resolved by converting Zillow's API response to my `fetch` call into a [USVString](https://developer.mozilla.org/en-US/docs/Web/API/USVString). But I still didn't have data that I could work with.

```
  fetch(`https://www.zillow.com/webservice/GetDeepComps.htm?zws-id=${ZWS_ID}&zpid=${zpid}&count=5`)
	.then(response => response.text())
```

## `DOMParser`
I next used the [`DOMParser`](https://developer.mozilla.org/en-US/docs/Web/API/DOMParser) interface to create a new XML DOM parser that could be used to convert the USVString that `text()` resolved with into a workable XML DOM object.

I passed `text()`'s resolution to `parseFromString()` via the new XML DOM parser, along with a mimeType argument of `"text/xml"` to tell `parseFromString()` the class of its return value:

```
  fetch(`https://www.zillow.com/webservice/GetDeepComps.htm?zws-id=${ZWS_ID}&zpid=${zpid}&count=5`)
	.then(response => response.text())
	.then(text => (new window.DOMParser()).parseFromString(text, "text/xml"))
```

## The resulting data
Working with the above code (and a whole lot of `console.log`-ing!), I figured out that the data I needed from the XML was contained in the `<principal>` tag, which I isolated like so:

```
  fetch(`https://www.zillow.com/webservice/GetDeepComps.htm?zws-id=${ZWS_ID}&zpid=${zpid}&count=5`)
	.then(response => response.text())
	.then(text => (new window.DOMParser()).parseFromString(text, "text/xml"))
	.then(xml => xml.getElementsByTagName("principal")[0])
```

From that point forward, I was able to extract the details I needed from the XML via [`childNodes`](https://www.w3schools.com/xml/prop_document_childnodes.asp) and [`innerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML).



