---
title: "Save Hours for Qualitative Research With AI and Automation"
date: 2023-03-30
description: 'Qualitative research is a goldmine, but doing it is tedious. Read this for a quick guide on how to use automation and AI to save hours doing it.'
image: images/META - Qualitative Research With AI.png
imageAltAttribute: Cover image of the post
tags:
   - tools
   - web 
   - miscellaneous
---
The best marketers know that qualitative research is a goldmine. It can help you uncover things you never knew existed, launch a new product, or get accused of reading your prospect's mind.

Unfortunately, it's tedious work that most will skip when given an option to.

What if you could make it a lot less time consuming with some automation and AI? Let's do a quick experiment to find out.

## Experiment: gather and interpret qualitative data using automation and AI

There are two stages in qualitative research that you need to handle:

1.  Collecting data
2.  Interpreting data

Proper researchers will probably cringe at my simplistic description, but stay with me and you'll see how you can get 90% of the value for 10% of the effort.

### Here's what I'm going to do

1.  Scrape a review site using [bardeen.ai](http://bardeen.ai) -- a neat no code automation tool
2.  Clean up the data in Google Sheets to have better inputs
3.  Interpret the data using ChatGPT

## Step 1 -- Collecting the data with bardeen

If you have ever tried to scrape the web before, you know it can get tricky. Many sites are not exactly happy with you scraping their content and will have various anti-bot measures at the slightest hint of automation.

This usecase, while automated, doesn't really hurt the business on the other end. It merely expedites the actions you would do anyway.

### Setting up the scraper

I recently discovered a nice tool named *bardeen.ai* that enables you to create a DIY scraper without having to be proficient in python or Javascript. It's a Chrome extension and you can [download it here](https://chrome.google.com/webstore/detail/bardeen-automate-manual-w/ihhkmalpkhkoedlmcnilbbhhbhnicjga).

Now that you've downloaded the extension and set up an account, you should simply navigate to the site where you'll be collecting the data. For this experiment, it's G2 and I picked the review page of Writesonic AI writing tool for the demo.

{{< youtube rL590TkrTQM >}}
<br>
Here's how to set up scraper's settings:

1.  Launch Bardeen using Alt+B or the extension icon
2.  Click on Scraper in top menu and select New Scraper Template
3.  Select List or Table and name it
4.  Select 2 items of the same kind in 2 different reviews (e.g. the review's title)
5.  Select the type of pagination
6.  Select the elements to scrape (the actual data you need)
7.  Checkmark next to Get Text and click the Get Data button
8.  Name your column for output spreadsheet
9.  Click Save Template on the right side
10. Done

It looks like quite the list, but if you follow the video above the list, you'll see it's super simple. I just didn't want to skip anything as the steps were not obvious to me as a first-time user, but now it's a breeze.

### Setting up the playbook

You just set up the template to collect data, but you also need to instruct the automation to store it somewhere. That's what a playbook is for in Bardeen. You will use it to save the data you collect to a Google Sheet.

{{< youtube uUjo4pTuwO4 >}}
<br>
Here's how to set up the playbook:

1.  Click Playbooks in the Bardeen's top menu, then Create Playbook in the UI below
2.  Select Scrape among the Actions, then Scrape data on active tab
3.  Then you will be able to see scraper's settings you've saved before, select those
4.  Select the amount of items (in this case reviews) and pages you want to extract
5.  Set a custom delay if site might have some scraping protection in place and hit Done
6.  Then click + to the right from your scraper block and select New Action
7.  Type add rows in the search bar and select Add rows to Google Sheet as your action
8.  Connect a Google account if you haven't done so before
9.  Select Create Google Sheet with name [title] and type in the name your new spreadsheet will have
10. Then click the Use commands button in UI that appears and select the data from Action 1
11. Hit Done everywhere you see and that's it, you're set.

If you're intimidated by the list above just watch the video instead. It's way easier than it seems.

## Step 2 -- Cleaning up scraped data in Google Sheets

Once you open the scraper's output, you'll notice that G2 added a text string to the end of each review stating where it was originally collected. It's a fair thing to do on their end, but we're going to perform an automated analysis, so this has to be stripped away.

I also wanted to add numbering just so it's clear for ChatGPT where each review starts.

To do both of these, I used:

1.  A *SUBSTITUTE* function that replaces a text string in cell with, in our case, nothing.\
    =SUBSTITUTE(A4, "The text you want to remove.", "")
2.  Concatenation to add the numbering, where C contains a column of numbers and B is the cleaned up review.\
    =C2 & ". " & B2

I'm not going to write a step by step list for this, just use [this Google Sheet as a template](https://docs.google.com/spreadsheets/d/10KFbX3WF3U1eX-iXA4yBddy72aHQYDz621tfC17UnW0/edit?usp=sharing) and you won't take long to figure it out.

Also, while I'm sure one could set up some sort of automation to handle this straight away, it was way faster to just use a couple of manual actions in a tool I already know (Google Sheets) and be done with it.

Wouldn't be surprised if this last statement ages like raw milk though.

## Step 3 -- Interpreting reviews with ChatGPT

The rest is now a matter of prompting the ChatGPT for interpretation.

I used a prompt that sounds like this:

```
I've got some negative reviews of a product in a numbered list below. Please summarize them into top 3 most common arguments people have.
```

Then appended the actual reviews to this, *et voilà!*

### The results of ChatGPT summary

ChatGPT summarized the 20 reviews provided to these three points:

*[...]*

1.  *The pricing model is problematic, and the word limits on each plan can be limiting.*

2.  *The generated content may need manual editing, and the tool sometimes generates content that is inaccurate or irrelevant to the intended use case.*

3.  *The AI copywriting technology has inherent limitations and cannot replace human copywriting entirely. Additionally, some features are not intuitive, and there are technical issues with the platform's interface and functionality.*

To be completely accurate, I had to click *Regenerate response* a few times since the first 2 answers I got were not informative enough. That doesn't invalidate the approach itself though as it didn't add any additional work aside from clicking a button twice.

{{< youtube bGdS5J85oC0 >}}
<br>
If we look at the 3 points in the summary, key themes emerge. #1 is pricing, #2 is content quality, and #3 is a mix of content quality and product's features and UI.

For the sake of this experiment, let's take a manual look if there's something else in the reviews that ChatGPT skipped.

### Manual review

I went over all of the reviews and placed them into categories.

![](https://assets.ycodeapp.com/assets/app14922/Images/KjXfkjSIMXuaJgNqv5dbEWN9Tl641mZmrqmwj3mW.png)

After a manual review, it's clear that there's really not much else to bring up in there.

I marked a few of the reviews as not eligible due to people stating they have barely used the tool. Also, one review simply went over the pros instead of cons and looked not too legitimate overall.

It doesn't look like any of these non-eligible inputs swayed the GPT's analysis.

## Let's give this the Performance Pirate Score

### Ease of use 🟢🟢🟢🟢🔴

The Bardeen extension required some fiddling, but it's well-documented and 100 times easier than setting up a scraper in headless Chrome on your own with Puppeteer or using a scraper via something like Phantombuster.

### Productivity 🟢🟢🟢🟢🟢

Even if you happen to enjoy doing this type of digging and summarizing manually, this is still a massive boost in the speed of it. I've explored some uses in the next section of this post that will reinforce this even further.

### Usefulness 🟢🟢🟢🟢🔴

This is a way to do an extremely valuable task that's often overlooked due to being tedious. That's especially the case for startups or smaller companies that don't have a large marketing department where somebody can be dedicated to research.

### Obsolescence 🟢🟢🟢🔴🔴

The current setup is enough to replace an entry level person collecting and interpreting reviews or other written data manually. Alternatively, it's also enough to offset the need to hire somebody on Fiverr to write you a web scraper.

Connecting this into a full fledged automation flow might further reduce the workload.

## Additional uses

### Finding industry terms

Aside from finding the pain points, review analysis can also be used to find industry language and jargon that your audience uses. Those can later be used in writing ads or other content that speaks the way your target audience does. You wouldn't believe someone selling you marketing services if they say _B-2-B_ instead of _B2B_, right?

### Writing copy

This type of research typically leads to writing better for ads, emails, blog, and elsewhere anyway, so why not ask ChatGPT to write something from what it just learned?

It's not going to be a masterpiece, but there's a chance it's going to be good enough with a couple of edits and most importantly, it will hit all of the pain points.

## That's a wrap! 🦜

Overall, this way of using automation and AI for qualitative research is extremely useful and saves a ton of time. I'll keep experimenting in the area and see how can I connect this into an extensive automated workflow to further boost the usefulness.

If you'd like to chat about how to apply this in the work you do -- [book a 30 minute call](https://calendly.com/gocentas/intro?utm_source=performance-pirate&utm_medium=blogpost&utm_campaign=sound-like-a-robot) with me and let's talk it through. No strings attached.