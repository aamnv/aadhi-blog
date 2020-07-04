---
title: "Should You Opt Into Etsy Offsite Ads?"
date: 2020-06-08
summary: A tale of two metrics.
tags: ["etsy", "miniprinter"]
slug: "opt-into-etsy-offsite-ads"
draft: false
---

I recently wrote up a breakdown of [Etsy fees as of June 2020](https://www.aadhi.rocks/posts/etsy-fees-2020). The post was pretty well received [on Reddit](https://www.reddit.com/r/Etsy/comments/gxrds1/an_analysis_of_etsy_fees_june_2020/) and I got a great suggestion for a follow-up article: analyzing Etsy's offsite ads fees. Specifically - can you incorporate the fee into your overall pricing and if so, would that price still keep your shop competitive?

In the reddit thread, [/u/freemakerlucy](https://www.reddit.com/r/Etsy/comments/gxrds1/an_analysis_of_etsy_fees_june_2020/ft54a4a?utm_source=share&utm_medium=web2x) posted about how they thought about this calculation:

> You can look at how many of your sales come from offside ads (hard to do initially but Etsy did send me an email saying they expect them to generate 5% of my sales) and raise your prices accordingly. When I did the maths I needed to add less than 50c to each listing to cover the increase. So I added a dollar and called it good.

Although this rough estimate is good enough to get people started - I wanted to dive a bit deeper.

# Gathering Data

The first step was just gathering the data. I needed two data points:

- Total unit sales
- Offsite Ads Fee $

Luckily, you should be able to get both from data that Etsy provides.

## Total Unit Sales

To get total unit sales, you can go to:

Shop Manager > Settings > Options > Download Data

In the box with the 'Orders' heading, you need to select:

- CSV Type = Orders
- Year = 2020

Then hit 'Download CSV' and your browser should start downloading a CSV file with all your order info for the year 2020. In this CSV file you'll find all sorts of great data, but of interest is the 'Number of Items' column. The sum of this column is your total unit sales for the period.

**NOTE**: Etsy only rolled out the offsite ads scheme the end of [February 2020](https://www.etsy.com/seller-handbook/article/introducing-etsys-risk-free-advertising/729663416588) - so you don't want to include all orders in 2020. For my analysis, I only focused on May 2020 because that was the first month I even paid offsite ads. Read on to the next section to see when / if you're paying offsite ad fees.


## Offsite Ads Fee $

To get the total dollars paid in offsite ads fees, you can go to:

Shop Manager > Finances > Payment Account > Scroll to Bottom > 'See All Monthly Statements' > May 2020

This gives you the payment account entries for the month of May 2020. Technically you could collate multiple months of data together or choose a different month - but I stuck with May 2020 since it's only month where I had offsite ads sales.

Once you're on the May 2020 page, you can scoll down a bit till you see a box for 'All Activities for May 2020'. Here you'll notice a cloud icon with the label 'CSV' to the right of the title. Click on that to download a CSV of your payment account details.

In this CSV, the column of note is 'Type'. Whenever Type = Marketing (assuming you don't do any Etsy advertising), you'll see entries for charges related to offsite ads fees.

**NOTE**: for folks who do Etsy advertising, it may be easier to just use the dashboard and drill into the 'Marketing' category to get the breakout for offsite ads specifically - like in the screenshot below:

![payment_acct_dashboard](/etsy-offsite-ads/Pmt_Acct_Ex.png)

---

# Analysis

Okay, so now that you have the data together - it's time to figure out how much you'd need to increase prices to offset the offsite ads fee. It's pretty simple at first glance:

Offsite Ad Fees / Total Unit Sales = $ Price Increase

This is a super simplified formula that would vary depending on how similar / dissimilar the products in your store are. For my store, things are all in the same category and have similar average sale prices - so it was a straightforward calculation **that yielded a recommended price increase of 2.1%**.

**NOTE**: if you have dissimilar products (type, price, etc.) - I'd recommend segmenting them by average sale price and then doing the calculation for each segment independently.

## Incorporating TX Fees, Pmt Fees, & Offsite Ads Fees

Now the above ignores fees that would be applied to price increase for simplicity. However, if you wanted to include that in your calculation as well - then you can use this formula:

$ Price Increase / (1 - (0.08 + % Offsite Ads * 0.15)*) =  Adjusted $ Price Increase

*This expression is the sum of all Etsy platform fees that are tied to an offsite ad sale (TX Fee = 5%, Pmt Processing Fee = 3%, and Offsite Ads Fee = 15%) and incorporates the mix of offsite ad sales vs. regular sales into the offsite ads fee; more details on the fees in my [Etsy fees post](https://www.aadhi.rocks/posts/etsy-fees-2020)

**This adjusted method yielded a recommended price increase of 2.3%**.

## Sensitivity Analysis

But this initial analysis had me asking the obvious question: since the program just started - what if I see an uptick in the percent of my sales driven by offsite ads over the following months? Right now roughly 14% of orders were attributed to offsite ads. What if that jumps to 20% or more?

So to cover my bases, I did some sensitivity analysis to figure out what would happen and derived the following table:

| % Offsite Ad Sales | % Price Increase (12% Fee) | % Price Increase (15% Fee) |
|:------------------:|:--------------------------:|:--------------------------:|
|         5%         |            0.7%            |            0.8%            |
|         10%        |            1.3%            |            1.7%            |
|         15%        |            2.0%            |            2.5%            |
|         20%        |            2.7%            |            3.4%            |
|         25%        |            3.4%            |            4.3%            |
|         30%        |            4.1%            |            5.1%            |
|         35%        |            4.8%            |            6.1%            |
|         40%        |            5.6%            |            7.0%            |
|         45%        |            6.3%            |            7.9%            |
|         50%        |            7.1%            |            8.9%            |

---

# First Principles

Although all this analysis is interesting, it may not be practical. After all, Etsy is a competitive marketplace. If you had pricing power in your niche, wouldn't you have exercised it already to maximize profits?

So perhaps the question isn't 'how much should I increase prices to offset offsite ads?' as much as it is 'am I still unit profitable on an offsite ads sale?'

That reframing of the problem made me examine my unit economics on an offsite ads deal. Luckily I found that I was indeed unit profitable - even with the fee. Therefore I should be OK with keeping offsite ads enabled. Right?

Well, only if I believe offsite ads are driving truly incremental sales. Each offsite sale would need to be a sale I otherwise would not have gotten. If the customer would've ended up purchasing from me anyway - then I'm just giving away free money.

# Concluding Thoughts

But how do you test something like that? How can you test whether customers are willing to accept price increases? My answer: [split testing](https://www.optimizely.com/optimization-glossary/split-testing/).

I'm currently in the process of running some split tests on my pricing and will report back in the next few weeks on my results. If you're interested in chatting about how to run split tests for your shop - definitely feel free to reach out to me at [theminiprinter@gmail.com](mailto:theminiprinter@gmail.com)!

Till then.

# Resources

- [Etsy Offsite Ads Announcement](https://www.etsy.com/seller-handbook/article/introducing-etsys-risk-free-advertising/729663416588)
- [My Blog Post on Etsy Fees](https://www.aadhi.rocks/posts/etsy-fees-2020)
- [Split Testing Overview](https://www.optimizely.com/optimization-glossary/split-testing/)