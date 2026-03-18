---
title: What Makes Data Good?
slug: what-makes-data-good
pillar: understanding-your-data
author: Kevin L Frank
date_published: '2026-03-18'
tags:
- foundations
- understanding-your-data
- fitness-for-purpose
- data-quality-dimensions
- data-usability
excerpt: Data can pass every quality check and still be useless. The six dimensions
  tell you whether data is correct. Fitness for purpose tells you whether it's useful.
  You need both.
seo_title: What Makes Data Good? Beyond the Six Dimensions
seo_description: The six data quality dimensions aren't enough. Learn why fitness
  for purpose, interpretability, and context determine whether data is actually useful.
featured_image: images/010-what-makes-data-good-featured.png
---

## When Every Check Passes and the Data Is Still Wrong

A team in New York sends a dataset to a team in London. One of the columns contains dates: "03/04/2026." The New York team means March 4th. The London team reads April 3rd.

The data is accurate (those are real dates). It's complete (no missing values). It's consistent (every row uses the same format). It's timely, valid, and unique. Run it through the [six dimensions of data quality](/blog/the-6-dimensions-of-data-quality) and it passes every check. But when the London team schedules a product launch for the wrong month, the data has failed them in a way that no dimension score would have caught.

I've seen a version of this play out firsthand. At a mid-sized regional bank in the Mountain West, we ran our servers and tools on Mountain Time for all data processing. Then a vendor built new pipelines for our enterprise data warehouse and built everything around UTC. Suddenly, a subset of our data arrived timestamped in a completely different standard. The data was accurate. It was complete. It passed every check. But our developers had to remember which pipelines used which time zone, and every spring and fall it got worse: the U.S. shifts to daylight saving time on a different date than UTC adjusts, so for a few weeks each year our processes were offset by a different number of hours than the rest of the year. We had to divert development resources to fix timing mismatches, and every code change introduced its own risk to processing and data quality.

[The previous post](/blog/the-6-dimensions-of-data-quality) gave you the vocabulary to describe what's wrong with data: accuracy, completeness, consistency, timeliness, validity, uniqueness. That vocabulary is essential. But it answers only one question: *is this data correct?* [The first post in this series](/blog/what-is-data-quality-and-why-should-you-care) introduced the idea that quality is always contextual. This post gives that principle the full practical treatment and asks the next question: *is this data good enough to actually use?*

## Correct Is Not the Same as Useful

In 1996, researchers Richard Wang and Diane Strong asked a question that the data quality field had been sidestepping: what do the people who actually *use* data think quality means? Instead of defining quality from a theoretical perspective, they surveyed data consumers directly. Through iterative sorting and consolidation, participants identified 118 attributes that mattered to them, which the researchers grouped into 15 dimensions across four categories (Wang and Strong, 1996).

The four categories reframe how we think about quality:

- **Intrinsic quality:** The data is correct in its own right. Accuracy, believability, objectivity, reputation. The traditional six dimensions live mostly here.
- **Contextual quality:** The data fits the task. Relevance, timeliness, completeness, and having the right amount of data for the purpose at hand.
- **Representational quality:** The data is presented in a way people can work with. Interpretability, ease of understanding, consistent formatting, conciseness.
- **Accessibility quality:** People can actually get to the data when they need it, with appropriate security controls.

Think of it like a restaurant. The six dimensions are food safety: the kitchen is clean, the ingredients are fresh, everything is stored at the right temperature. Food safety is essential and non-negotiable. But it doesn't make a good meal. A three-year-old's birthday party needs chicken nuggets, small portions, and paper plates. A board of directors celebrating a transformative acquisition needs a multi-course dinner, full place settings, and a private dining room. Both meals can be equally food-safe. Only one is right for the occasion. Context determines quality.

Intrinsic quality (correctness) is the foundation. Contextual, representational, and accessibility quality are what make data actually useful.

## Context Changes Everything

The same dataset can be perfectly good for one team and useless for another. That isn't a flaw in the data. It's the nature of **fitness for purpose**.

A few examples of how context shifts the quality bar:

Your sales team pulls daily transaction data. The finance team needs weekly summaries for their report. The data is correct, but it's at the wrong **granularity** for the consumer. Someone has to aggregate it, and if they aggregate it wrong, the finance report is off.

Your CRM defines a "customer" as anyone who has entered the sales pipeline, including prospects. Your billing system defines a "customer" as anyone who has received an invoice. Both definitions are accurate within their own systems. Join the two datasets without understanding this **semantic difference**, and you'll count prospects as paying customers.

A patient allergy field is blank. In a billing workflow, that's a minor gap. In a clinical workflow, it could be life-threatening. The completeness problem is identical. The risk is entirely different because the **context** changed. ([The 6 Dimensions of Data Quality](/blog/the-6-dimensions-of-data-quality) made this same point about completeness being context-dependent; fitness for purpose generalizes that principle across all data characteristics.)

I ran into another version of this at Rabobank. Our data warehouse team delivered data in two forms: reports for people and extracts for other systems. The distinction mattered because each required different specialists and different requirements gathering. But departments would routinely request a "report" when what they actually needed was a machine-readable extract. We'd assign the reporting team, start the project, and then discover mid-stream that the consumer wasn't a person reading a dashboard; it was an automated process ingesting a flat file. Knowing *who* or *what* is consuming the data, and in what format, changes the entire definition of quality. A beautifully formatted PDF is perfect for a human and useless for an API.

Gartner's research reinforces this. Their data quality model arranges dimensions in a hierarchy: accessibility first, then timeliness, then relevance, and accuracy last (Medd, 2024). The logic is straightforward: there's no point perfecting the accuracy of data that nobody can access, that arrives too late, or that isn't relevant to the task. Accuracy depends on the other three being established first.

