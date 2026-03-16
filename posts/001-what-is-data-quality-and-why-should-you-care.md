---
title: What Is Data Quality and Why Should You Care?
slug: what-is-data-quality-and-why-should-you-care
pillar: strategy-leadership
author: Kevin L Frank
date_published: ''
tags:
- foundations
- data-governance
- data-quality-dimensions
excerpt: Data quality touches everything from family photo albums to pandemic response
  to space missions that cost hundreds of millions of dollars. Here's what it really
  means, and why it should matter to you.
seo_title: What Is Data Quality? Definition & Why It Matters
seo_description: Learn what data quality means, why it matters for every organization,
  and how poor data has derailed space missions, banks, and public health responses.
featured_image: images/001-what-is-data-quality-and-why-should-you-care-featured.png
---

## A Shoe Box Full of Questions

I recently opened an old shoe box of pictures from my mother's family in Maine. The photos were all 75 years old or older: black-and-white snapshots of people standing on porches, sitting at kitchen tables, squinting into summer sun.

Someone had written names on the back of each picture. At least, I think they had. The writing was no longer legible. Faded ink on aging paper, decades past the point of being useful.

So I found myself staring at a young girl in one of the photos and asking: Is that my grandmother? A great-aunt? Some other distant relative? Maybe a friend of the family who ended up in our picture box by accident?

The photos themselves were fine. But the **metadata** (the data about the data, the writing that told you who was in each picture) had deteriorated beyond recovery. Without it, the photos went from family history to a box of strangers, some with familiar features, some without.

That's a data quality problem. And it's one that most people would never think to call by that name. But after a long career working with data, I see data quality, metadata, structured data, and unstructured data where others see family photos.

## Data Quality Is Everywhere

Data quality isn't just a problem for databases and data warehouses. It shows up anywhere data is created, stored, or used. In practice, that means everywhere.

Consider banking. In 2022, the Consumer Financial Protection Bureau ordered Wells Fargo to pay $3.7 billion after finding that the bank had incorrectly applied consumer payments on auto loans, in some cases for over a decade. The misapplied payments triggered wrongful late fees and incorrect interest charges. Customers saw negative marks on their credit reports, and some had their vehicles wrongfully repossessed.

The errors affected more than 11 million accounts, and it took years to unwind the damage, not because any single error was large, but because the downstream consequences compounded across millions of accounts and multiple billing cycles (CFPB, 2022).

Or consider something as simple as a mailing address. When a retailer's customer database has duplicate records ("123 Main St" vs. "123 Main Street, Apt 2"), the result isn't just wasted postage. The marketing team makes decisions based on inflated customer counts, and the data warehouse can't answer a basic question: how many customers do we actually have?

These aren't edge cases. They're the kinds of problems that data professionals deal with every day, across every industry. And sometimes the consequences go far beyond an inconvenience.

## When 16,000 COVID Cases Disappeared

In October 2020, in the middle of a global pandemic, Public Health England discovered that nearly 16,000 positive COVID-19 test results had gone unreported over the course of a week. The cause was a data processing pipeline that used Microsoft Excel as an intermediate step. Because the legacy .xls file format had a maximum row limit of approximately 65,000, the extra cases were silently dropped once the volume of test results exceeded that limit (*The Register*, 2020).

No error message. No warning. The data just stopped being captured.

The consequence was immediate and serious: approximately 48,000 close contacts of those infected individuals were never notified. People who should have been isolating went about their daily lives, unaware of their exposure, during one of the most critical periods of the pandemic.

The full story is more complex than a single spreadsheet limit. It involved architectural decisions about why a mission-critical public health pipeline was running through Excel at all, and organizational choices about data formats and validation. Those are important questions, and they point to a pattern that shows up across every industry: tools and processes that work fine at small scale can break silently when volume grows.

But fundamentally, this was a **completeness** failure. The data that *was* captured was perfectly accurate. It just wasn't all there, and nobody knew until it was too late.

## When Bad Data Costs Hundreds of Millions

If you want an example of what happens when data quality fails at an engineering scale, look no further than NASA's Mars Surveyor '98 program.

The program cost $327.6 million and comprised two spacecraft: the Mars Climate Orbiter and the Mars Polar Lander (NASA NSSDCA, 2024). In 1999, after nearly 10 months of travel to Mars, the Climate Orbiter approached the planet on a trajectory that brought it to approximately 57 kilometers altitude, far lower than the planned 150 to 200 kilometers needed for orbit insertion. At that altitude, atmospheric drag destroyed the spacecraft (NASA, 2024).

The cause? One team's software produced thruster data in imperial units (pound-force seconds). Another team's system expected that data in metric units (newton-seconds). The inconsistency in units was an undetected disaster silently waiting to reveal itself over the entire 10-month journey.

No one entered bad data. No one made a typo. The values were technically correct in their own context.

But when two systems used different standards and nobody caught the mismatch, a spacecraft was lost. Two months later, the Mars Polar Lander was also lost during its landing attempt, for unrelated reasons. The entire $327.6 million program investment was gone.

That's data quality. Not just "is the data right?" but "is the data right *in context*?" (That question of context is becoming even more important as AI systems consume data without human judgment to compensate. See [AI Didn't Replace Data Quality. It Raised the Bar.](/blog/gartner-2026-data-quality-in-the-age-of-ai) for how the Gartner 2026 summit framed this shift.)

## Dimensions of Quality, and Why They're Just the Starting Point

