---
layout: post
title:  "“Using” Instagram API"
date:   2016-11-07 12:52:06 -0400
categories: uncategorized
---

Steps to use Instagram’s API. Need to be logged into an Instagram account for this.

<ul>
    <li>Go to the <a href="https://www.instagram.com/developer/">Instagram Developer Page</a></li>
    <li>Go to “Manage Clients” and Register a new client</li>
    <li>Go back to “Manage Clients” and go to the “Security” tab.</li>
    <li>Open a new tab and go to {% highlight text %}https://www.instagram.com/oauth/authorize/?client_id=CLIENT_ID&redirect_uri=ALLOWED_URIs&response_type=token&scope=public_content{% endhighlight %}</li>
    <li>Replace CLIENT_ID with your Client ID from your Manage Clients page</li>
    <li>Replace ALLOWED_URIs with whatever your put for Valid redirect URIs in the Security tab. These can be a url to any website.</li>
    <li>You will get a new tab with your URI followed by /#access_token=&lt;YOUR_ACCESS_TOKEN&gt;</li>
    <li>Use this access token in the url for your API requests</li>
</ul>

Unfortunately, although your requests may succeed, you will probably get empty data.

{% highlight javascript %}
{"meta": {"code": 200}, "data": []}
{% endhighlight %}

This is because your app is in ‘Sandbox Mode’. A feature Instagram implemented in late 2015, in order to revamp their API and have more strict requirements to access their endpoints to prevent malicious activity. Your requests will only search for users that are in your “Sandbox.” i.e uses in the Sandbox tab next to your security tab.

In order to get out of sandbox mode into ‘Live’ mode, go into the Permissions tab and start a submission, and Instagram will review your request. Since I don’t have a company name or private policy URL, I have not done this, and am stuck in the virtually useless sandbox mode. Though I assume Instagram is quite strict and will review your description carefully, considering how much they are restricting actual access to their API…
