---
title: The True Cost of Bad Data
slug: the-true-cost-of-bad-data
pillar: strategy-leadership
author: Kevin L Frank
date_published: '2026-03-06'
tags:
- foundations
- cost-of-bad-data
- business-case
- data-quality-ROI
excerpt: Bad data doesn't just cause headaches. It causes nine-figure fines, shuttered
  expansions, and abandoned business lines. Here's what poor data quality actually
  costs, with stories from the inside.
seo_title: 'The True Cost of Bad Data: Real Stories & Numbers'
seo_description: Discover the real cost of bad data through insider stories of nine-figure
  fines, failed expansions, and the 1-10-100 rule that every data leader should know.
featured_image: images/002-the-true-cost-of-bad-data-featured.png
---

## I Watched Bad Data Help Destroy a Bank

Before I led the build of the data warehouse (the central reporting database) at Rabobank N.A. (RNA), the bank's data infrastructure had significant gaps. Transaction monitoring systems were thin. Reporting was limited. And critically, suspicious activity data that should have been captured and surfaced to senior leadership simply was not.

At the Calexico, California branch, located roughly two blocks from the U.S.-Mexico border, hundreds of millions of dollars in suspicious cash were flowing through accounts. One customer alone funneled more than $100 million in transactions that should have triggered investigation (DOJ, 2018). The branch was one of the bank's "highest performing" in the region, and the cash abundance from cross-border activity was a big reason why.

The data to identify these patterns existed in fragments across the bank's systems. But it was never properly captured, connected, or made visible to the people in the organization who had the authority and responsibility to act on it. That gap created the conditions for everything that followed.

The public record eventually revealed deliberate choices that made the problem worse. RNA maintained a "Verified List" of roughly 1,000 customers whose transactions were not to be questioned, regardless of what the data showed. Managers imposed daily quotas for clearing alerts that made meaningful investigation impossible. The bank had only three employees investigating over 2,300 alerts each month (ACFCS, 2022). Executives who commissioned an external review of the compliance program deleted, delayed, and altered the consultant's findings before the OCC could see them. Employees who raised questions were demoted or fired (ACFCS, 2022).

Those were failures of leadership and compliance, and they were serious. But consider what made them possible: the absence of reliable, visible data. If suspicious activity had been properly captured and communicated to the right people at the right time, the controls designed to catch it would have had something to work with. When critical data is not collected and surfaced, the organization loses its ability to self-correct. Bad actors thrive in data gaps. The compliance failure was real, but the data failure is what allowed it to persist unchecked for years.

## $418.7 Million and an Exit From American Banking

The consequences came in waves.

In February 2018, RNA pleaded guilty to a federal felony conspiracy charge and agreed to pay $368,701,259 in forfeiture, the largest financial penalty in the history of the Southern District of California. The OCC separately assessed a $50 million civil money penalty (OCC, 2018). Individual executives were also penalized, including a lifetime banking ban for the former General Counsel (ACFCS, 2022).

That was the direct cost. The indirect costs were larger.

A bank operating under consent orders (binding regulatory agreements that restrict operations) and federal scrutiny cannot pursue a growth strategy. In March 2019, Rabobank sold RNA to Mechanics Bank for approximately $2.1 billion (Mechanics Bank, 2019). To be clear: the $2.1 billion was the sale price, not money lost. Rabobank retained its U.S. agribusiness lending and wholesale operations under Rabobank North America, but the retail banking franchise it had spent decades building was gone. The real cost was the loss of strategic optionality, the constrained negotiating position, and a forced exit from American retail banking. By September, every RNA branch carried the Mechanics Bank name.

Think of it like a building where the smoke detectors had dying batteries. The alarms went off, but only three people were listening for the entire building, and management had posted a list of rooms where alarms should be ignored. The people with the authority to evacuate never heard a thing. By the time regulators broke down the door, the damage wasn't just the fire. It was the explosion: fines, lost growth, divestiture, and a forced exit from American retail banking. The missing detectors didn't start the fire. But they are the reason nobody stopped it in time.

To be clear: I am not asserting that better data visibility alone would have prevented the money laundering at RNA. The public record shows deliberate choices by people who knew what they were doing. But preventative controls are dependent on good data being visible to the right people at the right time. At RNA, that data was not visible to the right people, so the controls designed to catch suspicious activity had nothing to work with.

Bad data costs don't stay in one category. They cascade.

## The Pattern Is Bigger Than One Bank

My experience at RNA isn't unusual in its shape, only in its scale. The research on the cost of poor data quality tells a consistent story across industries.

Gartner estimates that poor data quality costs large enterprises an average of $12.9 million per year, based on a survey of 154 reference customers of data quality vendors (Gartner, 2020). The actual cost varies widely by size and industry. IBM estimated the aggregate cost to the U.S. economy at $3.1 trillion annually in a widely cited 2016 analysis; no updated figure has been published, but data volumes have grown substantially since then (IBM, 2016). And Thomas Redman's research for Harvard Business Review found that only 3% of companies' data meets basic quality standards, with 47% of newly created records containing at least one work-impacting error (Redman, 2017).