If you've read anything about data quality before, you've probably seen a list of dimensions: **accuracy**, **completeness**, **consistency**, **validity**, **timeliness**, and **uniqueness**. These are real and important, and we'll explore each of them in depth across this series.

But in practice, applying these dimensions requires judgment and contextual interpretation. They're not a checklist you run through mechanically; they're a framework for thinking about what can go wrong and why it matters.

My shoe box photos were *accurate*: real photographs of real people. They were *complete*: every photo was intact. But the metadata had degraded, and without it, the photos lost much of their meaning.

You could call that a completeness failure (information is missing) or an integrity failure (the relationship between the photo and its label is broken). It depends on how you frame it. The point is that real-world problems don't always announce which dimension they belong to, and data professionals need to think beyond a rote checklist.

The UK COVID data was *accurate* for every case that made it into the spreadsheet. The problem was that 16,000 cases never made it in at all. That's a completeness failure, but not one caused by someone leaving a field blank. The system itself silently dropped the data.

The NASA orbiter's data was *accurate* and *complete* in each system. The problem was *consistency* across systems, and the consequence was the loss of a mission that cost hundreds of millions of dollars. Data quality is contextual. The dimensions that matter most depend on what you're trying to do with the data, who's using it, and what's at stake when it's wrong.

## One Part of a Bigger Picture

Data quality doesn't exist in isolation. It's one of several interconnected knowledge areas in **data management** (the discipline of managing data as a valuable organizational asset). **Data governance** (the set of practices, policies, and standards an organization uses to manage its data) sits at the center, coordinating areas like data architecture, metadata management, data security, master data management, and data quality.

If you're familiar with the **DAMA-DMBOK2** framework (a thorough reference from the Data Management Association that maps these knowledge areas around a central governance hub), you'll recognize data quality as one of those areas, deeply connected to every other one (DAMA International, 2017).

Poor data quality undermines your security classifications. Weak metadata management makes quality harder to measure. Inconsistent architecture creates the conditions for the kind of cross-system mismatch that doomed the Mars orbiter. And as my shoe box reminded me, even the best data is only as useful as the metadata that gives it context.

Over the course of this blog, we'll explore how data quality connects to each of these areas, and how they all connect back to each other.

## What's Ahead

This is the first post in what I'm planning as an extended series on data quality, with dozens of topics and a list that keeps growing as we go deeper.

Some of those posts will be technical, walking through SQL queries for data profiling and validation checks you can build into your deployment pipeline. Others will be strategic, focused on making the business case for data quality investment and building a culture that takes it seriously. And a few will be exploratory, asking questions you might not expect: What happens when data is technically correct but contextually misleading? What can missing data tell us?

What I hope is that these posts become more than something you read and move on from. Data quality is a conversation. I'd welcome your thoughts, your experiences, and your perspectives on what data quality means to you, whether you're a data engineer writing pipeline checks, a business leader making decisions from dashboards, or someone who just opened a shoe box and wished the handwriting was still legible.

## Key Takeaways

- **Data quality isn't just a technical problem.** It affects everything from personal family history to pandemic response to space exploration, and everything in between.
- **The standard dimensions (accuracy, completeness, consistency, etc.) are a starting point, not the full picture.** They're a framework for thinking, not a mechanical checklist. Real-world problems require judgment about which dimensions apply and how.
- **Context determines quality.** Data can be "correct" in isolation and still cause failures when systems, standards, or expectations don't align. The COVID data was accurate; it just wasn't all there. The NASA data was accurate; it was just measured in the wrong units.
- **"Correct" means different things in different contexts.** Some processes demand exact matches down to the penny. Others work within acceptable tolerances. The key is knowing which situation you're in, and not assuming "close enough" is fine without understanding what's at stake.
- **Data quality is one part of a larger data management ecosystem.** It connects to, and depends on, governance, architecture, metadata, security, and every other discipline in data management.
- **This is a conversation, not a lecture.** Across this series, we'll explore these topics together. Your experience and perspective matter.

## Sources

1. Consumer Financial Protection Bureau. "CFPB Orders Wells Fargo to Pay $3.7 Billion for Widespread Mismanagement of Auto Loans, Mortgages, and Deposit Accounts." *CFPB Newsroom*, 20 December 2022. https://www.consumerfinance.gov/about-us/newsroom/cfpb-orders-wells-fargo-to-pay-37-billion-for-widespread-mismanagement-of-auto-loans-mortgages-and-deposit-accounts/
2. NASA. "Mars Climate Orbiter." *NASA Science*, 2024. https://science.nasa.gov/mission/mars-climate-orbiter/
3. NASA. "Mars Climate Orbiter — NSSDCA/COSPAR ID: 1998-073A." *National Space Science Data Center*, 2024. https://nssdc.gsfc.nasa.gov/nmc/spacecraft/display.action?id=1998-073A
4. Karabus, Jude. "What a Hancock-up: Excel spreadsheet blunder blamed after England under-reports 16,000 COVID-19 cases." *The Register*, 05 October 2020. https://www.theregister.com/2020/10/05/excel_england_coronavirus_contact_error/
5. DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge.* 2nd Edition, 2017. https://www.dama.org/cpages/body-of-knowledge

## What's Next

Now that we've established what data quality is and why it matters, the next post digs into the numbers: [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) quantifies the financial and operational impact that poor data quality has on organizations, with some statistics that might surprise you.

If you're curious about the dimensions we mentioned (accuracy, completeness, consistency, and the rest), we'll give each one a thorough treatment in upcoming posts.
