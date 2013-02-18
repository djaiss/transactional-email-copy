## Background

As a product manager (in my professional life) and occasional developer working on my personal projects, I often have to write transactional emails myself. This is not an easy task for me: English is not my mother tongue and I don't have great marketing skills. I happen to browse through my Littlesnapper collection very often to read what others have done in their own transactional emails.

Then I thought: hey, Regis, you could probably share all those nice transactional emails to everyone on the planet. So I did it. Few hours later, I created this Jekyll-based repository and started to share this knowledge to the world.

## Philosophy

This website is listed as open-source on Github. That means everyone can either fork the repository or can choose to participe with pull-requests.

## How to participate

Submit a pull request to this repo, or send an email to transactionalemail AT fastmail DOT fm with the following subject "New post [BRAND NAME]". I will then judge the quality of the email (I'd like to keep a nice collection of emails, and it's not a democracy) and if it's good, it will show up in the next days or so.

### Structure of Jekyll post

Each post must start with the following structure:

```markdown
---
layout: post
title: Plex Account Confirmation
image: 2012-10-06-plex.png 
companyurl: https://my.plexapp.com
company: Plex
category: account-confirmation
category-fullname: Account confirmation
dateposted: 2012-10-06
author: Regis Freyd
author-url: http://djaiss.github.com
subject: Confirm your account
---
```

As of October 30, 2012, here are the following acceptable categories:

* account-confirmation (Account confirmation)
* cancellation (Cancellation)
* welcome-email (Welcome email)
* end-trial-email (End trial email)
* free-trial (Free trial email)
* weekly-digest (Weekly digest)
* password-confirmation (Password confirmation)

### Images

Images are placed in the `img/screenshots` folder, and have to be named with the following format `yyyy-mm-dd-COMPANY`. Please make sure images are in the PNG format and compressed with [Imageoptim](http://imageoptim.com/) or equivalent.

## Automatic creation of new posts

To facilitate the creation of new posts, there is a Rake method that takes in argument the name of the company and prefill a new post. It's pretty cool (it even takes your name from your Git configuration). Here is how the script would work with a company named Trello. Don't worry about casing.

`rake new_post COMPANY=trello`

## Taking down posts

Perhaps you don't want your brand to appear on that website. You have the right to ask me to remove it, of course (and I didn't ask for permissions in the first place). If you want me to remove one of the post, send me an email to transactionalemail AT fastmail DOT fm or send me a pull request, and I will proceed to the deletion immediately.

## Licence

I don't even know which one to use. Let's use this one:

Copyright (c) 2012 Regis Freyd
Licensed under the MIT, GPL licenses.