## What the Six Dimensions Don't Cover

The six dimensions we covered in the previous post aren't the only ones recognized by the field. DAMA-DMBOK2 lists additional dimensions including **reasonableness** (does this value make sense in context?), and Wang and Strong's original research identified 15 (DAMA International, 2017). Rather than adding more dimensions to memorize, it helps to think about three qualities that sit on top of the six:

**Interpretability.** Can the consumer understand what the data means without calling the person who created it? A column labeled "Sales" with no currency indicator could mean USD, EUR, or GBP. A field named "CUST_STS_CD" makes perfect sense to the source team and nothing to anyone else. If the data requires a phone call to decode, it isn't good enough, no matter what the dimension scores say.

**Relevance.** Is this the right data for this specific task? Gartner puts it directly: checking the accuracy of irrelevant data wastes time and energy, diverting resources from fixing accuracy for the data that actually matters (Medd, 2024). Relevance is what connects data quality effort to business outcomes.

**Appropriate representation.** Is the data in a format, granularity, and structure that serves the consumer's purpose? The date format problem from the opening is a representation failure. So is delivering raw event logs when someone needs a summary dashboard, or providing data in a proprietary format that the consumer's tools can't read.

These three qualities aren't theoretical. They create real tensions in practice, and one of the most common is the collision between accessibility and security. Sensitive fields like names, SSNs, account numbers, and TINs are often masked from developers. That's good security practice. But many of those fields serve as natural keys, and when they're masked, referential integrity breaks during unit testing, integration testing, and QA. I've encountered this problem more times than I can count. Two approaches help: **tokenization**, which replaces real values with tokens that preserve referential integrity across tables, and **attribute-based access controls**, where service accounts see real data while human users see masked values. Neither is perfect, but both acknowledge that "good data" sometimes means balancing competing quality needs, with security and usability pulling in opposite directions.

These qualities aren't a replacement for the six dimensions. They're a follow-up question: after you've confirmed the data is correct, ask whether it's actually useful for the person who needs it.

## A Practical Test

Here is a simple fitness-for-purpose check you can apply to any dataset, report, or pipeline output:

1. **Who is the consumer?** Data serves different people differently. The same customer list means one thing to marketing, another to finance, and another to compliance. Knowing the consumer tells you which quality attributes matter most.

2. **What decision does this data support?** This connects data quality to a business outcome. If the decision is "which accounts to prioritize this quarter," you need recency and completeness. If the decision is "did we meet regulatory reporting requirements," you need accuracy and auditability. The decision defines the quality bar.

3. **Can the consumer use this data without calling you?** This is the interpretability test. If your data needs a glossary, a phone call, or institutional knowledge to make sense, it isn't fit for purpose yet. Good data comes with enough context that someone outside your team can work with it.

A 2024 survey found that 77% of organizations cited data-driven decision-making as their leading goal, but only 46% reported high trust in the data used for those decisions (TDWI, 2024). Separately, 67% of data leaders reported they lack complete trust in their data for decision-making (Precisely, 2025). That trust gap isn't always a dimension failure. Sometimes the data is correct but not trusted because it isn't understood, isn't relevant to the decision at hand, or isn't in a format the consumer can work with.

## Key Takeaways

- **The six dimensions are necessary but not sufficient.** Data can pass every dimension check and still be useless if it doesn't fit the consumer's context. Correctness is the foundation; fitness for purpose is what makes data actually useful.
- **"Good data" is not an absolute.** The same dataset can be good for one purpose and inadequate for another. Quality always depends on who is using the data and what decision it supports.
- **Interpretability matters as much as accuracy.** If the consumer can't understand the data without asking the creator, the data isn't good enough, regardless of what the dimension scores say.
- **Context changes the quality bar.** A missing field that's irrelevant in one workflow can be life-threatening in another. Quality standards should be calibrated to how data is used, not applied uniformly across every dataset.
- **Apply the three-question test.** Who is the consumer? What decision does this support? Can they use it without calling you? These questions catch fitness-for-purpose problems that dimension checks miss.

## Sources

1. Wang, R.Y. and Strong, D.M. "Beyond Accuracy: What Data Quality Means to Data Consumers." *Journal of Management Information Systems*, Vol. 12, No. 4, 1996. https://www.tandfonline.com/doi/abs/10.1080/07421222.1996.11518099
2. Medd, Jason. "What Data Architects Need to Know About Data Quality." *Gartner*, 29 July 2024. ID G00810669.
3. TDWI. "2024 State of Data Quality Report." *TDWI Research*, 2024. https://tdwi.org/research/2024/05/diq-all-2024-state-of-data-quality-report.aspx
4. Precisely. "Data Quality Challenges: 2025 Planning Insights." *Precisely Blog*, 2025. https://www.precisely.com/blog/data-integrity/2025-planning-insights-data-quality-remains-the-top-data-integrity-challenges/
5. DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge.* 2nd Edition, 2017. https://www.dama.org/cpages/body-of-knowledge

## What's Next

Now that you know what makes data correct *and* what makes it useful, the next question is how to measure both. [Measuring Data Quality](/blog/measuring-data-quality) will cover the practical side: formulas, thresholds, and building measurement into your regular processes.

If you haven't read it yet, [The 6 Dimensions of Data Quality](/blog/the-6-dimensions-of-data-quality) covers the foundation this post builds on. And for a look at how AI is raising the bar on what "fit for purpose" means, see [AI Didn't Replace Data Quality. It Raised the Bar.](/blog/gartner-2026-data-quality-in-the-age-of-ai)
