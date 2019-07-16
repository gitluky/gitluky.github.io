---
layout: post
title:      "Responsive Layout: media queries"
date:       2019-07-16 20:20:17 +0000
permalink:  responsive_layout_media_queries
---


Nowadays, your web app can be viewed on a multitude of different devices. We’ve all visited ancient websites that were obviously built for desktops and did not translate well on our mobile devices - the text and images were microscopic, you had to zoom in every time you wanted to click on a link and god forbid if you didn’t have toddler sized fingers. Times have changed, now most web apps are developed in a way where you can view them on almost all devices, this approach to development is what we call Responsive Design. In this post I will go over one approach to make a web app more responsive – media queries.
Writing media queries is equivalent to setting break points for when you want css attributes for objects to change in order for it to better fit the screen or some other reasoning.. For example, if you have 2 columns of text and you want the columns to stack into 1 column when the screen is sized down instead of having 2 very thin columns, that will be a good opportunity to write a media query. You simply figure out what size you want to screen to be when the columns start stacking. You can see this example here:[codepen](https://codepen.io/jluk87/pen/WqqPbL). 
First, comment out the @media query completely then increase and decrease the width of the browser window. You will noticed the columns becoming very thin and there is no response to the resizing. Now, uncomment out the media query and play around with resizing it. I’ve set the max-width to 1080px, meaning that up until the width of the page is 1080px, the width of each column will be 100% of the provided space. After 1080px, the column width will only be 40%, leaving enough room to allow the other column to fit next to it side-by-side. 
You can include as many media queries as you want and there are more conditionals than just max-width. There are also min-width, min-height, max-height, and ones provided for device sizing. For more examples on this: [css-media-queries](https://css-tricks.com/css-media-queries/)