Those numbers can feel abstract, so here is a concrete example of what they look like in practice.

**Target Canada** entered the Canadian market in 2013 with 133 stores. Merchandisers had to enter approximately 75,000 products into a new SAP system (enterprise software for managing inventory and supply chain), and the work was assigned to junior merchandising assistants with limited experience. Data accuracy in the Canadian system was estimated at just 30%, compared to 98-99% in Target's U.S. system (Dolfing, 2019).

The errors were mundane: product dimensions listed in the wrong order, imperial and metric units confused, costs calculated in the wrong currency. But mundane errors at scale produce spectacular failures. Store shelves sat empty while warehouses overflowed with inventory that the system could not route correctly.

By 2015, all 133 Canadian stores had closed. Approximately 17,600 employees lost their jobs. Total losses reached $2.1 billion, with some estimates running as high as $7 billion (Retail in Detail, 2024).

Target Canada had multiple problems: an overly aggressive rollout, uncompetitive pricing, questionable real estate choices. But with only 30% data accuracy in its inventory system, even a better strategy would have struggled. When your systems can't tell you what's on your shelves or what fits in your shipping containers, everything else falls apart.

## The Costs That Don't Make Headlines

The examples above are dramatic because they ended in public penalties or shuttered stores. But most of the cost of bad data is quieter than that.

**Productivity drain** is the largest hidden cost. Estimates suggest that knowledge workers spend roughly half their time dealing with data issues: finding the right data, correcting errors, or seeking a second source to confirm what they're seeing (Redman, 2017). Nobody budgets for this, but it shows up everywhere: missed deadlines, slower decisions, teams that never get to their strategic priorities.

**M&A integration** is where hidden data costs hit hardest in my experience. Across several bank acquisitions I worked on, I saw a recurring pattern when two institutions' data assumptions collided. In one acquisition, the acquiring bank's reporting relied on account opening dates for regulatory and management purposes. After the deal closed, the team discovered that the acquired bank's internal accounts (general ledger accounts, not customer-facing ones) had never enforced the opening date field. It existed in the database structure but was routinely left blank or filled with placeholders.

When that data migrated, reports that had worked reliably for years broke. A field that nobody at the acquired bank thought about turned out to be load-bearing in the acquiring bank's infrastructure. In PwC's 2023 M&A Integration Survey, 59% of companies reported spending 6% or more of deal value on integration, up from 38% in the prior survey (PwC, 2023). In my experience, data quality problems drive a significant share of those costs, and they tend to surface after the deal has already closed.

**AI and machine learning projects** are the newest casualty. According to S&P Global, 42% of companies abandoned most of their AI initiatives in 2025, up from 17% in 2024 (S&P Global, 2025). That survey found cost and data security among the top factors.

A separate Informatica CDO survey, as reported by WebProNews, found that 43% of Chief Data Officers cited data quality and readiness as a top obstacle to AI success (WebProNews, 2025). Across both studies, data quality is consistently one of the most commonly cited barriers. You cannot skip the data quality work and expect AI to compensate. (The [Gartner 2026 Data & Analytics Summit](/blog/gartner-2026-data-analytics-summit-key-takeaways) reinforced this message: "AI-ready data" is now a higher bar than traditional data quality, and 60% of AI projects are being abandoned for lack of it.)

## The 1-10-100 Rule: A Framework for Thinking About Prevention

George Labovitz and Yu Sang Chang proposed a simple framework in 1992 that still holds up in principle: the **1-10-100 Rule**.

- It costs **$1** per record to prevent a data quality issue at the point of entry.
- It costs **$10** per record to find and correct the issue after the fact.
- It costs **$100** per record (or more) when the issue is never corrected and drives downstream failures.

The specific dollar amounts are illustrative, not empirical measurements. The rule is a teaching heuristic, not a pricing formula. Some practitioners now argue that the absolute costs at every stage are significantly higher in modern cloud environments, where prevention requires more sophisticated tooling and a single bad record can propagate across dozens of downstream systems instantly (Matillion, 2024). But the underlying principle has held up for over three decades: the earlier you catch a data quality issue, the cheaper it is to fix.

If you want to start making this case inside your organization, here is a practical approach:

1. **Pick one business process** that depends on data (customer onboarding, financial reporting, inventory management).
2. **Measure the error rate** in the data that feeds it. Even a rough estimate is useful.
3. **Estimate the cost per error.** How much time does each error take to investigate and fix? What downstream decisions does it affect?
4. **Multiply.** Error rate times volume times cost per error gives you an annual cost estimate for that single process.
5. **Compare to prevention cost.** What would it cost to validate data at the point of entry for that process?

