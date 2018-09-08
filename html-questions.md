# HTML Questions

* [What does a doctype do?](#what-does-a-doctype-do)
* [How do you serve a page with content in multiple languages?](#how-do-you-serve-a-page-with-content-in-multiple-languages)
* [What kind of things must you be wary of when designing or developing for multilingual sites?](#what-kind-of-things-must-you-be-wary-of-when-designing-or-developing-for-multilingual-sites)
* [Describe the difference between a cookie, sessionStorage and localStorage.](#describe-the-difference-between-a-cookie-sessionstorage-and-localstorage)
* [Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?](#why-is-it-generally-a-good-idea-to-position-css-links-between-headhead-and-js-scripts-just-before-body-do-you-know-any-exceptions)
* [Have you used different HTML templating languages before?](#have-you-used-different-html-templating-languages-before)

</br>

### What does a `DOCTYPE` do?

`DOCTYPE` is an abbreviation for "document type". It is a declaration used in HTML to distinguish between **standards mode** and **quirks mode** (old HTML and CSS). Its presence tells the browser to render the web page in standards mode.

Just add <!DOCTYPE html> at the start of your page.

### How do you serve a page with content in multiple languages?
When client send an HTTP request to a server, it usually sends information about language preferences, such as in the `Accept-Language` header. The server can then use this information to return a version of the document in the appropriate language if available. The returned HTML document should also declare the lang attribute in the `<html>` tag, such as `<html lang="en">...</html>`.

### What kind of things must you be wary of when designing or developing for multilingual sites?
* Use `lang` attribute in your HTML.
* Directing users to their native language without hassle
* Restrictive words/sentence length. Be wary of layout or overflow issues in the design. Eg: **headlines, labels, and buttons** which are not free-flowing like text or comments.
* Different **color meaning**, **formatting dates**,**reading direction** and **currencies**. Eg. "May 31, 2012" in the U.S. vs. "31 May 2012" in parts of Europe.

### Describe the difference between a cookie, sessionStorage and localStorage.
_**WebStorage**_
* _**LocalStorage**_

    size: 5MB, Forever unless be cleared, accesssed any window

```
<script src="../js/jquery.min.js"></script>
function closeAd(){
    if(localStorage.getItem("isClose")){             
        $(".header").hide();
    }else{
        $(".header").show();
    }
    $(".close").click(function(){
        $(".header").fadeOut(1000);
    
        localStorage.setItem("isClose", "1"); 
    })
}
closeAd();
```

* _**SessionStorage**_
size: 5MB, Expired on tab close, accessed on same tab


* _**Cookie**_ 
size:4k, expired when window closed
    
```
<script src="../js/cookie.js"></script>
function hideHeader(){
    if(getCookie("isClose")){             
        $(".header").hide();
    }else{
        $(".header").show();
    }
    
    $(".close").click(function(){
        $(".header").fadeOut(1000);

        setCookie("isClose", "1","s10");
    })
}
hideHeader();
```

 ![屏幕快照 2018-09-07 下午5.49.48](media/15363625627319/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-09-07%20%E4%B8%8B%E5%8D%885.49.48.png)
* Pros:
    * Conveniency: Store which web you have been to, fill your address or other information.
    * Effective Ad:  Internet marketing companies collect data from cookies
    * Easy to control: Clear your browsing history
* Cons: 
    * Privacy: Cookie enabled web browsers keep track of all the websites you have visited.
    * Security: If be stolen, someone get all information of session.
    * Increase the traffic in/out.
    
### Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
Putting `<link>`s in the head is part of the specification. Besides that, placing at the top allows the page to render progressively which improves the user experience. 

`<script>`s block HTML parsing while they are being downloaded and executed. Downloading the scripts at the bottom will allow the HTML to be parsed and displayed to the user first.

### Have you used different HTML templating languages before?
Yes, **Pug** (formerly **Jade**),**EJS**. They provide similar functionality of escaping content and helpful filters for manipulating the data to be displayed. 


###### Reference






