---
title: The Two Types of Garbage In, Garbage Out
slug: gigo-garbage-in-garbage-out
pillar: when-data-goes-wrong
author: Kevin L Frank
date_published: '2026-03-16'
tags:
- foundations
- when-data-goes-wrong
- gigo
- financial-services
- credit-risk
- data-decay
- risk-management
- agricultural-lending
excerpt: Most people treat garbage in, garbage out as a single phenomenon. It isn't.
  The distinction between transactional GIGO and structural GIGO changes how you respond,
  and I learned that across two very different data quality failures.
seo_title: The Two Types of Garbage In, Garbage Out (GIGO)
seo_description: GIGO isn't one problem, it's two. Learn the difference between transactional
  and structural GIGO through real stories from WaMu's collapse and ag lending.
featured_image: images/009-gigo-garbage-in-garbage-out-featured.png
---

## Patching a Sinking Boat

Near the end of Washington Mutual's life, I was responsible for a data warehouse that ingested and distributed the bank's account information, including its loan portfolio, for analytic purposes. The inputs were already poisoned. Customer attributes were unreliable. Income figures didn't hold up under scrutiny. Demographics, net worth, credit history: none of it could be trusted at face value.

I was trying to apply patches on a boat that was already below water.

Every downstream system that consumed that data produced wrong outputs. **PD** (Probability of Default, the likelihood a borrower won't repay) was miscalculated because the borrower data was garbage. **LGD** (Loss Given Default, how much the bank loses when a borrower defaults) was wrong because the collateral and credit data feeding it was wrong. The **ALLL** (Allowance for Loan and Lease Losses) reserve calculations that depended on those inputs were unreliable.

The risk models said one thing. Reality said another.

The crisis that followed would eventually lead regulators to replace the ALLL framework entirely with **CECL** (Current Expected Credit Losses), an accounting standard requiring banks to estimate lifetime expected losses on their loan portfolios. CECL exists, at least in part, because the old framework failed so visibly at institutions like WaMu. But even CECL is only as good as the data feeding it. Better accounting standards cannot compensate for garbage inputs.

On September 25, 2008, the FDIC seized Washington Mutual Bank. It remains the largest bank failure in US history: $307 billion in assets, gone (FDIC, 2008).

The Senate's investigation later revealed the scope of the rot. WaMu's regulator had identified over 500 serious deficiencies across lending, risk management, and appraisal practices over five years, without forcing corrective action (FDIC OIG, 2010). The bank had deliberately transformed its lending profile: low-risk originations fell from 64% of the portfolio in 2003 to less than half by 2006, while high-risk originations rose to 55% over the same period, all in pursuit of higher yields on Wall Street (Senate PSI, 2011).

Staff were paid by loan volume, not loan quality. At one branch, employees manufactured borrower documents by cutting and pasting from existing client files. A peer-reviewed study later found that 48% of privately securitized loans during this era contained at least one form of fraud (Jiang et al., 2020).

That is what **garbage in, garbage out** looks like at systemic scale.

## More Than a Computing Cliché

The principle is nearly as old as computing itself. Charles Babbage wrote about it in 1864, recounting members of Parliament who asked whether his computing machine would produce correct answers from incorrect inputs. His reply: "I am not able rightly to apprehend the kind of confusion of ideas that could provoke such a question" (Babbage, 1864, cited via EBSCO). The phrase **GIGO** entered popular use in the 1950s among military engineers working with vacuum tube computers, and first appeared in print in 1963.

Most people treat GIGO as a single phenomenon: bad data in, bad results out. But working inside two very different [data quality](/blog/what-is-data-quality-and-why-should-you-care) challenges taught me that GIGO comes in two distinct forms, and the distinction changes everything about how you respond.

**Transactional GIGO** is what happened at WaMu. Bad data enters the system through flawed processes, fraudulent documentation, or broken incentives. Once those inputs are in, every downstream consumer inherits the garbage.

**Structural GIGO** is different. The data was accurate when it was captured, but the reality it describes changed. The inputs become garbage not because someone entered bad numbers, but because the world moved and the data didn't.

## Transactional GIGO: When Garbage Enters the System

The WaMu story is a textbook case. The origination process was the [failure point](/blog/where-data-quality-issues-come-from). Loan officers working under volume-based incentives had no reason to verify borrower information carefully. Appraisals were inflated. Documentation was fabricated.

The data entered the system already corrupted, and from that point forward, every calculation built on it was wrong.

The **1-10-100 rule** (Labovitz & Chang, 1992) illustrates the [cost escalation](/blog/the-true-cost-of-bad-data) as a teaching framework: the relative cost of preventing a data quality issue at the source versus correcting it after the fact versus absorbing the downstream failure. The specific ratios are heuristic, not empirical, but the pattern holds.

At WaMu, the prevention investments were never made. The $10 corrections were overwhelmed by volume. The $100 failures brought down the institution.

Transactional GIGO is not unique to banking. In healthcare, a miskeyed medication dosage or a wrong diagnostic code follows the patient through every downstream system, from treatment plans to insurance claims to clinical research datasets. A sensor miscalibrated at installation feeds bad readings into quality control systems from day one.

The pattern is the same in retail, where a product catalog with incorrect weight data cascades into shipping costs, warehouse slotting, and delivery estimates. Garbage enters at a specific point, and everything downstream inherits it.

The fix for transactional GIGO is prevention: input validation, process controls at origination, **shift-left** quality checks (embedding validation as early as possible in the data lifecycle, at the point of creation rather than downstream) that catch garbage before it enters the system. The problem has a point of entry, and that's where you stop it.

## Structural GIGO: When Good Data Goes Stale

After WaMu, I went to RaboAgrifinance, a subsidiary within the Rabobank group focused on agricultural lending, where I established and managed the Enterprise Data Warehouse. One of the projects I worked on addressed the quality of collateral data for agricultural loans. The data quality challenge there was fundamentally different from what I had seen at WaMu, and it wasn't a failure. It was a structural reality of the business.

In ag lending, the collateral is often the crop in the field or the herd in the pasture. One storm, one frost at the wrong time, or a few weeks of drought can cut the value of a crop significantly. A cattle herd can be decimated by disease before spring.

A surprisingly good growing season can push collateral values well beyond projections. International events, trade disputes, and commodity price swings can move valuations in either direction overnight.

The collateral data was generally accurate when it was captured. But last quarter's accurate valuation no longer reflected reality, and the LGD calculations built on that data drifted with it. Not because of a data entry failure, but because of **data decay**: the gap between what the data says and what the world now looks like.

The OCC's Comptroller's Handbook specifically addresses this, requiring periodic reevaluation of ag collateral with increased frequency during periods of price volatility (OCC). This same concept of data aging over time is one of the [six dimensions of data quality](/blog/the-6-dimensions-of-data-quality): timeliness, the question of whether data is current enough to be useful for its intended purpose.

This is part of what makes agricultural lending a specialized discipline. The uncertainty in collateral data makes ag lending unsuitable for institutions that cannot manage constant data volatility, and it makes risk analysis and planning genuinely difficult. It is also part of the reason specialized ag lenders exist: they build the competencies, processes, and data infrastructure to handle what general-purpose banks typically cannot.

Structural GIGO shows up well beyond agriculture. A patient's medication list captured during one visit may no longer be accurate by the next. Demand forecasts built on pre-pandemic purchasing patterns became instantly unreliable in early 2020; the models were sound, but the world they described had changed overnight. Property valuations captured during a rising market can become dangerously optimistic within months if conditions shift, a dynamic that contributed directly to the 2008 crisis.

Industry research estimates that general business data decays by roughly 30% per year as people change jobs, companies restructure, and contact details go stale (Data Axle via Landbase, 2025). A campaign targeting last year's accurate customer profiles is mailing into the void.

The fix for structural GIGO is entirely different from transactional GIGO. Better input validation won't help when the inputs were correct at the time. You need continuous revalidation, refresh cycles tied to the volatility of the underlying asset, and monitoring that flags staleness rather than just accuracy at the point of entry.

## Why the Distinction Matters

In practice, many GIGO problems combine both types. A system that ingests bad data (transactional) and then never refreshes it (structural) compounds the damage. The value of the distinction is not that every case fits neatly into one category. It is that it forces you to ask whether the problem is at the point of entry, in the aging of the data, or both.

Organizations that treat all GIGO as transactional will invest in input quality controls and still get garbage out, because their data aged past its shelf life. Organizations that treat all GIGO as structural will build monitoring and refresh cycles but leave the front door open for bad data to walk in.

The interventions are different:

- **Transactional GIGO** responds to input validation, process governance, shift-left quality checks, and incentive alignment at the point of data creation.
- **Structural GIGO** responds to refresh cadences, decay monitoring, revalidation triggers, and shelf-life policies tied to how fast the underlying reality changes.

The downstream consequences are identical regardless of type. Whether you are calculating PD, estimating LGD, or building CECL reserves under today's accounting standards, none of those outputs care whether the input data was born bad or aged into it. Wrong is wrong, and the decisions built on wrong data carry the same risk either way.

Babbage observed this principle in the 1860s, when the stakes were printed mathematical tables. At WaMu, the stakes were $307 billion. The stakes are growing again as AI enters the picture.

Garbage training data looks like transactional GIGO; model drift from a changing world shares characteristics with structural GIGO. The analogy is imperfect (model drift covers concept drift, distribution shift, and upstream schema changes that go well beyond simple data staleness), but the underlying truth remains: outputs cannot be better than inputs, and the [principle scales with the technology](/blog/gartner-2026-data-quality-in-the-age-of-ai).

## Key Takeaways

- **GIGO is not one phenomenon but two.** Transactional GIGO (bad data enters the system) and structural GIGO (good data decays because reality changes) require fundamentally different responses. Treating them as the same problem leads to investments that address only half the risk.
- **Transactional GIGO is a prevention problem.** The 1-10-100 rule (Labovitz & Chang, 1992) shows that catching garbage at the source is orders of magnitude cheaper than fixing it downstream. WaMu's collapse illustrates what the $100 end of that spectrum looks like at institutional scale.
- **Structural GIGO is a freshness problem.** Data that was generally accurate when captured becomes garbage when the world it describes changes. Agricultural collateral, patient health records, customer contact data, demand forecasts: anything tied to a volatile reality faces this risk. This is not a failure of the people entering data; it is a structural characteristic of the domain.
- **The downstream consequences don't care about the cause.** PD, LGD, and CECL calculations produce wrong numbers whether the inputs were born bad or aged into it. Risk models are only as good as the data feeding them, regardless of how the data became garbage.
- **The principle scales with technology.** What Babbage observed in the 1860s now collapses banks and threatens AI systems. The stakes grew; the underlying truth didn't change.

## Sources

1. FDIC. "Status of Washington Mutual Bank Receivership." *FDIC*, 2008. https://www.fdic.gov/bank-failures/status-washington-mutual-bank-receivership
2. U.S. Senate Permanent Subcommittee on Investigations. "Wall Street and the Financial Crisis: Anatomy of a Financial Collapse." April 2011. https://fraser.stlouisfed.org/title/wall-street-financial-crisis-anatomy-a-financial-collapse-5094
3. FDIC Office of Inspector General. "Evaluation of Federal Regulatory Oversight of Washington Mutual Bank." Report No. EVAL-10-002, April 2010. https://www.fdicoig.gov/sites/default/files/reports/2022-08/10-002EV.pdf
4. Jiang, W., Matvos, G., Piskorski, T., and Seru, A. "Ten Years of Evidence: Was Fraud a Force in the Financial Crisis?" *American Economic Association*, 2020. https://www.aeaweb.org/content/file?id=13538
5. Labovitz, George and Yu Sang Chang. The 1-10-100 Rule of Data Quality, 1992. Referenced via: Matillion, "The 1:10:100 rule of data quality: A critical review for data professionals." 2024. https://www.matillion.com/blog/the-1-10-100-rule-of-data-quality-a-critical-review-for-data-professionals
6. Office of the Comptroller of the Currency. "Agricultural Lending." *Comptroller's Handbook*. https://www.occ.treas.gov/publications-and-resources/publications/comptrollers-handbook/files/agricultural-lending/pub-ch-agricultural-lending.pdf
7. EBSCO Research. "Garbage in, garbage out (GIGO)." *EBSCO Research Starters, Computer Science*. https://www.ebsco.com/research-starters/computer-science/garbage-garbage-out-gigo
8. Data Axle via Landbase. "B2B Data Decay Statistics." *Landbase*, 2025. Referenced for the ~30% annual business data decay rate.

## What's Next

GIGO extends beyond bad numbers into bad assumptions. The next post in this chain, **Bias in Data**, examines what happens when the garbage going in isn't random noise but systematic distortion: biased training data, skewed samples, and the ways that structural inequities get encoded into datasets and amplified by the systems that consume them.

If you're thinking about what GIGO means for autonomous systems, **Agentic AI and Data Quality** explores how the principle becomes more dangerous when AI agents act on data without human review. When a person sees a suspicious number, they can pause and investigate. When an agent sees the same number, it acts.

For the foundation this post builds on, see [Where Data Quality Issues Come From](/blog/where-data-quality-issues-come-from), which introduces the three origin types (human error, systemic failure, and deliberate manipulation) that feed GIGO at the source.
