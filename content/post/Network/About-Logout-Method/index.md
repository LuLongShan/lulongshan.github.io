---
title: Logout GET or POST
date: 2020-09-10
categories:
  - programing
markup: mmark
math: true
tags:
    - web
---

## [Copy]Logout: GET or POST

>This question is not about when to use GET or POST in general; it is about which is the recommended one for handling logging out of a web application. I have found plenty of information on the differences between GET and POST in the general sense, but I did not find a definite answer for this particular scenario.
 
> As a pragmatist, I'm inclined to use GET, because implementing it is way simpler than POST; just drop a simple link and you're done. This seems to be case with the vast majority of websites I can think of, at least from the top of my head. Even Stack Overflow handles logging out with GET.
 
> The thing making me hesitate is the (albeit old) argument that some web accelerators/proxies pre-cache pages by going and retrieving every link they find in the page, so the user gets a faster response when she clicks on them. I'm not sure if this still applies, but if this was the case, then in theory a user with one of these accelerators would get kicked out of the application as soon as she logs in, because her accelerator would find and retrieve the logout link even if she never clicked on it.
 
> Everything I have read so far suggest that POST should be used for "destructive actions", whereas actions that do not alter the internal state of the application -like querying and such- should be handled with GET. Based on this, the real question here is:
 
> Is logging out of an application considered a destructive action/does it alter the internal state of the application?

### Answer

>Use `POST`
 
> In 2010, using GET was probably an acceptable answer. But today (in 2013), browsers will pre-fetch pages they "think" you will visit next.(浏览器的预加载机制可能会加载登出链接，可是我没遇到过啊！)

