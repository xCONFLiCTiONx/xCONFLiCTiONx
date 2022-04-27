---
title:  "Social Post Scheduler"
subtitle: "Post to Facebook and Twitter on a weekly schedule"
layout: post
author: "xCONFLiCTiONx"
header-style: text
tags:
  - projects
--- 

{% include button-new-tab.html button_name="GitHub" button_class="primary" url="https://github.com/xCONFLiCTiONx/Social-Post-Scheduler" %}

Post to Facebook and Twitter on a weekly schedule. This is for repeat posts or for posts that you want to schedule for later. Using Facebook Creator Studio is the preferred method for posting to Facebook but for those posts that you repeat or want to post for a while then this program will save you tons of time.

#### Some things to consider while scheduling: 

* The page name field in the Facebook Connection area must be exact. 
* The entries are stored in a MSSQLLocal database and the instance will shutdown to save resources. That said, if you decide to edit an entry after it's been shutdown, the initial startup can take a few seconds causing the app to freeze until the instance starts. 
* Use the Text Editor tab to format the text easily along with seeing how many characters will be used. This is great for Twitter posts. 
* Twitter links plus the message cannot exceed 280 characters, so use short links or images instead. 
* You cannot post an image and a url in the same post. The url is used when you want to display the image from the website's open graph image, if they have one. If you want a link and an image in the post then put the link in the message instead. 
* Keep in mind that your computer must be running and the Social Post Scheduler must be running for posts to be posted so if you reboot your computer when a post is scheduled then it will be skipped. 
* To post a video, post it manually to your facebook page once and then grab the post link and then use that link in the link field to post them as a scheduled post. 
* Posting too many posts at the same time could cause issues on slower networks. Spread them out over a few minutes if this happens. 
* Make sure to setup backup and cleanup during a time that you won't be posting or editing the schedule. 


#### How to create the apps for Facebook and Twitter
##### Facebook API
<a href="https://developers.facebook.com">https://developers.facebook.com</a>

Generate USER Token with proper permissions:

* pages_show_list
* pages_read_engagement
* pages_manage_metadata
* pages_read_user_content
* pages_manage_posts
* pages_manage_engagement
* public_profile

![FacebookApi](https://github.com/xCONFLiCTiONx/Social-Post-Scheduler/raw/master/SocialPostScheduler/Resources/FacebookApi.jpg)

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

<hr>

##### Twitter API
<a href="https://developer.twitter.com/en/portal/dashboard">https://developer.twitter.com/en/portal/dashboard</a>

Go to Overview and click on `Create App`. 
Name your app and press OK. 
Copy your new keys and token to a safe place and click `App Settings`. 
Click `App permissions` and choose Read and Write then Save 

<hr>

##### Setup the database
You'll need to install Microsoft Local Database to use this application. You can download it <a href="https://www.microsoft.com/en-us/Download/details.aspx?id=101064">here</a>.

You only need to install LocalDB
![LocalDB](https://github.com/xCONFLiCTiONx/Social-Post-Scheduler/raw/master/SocialPostScheduler/Resources/LocalDB.jpg)
 
Next you'll need to setup the instance in your terminal or cmd prompt: `sqllocaldb i MSSQLLocalDB`

If the outcome doesn't look like the below screenshot move to the next step.
![outcome](https://github.com/xCONFLiCTiONx/Social-Post-Scheduler/raw/master/SocialPostScheduler/Resources/outcome.jpg)

 ```Terminal
sqllocaldb stop MSSQLLocalDB

sqllocaldb delete MSSQLLocalDB

sqllocaldb create MSSQLLocalDB
```
