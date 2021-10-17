---
layout: post
description: A look into the econimics and financial dynamics of Olympus' Ohm monetary reserve system with contrasting examples from the fiat reserve system 
title: Ohmmmm, that seems like the FED
categories: [finance, economy, cryptocurrency, ethereum]
permalink: /post/:year/:month/:day/:title
toc: true
hide: true
---

Recently I have been dabbling a bit more into cryptocurrencies finding interesting projects and communities. Of course, there is the investment portion of it, but there is also the educational and pure interest part of it. Since I've been more into economics and finance lately and being a part of what media likes to call the digital generation, cryptocurrency has become more attractive as an interest. One of the most economically interesting cryptocurrency project that I have gotten to know is the [Olympus] project. What makes it interesting is that it is a project that is trying to become a monetary reserve system of Ethereum, that is, it is tyring to become a [FED](https://en.wikipedia.org/wiki/Federal_Reserve)-like entity, with cryptocurrency and decentralization twist along with a different monetary policy outlook

In this post I would like to help readers (you) better understand Olympus's economic models and their implications, to the best of my ability and understanding

Note that I will be using several cryptocurrency terminologies which may seem foreign to those that have never delved into cryptocurrencies before. Such terminologies will be _italicized_

> Disclaimer: I am not affiliated with Olympus, nor do I own (at the time of this writing) any investments in Olympus's products. I am not a financial advisor, and you should not take the content here as investment advise. The information and opinions in this post are solely mine, and are published for informational purposes

# Ohm: A backed currency

`Ohm` is the currency circulated by Olympus. It is a currency that is backed against assets held in the Olympus treasury of which currently primarily consits of _stablecoins_, _liquidity provider (LP) tokens_, and several accepted cryptocurrencies. To be more precise, it is not the assets that Ohm is backed against, but a guaranteed amount of value that Ohm calls this the [Risk-Free Value](https://docs.olympusdao.finance/main/references/glossary#rfv) derived out of the market value of these assets. See [RFV formula](https://docs.olympusdao.finance/main/references/equations#backing-per-ohm)

So what does it mean to be backed? Is the value of `Ohm` supposed to equal the value or `RFV` of the assets? That's not the case. In fact Olympus explicitly made it clear that `Ohm` is a [free-floating currency](https://policonomics.com/lp-exchange-rate-regimes-free-float/#:~:text=A%20free%20floating%20exchange%20rate,government%20intervention%20is%20totally%20inexistent.) with a market driven market rate. If `Ohm`'s value is enforced to be 1-to-1 correspondent to the value of the backing assets, it's value will be `$1`. However, Olympus is giving a guarantee that every `Ohm` out there will always be redeemable for **AT LEAST** `$1`. This is the price floor of `Ohm`, or in other words its current intrinsic value to be `$1`. Theoretically in general, it is possible for the price floor of `Ohm` to be above `$1`

Olympus makes this possible precisely because of the `RFV` in the treasury, that can be used to buy any circulating `Ohm` for `$1`, or theoretically in general any price floor e.g `$100`. Essentially, if `Ohm`'s price ever goes down below `$1`, a seller can go to Olympus and sell it for `$1` which Olympus buys using the treasury assets it has accumulated. Additionally, by buying `Ohm` Olympus can remove the purchased `Ohm` out of circulation through a _burning_ process (algorithmic removal of a token supply). So in addition to the price increase pressure from Olympus being a so-called **buyer of last resorts**, the price of the still circulating `Ohm` will eventually get back to its intrinsic value

# Ohm: An inflationary currency

I mentioned previously how `Ohm`'s market price is free-floating and possibly above `$1`. The market price is the market price, it is a price that is determined by market outlook, sentiment and supply and demand. If `Ohm` is seen as a useful and productive currency, it's price has a chance to go up. In fact, it is natural for such a currency to increase in price over time all else being equal. The `USD` for example, is a valuable currency used to transact across many countries and regimes around the world for all kinds of assets and commodities and used as various countries cash reserves. At times when there are high demand for the `USD` you would expect its price, relative to some other currency to increase.

While price increase sounds nice for primarily an investment asset, price increase relative to goods, services and other assets are deflationary. For example:

> If with 10 `Ohm` you can buy 10 apples, but then the price of Ohm increases 10 times while the price of apples stays the same, then that same 10 `Ohm` can now buy 100 apples. The value of apples has deflated subjective to `Ohm`

The problem with deflation is that it encourages indefinite hoarding. If you are acclimated to prolonged a deflationionary pricing environment you would likely eventually be led to believe that deflation is the state of nature. The result is that you would start to believe that the asset that you hold will be worth more tomorrow than it is today, and your neighbours and everyone else with their assets would think the same. The rational next step is for everyone to not consume or divest the value of that asset and just hoard! But clearly this is problematic for a currency, whose objective is in large part to be spent!

In order to combat the deflationary aspect caused by a potential market price increase, Olympus has set out `Ohm` to be an inflationary currency, which means that Olympus literally mints more `Ohm` over time. In order to mint more `Ohm`, Olympus provides a staking program (covered more later), that gradually mints more `Ohm` at a variable rate. Essentially you can think of this as making a deposit into an account with a variable interest rate

Now, you may think that this is bad since the consequence of minting more of `Ohm` means that there is a price reduction pressure, and that is true! But this is a feature of `Ohm`, not a bug. The point of minting more of `Ohm` is to ensure an adequate supply of `Ohm` in the ecosystem. With an inflationary currency, or hence a deflationary currency in value, holders will be incentivized over time to spend `Ohm` instead of hoarding it. As `Ohm` is used more and more as a currency being used to transact and purchase goods and services, there will be more demand for `Ohm`. This demand will lead to some price increase support, but more importantly it requires `Ohm` to be present to be used widely and as conveniently as possible. Inflationary supply helps make that possible

Now lastly, remember the previous section where I talked about the `RFV`. While Olympus mints `Ohm`, it is algorithmically made to mint only to the point that the amount of `Ohm` in circulation matches the `RFV` in treasury. The reason is because 1 `Ohm` is backed by `$1`. Not minting more `Ohm` than the `RFV` would help ensure that every `Ohm` can be sold back for `$1`

# Staking: The monetary supply tool

# Quick comparisons with the FED and modern monetary system

- The FED is also the issuer of currency
- The banks create money, Olympus is both reserve and money creator
- Olympus says that it's money is backed by real assets, USD is backed by nothing. This is not quite true since the USD can be seen as backed by **future** spending, and the production of the economy. Likewise, Olympus reserves backed by the belief in cryptocurrency economy, and hence likewise for `Ohm`

Things to follow up on:

- What happens to the APY and staking when the price of Ohm increases?
- What happens to the APY and staking when the price of Ohm decreases?
