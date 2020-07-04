---
title: "A/B on Etsy: Raising Prices"
date: 2020-06-15
summary: Ramen isn't cutting it anymore.
tags: ["etsy", "a/b testing", "miniprinter"]
slug: "a-b-testing-etsy-pricing-jun-2020"
draft: false
---

Pricing is a powerful lever for any business.

However, since I launched [MiniPrinter](https://www.etsy.com/shop/miniprinter) (my business selling 3D printed D&D miniatures on Etsy) - I'd never played with pricing. After some eye opening analysis in my [breakdown of Etsy fees](https://www.aadhi.rocks/posts/etsy-fees-2020), I realized it may be time to thinking about raising prices or I'd be stuck with a slightly profitable side hustle instead of a real business.

So I decided to ask the question: **can I raise prices without affecting sales?**

# Experiment Setup

To find an answer to the question, I used a tool most in the web world are familiar with - [A/B testing or split testing](https://www.optimizely.com/optimization-glossary/split-testing/). The setup is pretty straightforward. 

Every hour I'd switch prices between option A ($9.50) and option B ($10.00) on a select group of listings. This price switching is automated by some code I wrote. During each price switch, my code will also note down the change in the following two data points since the last price switch: 

- Views
- Sales

After a period of three weeks, I'd look at both of these data points for A & B by day and hour to determine if there's a statistically significant difference. If there is - then I can raise prices without worrying about a drop in sales. For reference, I'm using a common benchmark (95% confidence or p-value of < 0.05) to determine statistical significance.

# Results

Here are the descriptive stats for views:

|   | Mean | Std Dev |  N  |
|---|:----:|:-------:|:---:|
| A | 0.46 |   0.84  | 257 |
| B | 0.46 |   0.84  | 257 |

**p-value = 1

And for sales:

|   | Mean | Std Dev |  N  |
|---|:----:|:-------:|:---:|
| A | 0.03 |   0.17  | 257 |
| B | 0.01 |   0.09  | 257 |

**p-value = 0.055

# Commentary

So what are these tables telling me? 

Well, the views table is telling me that there's no difference in terms of listing click throughs when I raise prices. **That's good.** The table for sales is telling me that there's pretty damn near statistical significance on sales being lower when I raise prices. **That's bad.**

Now, to maintain the integrity of the experiment - I should conclude that I can raise prices without affecting sales since the p-value was less than my initially set threshold (< 0.05). But come on. It's so damn close.

So let's assume for a moment that the results were indeed statistically significant. The data is telling me that I should expect 3x lower average sales at a price point of $10.00 (B) vs. $9.50 (A). Combining this data with the fact that sales at my current $9.50 price point net me $3.00 in profit, I can make a decision on whether raising prices is advisable.

Breaking down the analysis into two step - let's first look at the loss from raising prices to $10.00. For every sale I'd do at that price point, I'd lose two potential sales. This means I should expect a loss of $6.00. However, that loss is slightly offset in the second step by the increased in price ($0.50). Unfortunately, that's still a net loss of $5.50 as a result of raising prices.

# Next Steps

To summarize, the analysis has told me that **I can't raise prices without reducing my profits**. It's a bummer, because at current price points, the volume of sales I'd need to generate have to increase significantly to make MiniPrinter into a real business. Could it be done? Sure - but it'd take a long long time (10+ years) for a relatively small reward.

However, the analysis did open my eyes to other possibilities. Notably - is there some sort of [anchoring effect](https://www.pon.harvard.edu/daily/negotiation-skills-daily/the-drawbacks-of-goals/) when shoppers search for D&D minis on Etsy? I did some research and noted most other shops don't offer free shipping on every listing. Rather they offer free shipping on cart values above $35. This creates a gap between my pricing (includes average shipping cost of $3 in the list price) versus my competition (doesn't include shipping in list price).

For example: if customers look at all the other D&D minis being offered and see an average sale price of $7 and see mine sitting at $10 - perhaps the anchoring on $7 makes mine seem 'expensive', even though the overall cost to the customer is the same.

To test that hypothesis, I'm going to try to switch my shop to free shipping on orders above $35 and 'reduce' my prices to $8.50. I have reduce in quotes, since it's an effective price increase of $1.50 - but looks like a reduction on first glance to customers.

Will it work? Who knows - but there's only one way to find out: try it!