Most teams that run this exercise are surprised. The cost of bad data is almost always higher than anyone assumed, and prevention is almost always cheaper than expected.

## Key Takeaways

- **Bad data costs cascade.** A data gap becomes a compliance failure becomes a business crisis. The RNA and Target Canada stories both follow this pattern: when critical data isn't captured and made visible, the organization loses the ability to self-correct, and small gaps escalate into outcomes that reshape entire organizations.
- **Large enterprises lose an average of $12.9 million per year to poor data quality** (Gartner, 2020), and only 3% of companies meet basic data quality standards. This is not a niche problem; it is a baseline condition of most organizations.
- **Direct penalties are only the visible cost.** Productivity drain, M&A integration failures, and abandoned AI initiatives represent the bulk of what bad data actually costs, and none of those show up in a headline.
- **Data that works in one context can break in another.** The bank acquisition story and the Target Canada example both illustrate that data quality is not an absolute property. It depends on the system, the assumptions, and the stakes.
- **Prevention is dramatically cheaper than failure.** The 1-10-100 Rule gives leaders a simple framework to quantify this for their own organizations. Start with one process, measure the error rate, and do the math.

## Sources

1. U.S. Department of Justice. "Rabobank NA Pleads Guilty, Agrees to Pay Over $360 Million." *DOJ Office of Public Affairs*, 7 February 2018. https://www.justice.gov/opa/pr/rabobank-na-pleads-guilty-agrees-pay-over-360-million
2. Office of the Comptroller of the Currency. "OCC Assesses $50 Million Civil Money Penalty Against Rabobank, N.A." *OCC News Release NR-OCC-2018-15*, 7 February 2018. https://www.occ.gov/news-issuances/news-releases/2018/nr-occ-2018-15.html
3. ACFCS. "Enforcement Spotlight: OCC Completes Rare C-Suite Sweep at Rabobank." *ACFCS*, 2022. https://www.acfcs.org/enforcement-spotlight-with-fine-against-ceo-occ-completes-rare-c-suite-sweep-at-rabobank-with-prior-penalties-against-cco-general-counsel
4. Mechanics Bank. "Mechanics Bank Completes Acquisition of Rabobank, N.A." *Mechanics Bank News*, 3 September 2019. https://www.mechanicsbank.com/about-us/who-we-are/news-press/2019-news-articles-press-releases/mechanics-bank-completes-acquisition-of-rabobank-na/
5. Dolfing, Henrico. "Case Study: The $2.5 Billion Cross-Border Expansion Mistake by Target." *henricodolfing.com*, 2019. https://www.henricodolfing.com/2019/09/case-study-target-canada-failure.html
6. Retail in Detail. "Bullseye Missed: How Bad Data Took Down Target in Canada." *retailindetail.ca*, 2024. https://www.retailindetail.ca/post/bullseye-missed-how-bad-data-took-down-target-in-canada
7. Gartner. "Data Quality." *Gartner*, 2020. https://www.gartner.com/en/data-analytics/topics/data-quality
8. IBM. "The True Cost of Poor Data Quality." *IBM Think*, 2016. https://www.ibm.com/think/insights/cost-of-poor-data-quality
9. Redman, Thomas C. "Only 3% of Companies' Data Meets Basic Quality Standards." *Harvard Business Review*, September 2017. https://hbr.org/2017/09/only-3-of-companies-data-meets-basic-quality-standards
10. Making Strategy Happen. "The Cost of Quality: The 1-10-100 Rule." *Making Strategy Happen*, 2020. https://www.makingstrategyhappen.com/the-cost-of-quality-the-1-10-100-rule/
11. S&P Global Market Intelligence. "AI Experiences Rapid Adoption, but with Mixed Outcomes." *S&P Global*, 2025. https://www.spglobal.com/market-intelligence/en/news-insights/research/ai-experiences-rapid-adoption-but-with-mixed-outcomes-highlights-from-vote-ai-machine-learning
12. WebProNews. "Poor Data Quality to Cause 42-85% AI Project Failures in 2025." *WebProNews*, 2025. https://www.webpronews.com/poor-data-quality-to-cause-42-85-ai-project-failures-in-2025/
13. PwC. "M&A Integration Survey 2023." *PwC*, 2023. https://www.pwc.com/us/en/services/consulting/deals/library/ma-integration-survey.html
14. Matillion. "The 1:10:100 Rule of Data Quality: A Critical Review for Data Professionals." *Matillion*, 2024. https://www.matillion.com/blog/the-1-10-100-rule-of-data-quality-a-critical-review-for-data-professionals

## What's Next

If you haven't read the first post in this series, [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care) covers the foundational concepts (the six dimensions, why context matters, and how data quality fits into the broader data management picture).

Coming up next, we'll look at where data quality issues actually come from. Spoiler: it's not always an accident. Bad data can come from human mistakes, from systems and processes that were never designed to prevent it, and sometimes from people who made it bad on purpose. The origin changes everything about how you respond.
