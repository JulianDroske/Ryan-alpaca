# Recovery Report

Interested in a mystery singer and programmer, and here's the website that
he owned before and I'm curious about, which it's said to be welcome to
visit though.

![](./pageshot.png)


## Clues

The link written in his profile, `uryan.fun`, no longer exists almost
a year ago, according to Wayback Machine's only record:

```
http://uryan.fun/ | 05:47:33 March 04, 2023

Got an HTTP 302 response at crawl time

Redirecting to...

http://47.98.226.8:80
```

The IP server seems to be abandoned, leaving nothing other than a message
saying that domain does not exist, which looks familiar for BT users.
[Example with same result using BT](https://www.bt.cn/bbs/thread-116919-1-1.html)


So the source code here has been the only existing one related to his website.


## Before recovery

Apparently the webpage is incomplete, as well as some characters are missing
inside.

It's easy to tell, for instance:

```
!DOCTYPE htmlhtml lang=zh-cmn-Hans
head
    meta charset=utf-8
```

shows some patterns according to HTML5 standards, which every frontend dev
knows.

Recovered version for the code above should be:

```html
<!DOCTYPE html><html lang="zh-cmn-Hans"><head>
    <meta charset="utf-8">
```

Many characters are erased, possibly because the author failed to keep binary
files when going through some input fields that required escaping, or simply
on purpose. Anyway, the filtered chars have been found are listed below

`<>\/:"*`

causing many information lost, including:

* Basic HTML structure including attrs
* Broken CSS selectors
* Unreachable network resources
* ...

As such, we can recover the website back to life by manually modifying
the file, using intellect of mankind.


## Recovering

### BASIC HTML

```
                div class=container
                    h1 style=margin 0; id=barWelcomeh1
```
```html

                <div class="container">
                    <h1 style="margin 0;" id="bar">Welcome<h1>
```

### CSS / SELECTORS

```
      body -webkit-input-placeholder {
         WebKit browsers 

        font-family Source Sans Pro, sans-serif;
        color white;
        font-weight 300;
      }
```

```css
      body ::-webkit-input-placeholder {
        /* WebKit browsers */

        font-family: "Source Sans Pro", sans-serif;
        color: "white";
        font-weight: "300";
      }
```

### URLS

```
      @font-face {
        font-family iconfont;
        src url('at.alicdn.comtfont_1706200_3sgw4esvyq9.eott=1584846914425');
         IE9 
        src url('at.alicdn.comtfont_1706200_3sgw4esvyq9.eott=1584846914425#iefix') format('embedded-opentype'),
           IE6-IE8 
          url('dataapplicationx-font-woff2;charset=utf-8;base64,d09GMgABAAAAAAPcAAsAAAAACEAAAAOQAAEAAAAAAAAAAAAAAAA /* TRUNCATED */
          url('at.alicdn.comtfont_1706200_3sgw4esvyq9.wofft=1584846914425') format('woff'),
          url('at.alicdn.comtfont_1706200_3sgw4esvyq9.ttft=1584846914425') format('truetype'),
           chrome, firefox, opera, Safari, Android, iOS 4.2+ 
          url('at.alicdn.comtfont_1706200_3sgw4esvyq9.svgt=1584846914425#iconfont') format('svg');
         iOS 4.1- 
      }
```

```css
      @font-face {
        font-family: "iconfont";
        src: url('at.alicdn.com/t/font_1706200_3sgw4esvyq9.eot?t=1584846914425');
        /* IE9 */
        src: url('at.alicdn.com/t/font_1706200_3sgw4esvyq9.eot?t=1584846914425#iefix') format('embedded-opentype'),
          /* IE6-IE8 */
          url('data:application/x-font-woff2;charset=utf-8;base64,d09GMgABAAAAAAPcAAsAAAAACEAAAAOQAAEAAAAAAAAAAAAAAAA /* TRUNCATED */
          url('at.alicdn.com/t/font_1706200_3sgw4esvyq9.woff?t=1584846914425') format('woff'),
          url('at.alicdn.com/t/font_1706200_3sgw4esvyq9.ttf?t=1584846914425') format('truetype'),
          /* chrome, firefox, opera, Safari, Android, iOS 4.2+ */
          url('at.alicdn.com/t/font_1706200_3sgw4esvyq9.svg?t=1584846914425#iconfont') format('svg');
        /* iOS 4.1- */
      }
```

### MALFORMED CHUNKS

```
onclick=javascrtptwindow.location.href='httpsryan.rthe.xyzryan2.html'
               ^~~~
```

```
onclick="javascript:window.location.href='https://ryan.rthe.xyz/ryan2.html'"
                ^~~~
```


## Final Thoughts

Maybe he was trying to hide his website from the internet, I don't really think
that it was so terrible, however. The effects are pretty, despite the failure
to get rid of overflow problems and the possiblility to be a stolen work.

Anyway, although I extracted the code for curiousity, I admire this kind of
work as I'm a random blogger creating own technologies as well.
