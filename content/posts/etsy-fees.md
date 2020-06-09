---
title: "Analyzing Etsy Fees (2020)"
date: 2020-06-05
summary: Nickles and dimes.
tags: ["etsy"]
slug: "etsy-fees-2020"
draft: false
---

There's no shortage of discussion on the complex fee structure that Etsy has for sellers. Just do a quick search of the [Etsy subreddit for 'fees'](https://www.reddit.com/r/Etsy/search?q=fees&restrict_sr=1) and you'll see what I mean.

As a seller on Etsy(https://www.etsy.com/shop/miniprinter) since Dec 2019, I empathize. It's hard enough to run a business. You don't want to spend your time calculating fees. You want to spend your time figuring out how to better serve your customers and grow. 

I'm in this camp. Although I'm embarassed to say this - I never spent much time figuring out how much Etsy actually takes in platform fees. I just saw that I was netting positive in my account balance and thought it was around roughly 6%. 

But with the [not-so-recent change in off-site ads fees](https://www.ecommercebytes.com/2020/03/14/etsy-enrolls-all-sellers-in-its-new-offsite-ads-program/), I thought it'd be good to know for sure. So I sat down today and did some indepth analysis of the Etsy fee structure. 


# Fixed & Variable

One way to look at these fees is to separate them into fixed and variable fees in terms of list price.

A fixed fee would be something like the listing fee. It's $0.20 no matter what I do to the price of the listing. On the other hand, a variable fee would be the transaction fee - which is 5% of the list price. It'll go up or down as I change the list price respectively.

Using this lens, here's how the costs break out for a sale:

**Fixed**

- Listing Fee ($0.20)
- Payment Processing Fee (1) ($0.25)

**Variable**

- Transaction Fee (5% of list price)
- Payment Processing Fee (2) (3% of list price)
- Offsite Ads Fee* (15% or 12% of list price)

*This fee only applies if your shop has ever generated $10K+ in sales over 365 rolling days (12% fee), at which point you'll be signed up for the lifetime of your store **OR** you've never hit the $10K in sales threshold and aren't opted out of the program (15% fee)

Note that the payment processing fee has two components - one that's fixed  ($0.25 / sale) and one that's variable (3% of list price).

# Sale Analysis

Okay so now that I know the fees involved, I ran the numbers on an average sale in my shop. With a sell price of $10, **Etsy takes 27.5%**. That's massive. Definitely higher than the 6% I expected. Here's how the costs break out:

- Listing Fee = $0.20
- Payment Processing Fee (1) = $0.25
- Transaction Fee = $0.50
- Payment Processing Fee (2) = $0.30
- Off-Site Ads Fee = $1.50

As you can tell, the lions share is coming from the Off-Site Ads fee. If I decide to opt out of the program, then Etsy's take immediately drops down to 12.5%. Still higher than 6%, but a 2x jump - not 4.5x.

# Sensitivity Analysis

After the extent of fees on my sales sunk in, I thought about next steps. Etsy's fee structure has fixed and variable elements, so I started considering what effect increasing prices would have on the overall % taken.

Think about it this way. If you go to an ATM (not your bank's) that has a fixed $3.00 fee for withdrawing - you want to withdraw more rather than less. Assuming it's all the same to you. Said another way, you'd rather withdraw $100 and pay 3% in fees rather than withdraw $10 and pay 30% in fees. Assuming you didn't mind having $100 on your person.

So I ran some sensitivity analysis using Excel and got this table*:

| List Price | Etsy's Fee (%) |
|------------|:---------------:|
| $2.00      |      30.5%      |
| $4.00      |      19.3%      |
| $6.00      |      15.5%      |
| $8.00      |      13.6%      |
| $10.00     |      12.5%      |
| $12.00     |      11.8%      |
| $14.00     |      11.2%      |
| $16.00     |      10.8%      |
| $18.00     |      10.5%      |
| $20.00     |      10.3%      |

---
**Assumes no off-site ads*

Like I suspected, you can lower Etsy's take if you can **successfully** increase prices. However:

1. It's not easy to raise prices
2. There's diminishing returns

The second point is most obvious to see if you look at the difference in lowering Etsy's fee % by raising prices from $2.00 to $4.00 (-11.3 DIFF) versus $18.00 to $20.00 (-0.3 DIFF). Here's a graph for the visually inclined:

![etsy_fee_reduction](/etsy-fees/fee_reduction.png)

# Next Steps

What does this all mean? Well, two clear actions to take could be:

1. Opt out of off-site ads
2. Raise prices

BUT, these actions only make sense **if they don't affect sales / conversions**. Is that possible? Perhaps. There's only one way to find out: try it out and look at the data. 

I plan on doing separate split test experiments to see how opting out of off-site ads affects my traffic and similarly - how increasing pricing affects traffic on listings.

# Resources

- [Etsy Fee Calculator](https://www.alura.io/resources/etsy-fee-calculator)
- [Etsy's Fee Page](https://www.etsy.com/legal/fees/)
