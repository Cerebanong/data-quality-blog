---
title: The 6 Dimensions of Data Quality
slug: the-6-dimensions-of-data-quality
pillar: understanding-your-data
author: Kevin L Frank
date_published: '2026-03-15'
tags:
- foundations
- data-quality-dimensions
- understanding-your-data
- data-quality-framework
excerpt: When someone says 'the data is bad,' nobody knows what that means. The six
  dimensions of data quality give you the vocabulary to describe exactly what's wrong,
  and that vocabulary is what turns vague complaints into problems you can actually
  fix.
seo_title: The 6 Dimensions of Data Quality Explained
seo_description: Master the six dimensions of data quality — accuracy, completeness,
  consistency, timeliness, validity, and uniqueness — with practical examples and
  analogies.
featured_image: images/005-the-6-dimensions-of-data-quality-featured.png
---

## When "The Data Is Bad" Isn't Enough

Early in my career at Washington Mutual, roughly seven years before its seizure during the 2008 financial crisis, I worked on a project to migrate a charge-back process from an old Access database to a modern data warehouse. The process calculated how departments used corporate space across more than a dozen states and millions of square feet, driving financial charges meant to incentivize efficiency.

When we ran the new system in parallel with the old one, the results looked good. Aggregate totals were close, just a few dollars off. We ran it for several weeks. The numbers were always close but always off, anywhere from a few cents to a few dollars, wandering in either direction.

Our CFO wasn't satisfied. Even now, more than 20 years later, I remember his exact words: *"We are a bank, and if you are off by even a penny, you are off. Find the problem and fix it."*

He didn't say "the data is bad." He named the exact problem: the numbers didn't match, and in banking, a penny matters. That specificity is what made the problem solvable.

We traced the issue to intermediate calculations that weren't carrying enough significant figures. Small rounding differences accumulated across millions of square feet and hundreds of facilities. Once we added enough precision to those intermediate steps, the new process matched the old one to the penny.

The **six dimensions of data quality** give every organization that same kind of specificity. They turn "the data is bad" into something you can investigate and fix. [The first post in this series](/blog/what-is-data-quality-and-why-should-you-care) introduced these dimensions briefly. This post gives each one the full treatment it deserves.

## The Six Dimensions: A Framework, Not a Checklist

The concepts behind these six dimensions (accuracy, completeness, consistency, timeliness, validity, and uniqueness) have been discussed in data quality literature for decades. A **DAMA** (Data Management Association) UK working group consolidated them into a widely cited standard set in 2013 (DAMA UK, 2013), and the DAMA-DMBOK2 incorporates them as part of a broader data quality assessment framework (DAMA International, 2017). Other frameworks define more dimensions (some identify dozens), but these six capture the core of what most data quality conversations need.

Here's what matters more than the definitions: these dimensions are a way of thinking, not a mechanical checklist. When 47% of newly created records contain at least one critical error (Redman, 2017), knowing which dimension failed is the difference between a targeted fix and a frustrated shrug.

## Accuracy: Does It Match Reality?

**Accuracy** is the degree to which data correctly represents the real-world thing it describes (DAMA International, 2017). The Washington Mutual story from the opening is fundamentally an accuracy problem, but it also shows how neatly real problems refuse to stay in one box. The input data was accurate. The processing introduced the error.

A reader could just as easily call it a consistency problem (two systems that should agree didn't) or a validity problem (the rounding rules didn't meet required precision standards). That overlap is the point: the dimensions give you vocabulary to describe different facets of the same problem.

The WaMu story also introduces accuracy's close cousin: **precision**. Accuracy asks whether your result matches the true value. Precision asks whether your process produces consistent results each time.

Our new system was imprecise: the rounding errors in intermediate calculations wandered differently with each run, sometimes a few cents high, sometimes a few dollars low. That imprecision made the final results inaccurate. We caught the problem because two methods that should have produced identical numbers didn't. The inconsistency between methods was the clue; the insufficient significant figures were the cause; the wrong totals were the consequence.

Accuracy often requires a validated reference point to verify against. At WaMu, the old Access database served as that reference; its results had been reconciled against financial reports for years, giving us confidence it reflected reality. When no validated reference exists, reasonableness checks are the next best option: if a person's height is recorded as 15 cm, something is clearly wrong, even without checking the original source (GOV.UK, 2021).

## Completeness: Is Everything There?

**Completeness** measures whether all the data you need for a specific purpose is present. A jigsaw puzzle with 3 pieces missing might still show you the overall picture. A puzzle with 300 pieces missing is useless. The question isn't "is every field populated?" but "are the fields that matter for this task filled in?"

This distinction is context-dependent. A missing allergy field in a patient record could be life-threatening. A missing middle name in a marketing database is an inconvenience (GOV.UK, 2021). Completeness also operates at multiple levels: a single field can be empty (field completeness), an entire record can have gaps (record completeness), expected records can be missing from a dataset (dataset completeness), entire tables can be absent from a database, or a full day's data from a source system might never arrive at the data warehouse. That last one is more common than you'd think, and it often goes unnoticed until someone asks why yesterday's numbers look off.

