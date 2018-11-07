---
layout: post
title:  "OAuth notes"
date:   2016-11-07 15:52:06 -0400
categories: uncategorized
---

<a href="https://developers.google.com/api-client-library/python/guide/aaa_oauth">Google's Developer Guide</a> on this topic

is very helpful

Consumer Key (Client ID) – API key associated with YOUR application.

Consumer Secret (Client Secret) – “Password” to be sent with your key to the server (whichever API we are getting data from) to make sure you own the application you say you do

Access Token / Secret – Issued to US by the server. Gives us privileges of what we can do, see, etc, provided when making API endpoint requests.

To get token sometimes use a redirect URI? – you put in client ID and stuff in and url and it spits out a new page url with your token… is it just an arbitrary website?

<a href="http://stackoverflow.com/questions/13281084/whats-a-redirect-uri-how-does-it-apply-to-ios-app-for-oauth2-0">ANSWER</a>
