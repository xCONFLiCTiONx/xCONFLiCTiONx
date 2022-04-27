---
title:  "Facebook API"
subtitle: "How to obtain a user token"
layout: post
author: "xCONFLiCTiONx"
image: "FacebookApi.jpg"
header-style: text
tags:
  - documentation
--- 
### Facebook API
<a href="https://developers.facebook.com">https://developers.facebook.com</a>

Generate USER Token with proper permissions:

* pages_show_list
* pages_read_engagement
* pages_manage_metadata
* pages_read_user_content
* pages_manage_posts
* pages_manage_engagement
* public_profile

<img src="/img/post-images/FacebookApi.jpg" alt="FacebookWikiImage">


1. Make sure you are an admin of the Facebook page/s  you're posting to.
2. Create a Facebook App (should be the same user account that's associated with the page admin)
3. Head over to the <a href="http://developers.facebook.com/tools/explorer/" rel="noreferrer">Facebook Graph API Explorer</a>
4. On the top right, select the FB App you created from the "Application" drop down list
5. Click "Get User Access Token"
6. Make sure you add the correct permissions (see screenshot above).
7. Convert this short-lived access token into a long-lived access token by making this Graph API call: <a href="https://graph.facebook.com/oauth/access_token?client_id={APP_ID}&client_secret={APP_SECRET}&grant_type=fb_exchange_token&fb_exchange_token={SHORT_LIVED_ACCESS_TOKEN}">https://graph.facebook.com/oauth/access_token?client_id={APP_ID}&client_secret={APP_SECRET}&grant_type=fb_exchange_token&fb_exchange_token={SHORT_LIVED_ACCESS_TOKEN}</a>
8. Grab the new long-lived access token returned back
9. Make a Graph API call to see your accounts using the new long-lived access token: <a href="https://graph.facebook.com/{USER_ID}/accounts?access_token={LONG_LIVED_ACCESS_TOKEN}">https://graph.facebook.com/{USER_ID}/accounts?access_token={LONG_LIVED_ACCESS_TOKEN}</a>
10. Grab the <code>access_token</code> for the page you'll be pulling info from