The COVID-19 reporting failure from [Post 1](/blog/what-is-data-quality-and-why-should-you-care) was a completeness problem. Every record that made it into the system was accurate. 16,000 records simply never made it in. You can have perfect accuracy and still fail on completeness.

## Consistency: Do the Systems Agree?

**Consistency** is whether the same data tells the same story across different records and systems. Picture every clock in an office building. If the lobby clock reads 2:00, the conference room clock reads 2:07, and your phone reads 1:58, you can't be sure when the meeting starts. No single clock is necessarily "wrong," but they disagree, and that disagreement creates problems.

Two types matter here. **Internal consistency** means data doesn't contradict itself within a single record (a UK postcode's first characters should match the locality of the address). **Cross-system consistency** means the same data element matches across multiple systems (a customer's phone number should be identical in the CRM (customer relationship management system) and the order management system) (IBM, 2025; GOV.UK, 2021).

Cross-system consistency is especially hard in organizations with legacy systems or a history of acquisitions. **BCBS 239** is an international standard with 14 principles covering how banks aggregate and report risk data, spanning governance, accuracy, completeness, timeliness, and consistency across systems. As of 2023, only 2 of 31 global systemically important banks fully met all 14 principles (Basel Committee, cited via Gable.ai, 2024). If the world's largest and best-resourced banks struggle with cross-system data quality, the challenge is real for everyone.

The Mars Climate Orbiter loss from [Post 1](/blog/what-is-data-quality-and-why-should-you-care) was a consistency failure: two teams, two unit systems, one destroyed spacecraft.

## Timeliness: Is It Fresh Enough?

**Timeliness** is whether data is current enough to be useful for its intended purpose. Think of a weather forecast. Yesterday's forecast was perfectly accurate, yesterday. But if you're deciding whether to bring an umbrella today, yesterday's forecast tells you nothing.

The data hasn't changed; its usefulness has expired.

What "timely" means depends entirely on context. A stock trading system needs data updated in milliseconds. A quarterly financial report can work with data that is weeks old. Hospital bed management needs real-time updates; healthcare capacity planning can use quarterly figures (GOV.UK, 2021).

Data also decays on its own. Industry estimates suggest that general business data loses accuracy at a rate of roughly 30% per year, and B2B contact information decays at approximately 70% annually (Data Axle, cited via Landbase, 2025). These rates primarily reflect data elements that change over time: contact information, job titles, product catalogs, and organizational affiliations. (Transactional records and historical facts don't decay the same way; a completed sale is still a completed sale.)

Think of a product catalog: every year, products are discontinued, new ones are added, prices change, and suppliers update their codes. The catalog you published last year no longer reflects what's actually available, even though nobody introduced an error. The same thing happens to contact lists, customer records, and reference data across your organization.

## Validity: Does It Follow the Rules?

**Validity** checks whether data conforms to defined formats, types, and constraints. It's like filling out a form that requires a phone number in the format (XXX) XXX-XXXX. You might enter a real phone number, but if you write "555-1234" without the area code, the form rejects it. Validity checks structure, not truth.

Types of validity rules include: format rules (does the data follow the right pattern?), range rules (does a value fall within acceptable bounds?), business rules (does a birthday fall in the past, not the future?), and referential rules (does a reference in one table point to a valid record in another? For example, an address form that validates state or territory codes against an official list, so no one can enter "ZZ" as a state) (IBM, 2025; GOV.UK, 2021).

One distinction worth calling out explicitly: **valid data is not necessarily accurate data.** A ZIP code of "85001" is perfectly valid. It's the correct format, five digits, and it exists in the USPS database. But if that ZIP code is attached to an address in New York, it's inaccurate, because 85001 is in Phoenix, Arizona.

The data passes every structural check and is still wrong. This confusion between validity and accuracy trips up more data teams than almost any other concept. Validity answers "does this data follow the rules?" Accuracy answers "does this data reflect reality?" You need both, and they are not the same thing.

## Uniqueness: Is Each Record Distinct?

**Uniqueness** means each record in a dataset represents one distinct real-world entity, with no unintended duplicates. Think of checking a party guest list. If "Robert Smith" and "Bob Smith" both appear at the same address, is that one person listed twice or two different people?

Get it wrong and you either set too few places or too many. At scale, with thousands or millions of records, the ambiguity compounds fast.

Deduplication is harder than it sounds. "123 Main St" and "123 Main Street, Apt 2" could be the same location or different units. "John Smith" and "Jon Smith" could be the same person or a father and son. Fuzzy matching (algorithms that compare similar but not identical values) helps, but no approach is perfect.

The costs add up. Industry estimates, aggregated from healthcare surveys and vendor research, put the picture in perspective: large healthcare systems may experience 15-16% duplicate rates in patient records, with each duplicate costing roughly $1,950 to resolve (Black Book Research; TechTarget, cited via Landbase, 2025). The exact numbers vary by institution size and complexity, but the pattern is consistent: duplicates inflate customer counts, waste outreach budgets, and undermine any analysis that depends on knowing how many distinct entities you actually have.

## Dimensions Don't Work in Isolation

Real-world data problems rarely fall neatly into one dimension. A consistency failure (different systems disagree about a customer's address) might mask an accuracy problem (one of the addresses is flat-out wrong). Missing records in a dataset can make uniqueness impossible to assess (you can't deduplicate what you don't have). And a validity check might catch what is actually a timeliness issue (a once-valid product code that the catalog has since retired).

The root cause categories from [the previous post](/blog/where-data-quality-issues-come-from) also map to these dimensions. Human error most commonly affects accuracy (typos, transpositions) and completeness (fields left blank). Systemic failures tend to surface as consistency and completeness problems (silent data drops, cross-system mismatches). Deliberate manipulation can target any dimension but often hits accuracy (fabricated values) or uniqueness (duplicate records created to inflate metrics).

The $12.9 million that poor data quality costs large enterprises each year, based on a Gartner survey of data quality vendor reference customers (Gartner, 2020), isn't distributed evenly across the six dimensions. Some organizations bleed money from accuracy failures. Others lose it to completeness gaps or cross-system inconsistencies. Knowing which dimensions hurt you most is how you prioritize where to invest.

## Key Takeaways

- **The six dimensions are a vocabulary, not a checklist.** They let you move from "the data is bad" to "our customer address accuracy is 87% and our order record completeness dropped to 91% this quarter." That precision is what makes problems fixable.
- **Valid data is not necessarily accurate data.** A ZIP code can be perfectly formatted, exist in a real database, and still be attached to the wrong address. Validity checks structure. Accuracy checks truth. You need both.
- **Completeness is context-dependent.** A missing allergy field in a patient record is a safety risk. A missing middle name in a marketing database is a minor inconvenience. What counts as "complete enough" depends entirely on what you're using the data for.
- **Dimensions interact in the real world.** A consistency failure between two systems might hide an accuracy problem in one of them. A completeness gap makes it impossible to assess uniqueness. Fixing one dimension sometimes reveals problems in another.
- **Data decays on its own.** Contact information, job titles, product catalogs, and organizational affiliations all change over time. Industry estimates suggest business data loses roughly 30% of its accuracy each year (Data Axle, cited via Landbase, 2025). Quality is not a one-time achievement; it requires ongoing attention.
- **AI is raising the bar.** The six dimensions remain the foundation, but AI use cases require additional dimensions like semantic clarity, diversity, and lineage that most DQ programs don't measure yet. [AI Didn't Replace Data Quality. It Raised the Bar.](/blog/gartner-2026-data-quality-in-the-age-of-ai) explores how the six dimensions hold up in the AI era and what DQ professionals should be doing differently.

## Sources

1. DAMA UK Working Group. "The Six Primary Dimensions for Data Quality Assessment." *DAMA UK*, 2013. https://www.sbctc.edu/resources/documents/colleges-staff/commissions-councils/dgc/data-quality-deminsions.pdf
2. DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge.* 2nd Edition, 2017. https://www.dama.org/cpages/body-of-knowledge
3. UK Government Data Quality Hub. "Meet the Data Quality Dimensions." *GOV.UK*, 2021. https://www.gov.uk/government/news/meet-the-data-quality-dimensions
4. IBM. "What Are Data Quality Dimensions?" *IBM Think*, 2025. https://www.ibm.com/think/topics/data-quality-dimensions
5. Redman, Thomas C. "Only 3% of Companies' Data Meets Basic Quality Standards." *Harvard Business Review*, September 2017. https://hbr.org/2017/09/only-3-of-companies-data-meets-basic-quality-standards
6. Gartner. "Data Quality." *Gartner*, 2020. https://www.gartner.com/en/data-analytics/topics/data-quality
7. Landbase. "Duplicate Record Rate Statistics: 32 Key Facts Every Data Professional Should Know in 2026." *Landbase*, 2025. https://www.landbase.com/blog/duplicate-record-rate-statistics
8. Gable.ai. "Financial Data Quality: Modern Problems and Possibilities." *Gable Blog*, 2024. https://www.gable.ai/blog/financial-data-quality-management

## What's Next

Now that you have the vocabulary, the next question is: how do you put numbers on these dimensions? [Measuring Data Quality](/blog/measuring-data-quality) will cover the practical side, from formulas and thresholds to building measurement into your regular processes.

If you want to understand where these quality problems originate, [Where Data Quality Issues Come From](/blog/where-data-quality-issues-come-from) breaks down the three root cause categories: human error, systemic failure, and deliberate manipulation. And for the financial stakes, [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) puts real dollar figures on what happens when quality breaks down.
