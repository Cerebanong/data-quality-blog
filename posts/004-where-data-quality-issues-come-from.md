---
title: Where Data Quality Issues Come From
slug: where-data-quality-issues-come-from
pillar: when-data-goes-wrong
author: Kevin L Frank
date_published: '2026-03-06'
tags:
- foundations
- root-causes
- when-data-goes-wrong
- data-quality-framework
excerpt: 'Every data quality issue traces back to one of three origins: human error,
  systemic failure, or deliberate manipulation. Understanding where data quality issues
  come from changes how you detect, diagnose, and respond to bad data.'
seo_title: 'Where Data Quality Issues Come From: 3 Root Causes'
seo_description: Every data quality issue traces to human error, systemic failure,
  or deliberate manipulation. Learn to diagnose root causes with real-world case studies.
featured_image: images/004-where-data-quality-issues-come-from-featured.png
---

## The Welder's Three Questions

In the mid-1990s, I was working for Quest Environmental at the former U.S. Air Force station in King Salmon, Alaska. We were decommissioning underground storage tanks that had held jet fuel. The process was straightforward: a contractor cleaned and flushed each tank, I tested the air inside with an **OVM** (organic vapor meter, a handheld instrument that detects volatile organic compounds), and if the readings were safe, a welder cut holes in the tank, then an excavator crushed it.

The welder was a careful man. Before he would strike an arc on a tank that had held jet fuel, he wanted to know three things.

Could I have made a mistake reading the instrument? That's human error. Could the OVM itself be giving bad readings, maybe a calibration issue or a failing sensor? That's a systemic problem. And the one he asked with the most edge: could I be lying about the numbers to keep the project on schedule?

I told him I would stand right next to the tank while he cut it. If my data was wrong, I would be the first to know.

The tank didn't explode. My data was good. But the welder's three questions have stayed with me for thirty years because they map perfectly to where data quality issues come from, not just on an Alaskan job site, but in every database, pipeline, and report I've worked with since.

**Human error. Systemic failure. Deliberate manipulation.** Those are the three origins of bad data. The list of specific causes is practically infinite: typos, null values, schema changes, pipeline bugs, sampling errors, mismatched field definitions, and hundreds more. But nearly every one of them traces back to one of these three categories. And the category matters, because it changes everything about how you respond.

One thing this post is not about: what happens when accurate data gets misinterpreted or misused. That's a separate problem, one where the data itself is fine but the conclusions drawn from it are wrong. It's important, and this series will address it, but it's a different conversation from where the data quality issues originate.

## The Fumble: When People Make Mistakes

These are the ones most people picture when they think about bad data. A clerk transposes two digits in a phone number. A technician records a sample ID in the wrong column. Someone copies a formula and pastes it one row off.

IBM reports that manual data entry error rates range from 0.55% to 26.9% depending on the context (IBM, 2025). The low end reflects structured data entry with validation controls (dropdown menus, format masks). The high end reflects free-text entry under time pressure, where humans are typing fast with no system checking behind them. Even at half a percent, a table with a million rows contains five thousand errors before anyone downstream touches it.

Human errors are random. They don't favor one direction over another. A transposed digit is just as likely to make a number too high as too low.

That randomness is actually useful: accidental errors tend to show up in statistical checks. Outlier detection, range validation, and duplicate analysis all catch mistakes that follow no pattern.

The harder question is speed. In most organizations, accidental errors are constant. Someone is entering them right now. The goal isn't zero errors; it's finding them before they reach a decision.

Future posts in this series will examine specific types, from typos and duplicates to data corruption, in detail.

## The Slow Leak: When Systems Fail

Systemic errors don't come from someone making a mistake. They come from how processes and systems are built.

A database **schema** (the structure that defines what fields and tables exist) changes upstream and nobody tells the team downstream. Two departments define "active customer" differently, and both are technically correct in their own context. A data pipeline silently drops records when a load times out. A field that accepts free text in one system feeds a dropdown in another, and the values don't match.

These failures are baked into architecture, integration points, and organizational assumptions.

Monte Carlo, a data observability vendor, analyzed telemetry from over 11 million tables monitored on their platform and found that **pipeline execution faults** are the single most common root cause of data quality incidents, accounting for 26.2% of all issues (Monte Carlo, 2025). That data reflects organizations that have already invested in monitoring, so the real-world rate may differ. A peer-reviewed study confirmed the pattern: incorrect data types alone cause 33% of data-related pipeline issues (Zamanirad et al., 2023).

On August 1, 2012, Knight Capital Group deployed new trading software to its production servers. The deployment accidentally activated a piece of old, dormant code that had been left in the system. In forty-five minutes, that code executed a flood of erroneous trades.

Knight lost approximately $440 million before the market closed. The company needed an emergency capital infusion to survive the week and was acquired months later (SEC, 2013).

Nobody at Knight entered bad data. Nobody committed fraud. An outdated piece of code, left in place by a process that didn't account for it, brought down a major financial firm in less than an hour.

The system did exactly what it was designed to do. The design just didn't account for what was still lurking inside it.

The earlier posts in this series are full of systemic failures too: a unit mismatch between two NASA engineering teams and an Excel row limit that nobody expected to hit (both covered in [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care)).

Sometimes the categories overlap. The Rabobank story from [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) was both a systemic failure and a deliberate one: the bank's data infrastructure left suspicious activity invisible (a systemic gap), and people within the organization actively suppressed the data that did surface (a deliberate choice). When multiple origin types combine, the problem compounds: the systemic gap gave the deliberate actors room to operate, and the deliberate suppression ensured the systemic gap was never fixed.

## The Forgery: When Bad Data Is a Choice

This is the category most data quality content ignores entirely. Sometimes data is bad because someone made it that way on purpose.

In the late 1990s, German physicist Jan Hendrik Schon was publishing groundbreaking results in semiconductor physics at Bell Labs, at one point producing a new paper roughly every eight days. In April 2002, physicist Lydia Sohn at Princeton noticed something peculiar: two of Schon's published experiments, conducted at very different temperatures, contained graphs with identical random noise patterns (APS, 2022).

Random noise in experimental measurements is like a fingerprint. Every experiment generates its own. Seeing the same noise in two independent experiments is a statistical impossibility.

When *Nature* editors asked Schon about the match, he claimed he had accidentally submitted the same graph twice. Then Paul McEuen at Cornell found the same noise pattern in a third paper (Science, 2002).

Bell Labs formed an investigation committee. They confirmed fraud in at least 16 cases. Over 25 papers were retracted from journals including *Science*, *Nature*, and *Physical Review*. Schon had kept no laboratory notebooks and had deleted all raw data files, claiming limited hard drive space (Beasley et al., 2002).

Schon wasn't the only one. Dutch social psychologist Diederik Stapel fabricated data across his career at Tilburg University, eventually amassing at least 55 fraudulent publications and tainting at least 10 doctoral theses. He designed studies with collaborators, insisted on collecting the data himself, then handed students pre-fabricated datasets to analyze. His fraud lasted more than fifteen years (Levelt et al., 2012).

Three junior researchers finally raised the alarm. Their suspicion? Stapel's data looked too clean. Real experimental data is messy, but his consistently produced results that matched predictions almost perfectly (APA, 2011).

The Levelt committee concluded that Stapel's academic reputation was part of why the misconduct continued so long (Enserink, 2012).

Deliberate manipulation doesn't just happen in academic labs. In 2015, Volkswagen admitted that 11 million diesel vehicles worldwide contained software specifically designed to detect when a car was being emissions-tested. During the test, the software activated full pollution controls. On the road, it turned them off.

The cars produced clean data in the lab and wildly different emissions in the real world (EPA, 2016).

Engineers had built a system whose entire purpose was to generate false data under controlled conditions. VW pleaded guilty, and the total cost exceeded $33 billion in fines, settlements, and vehicle buybacks.

Unlike Schon or Stapel, the VW fraud wasn't one person falsifying results. It was an institutional decision, embedded in production software and deployed across a global fleet.

The pattern shows up anywhere someone has an incentive to make the numbers look different from reality, from inflated performance metrics to falsified compliance records.

These cases are rarer than accidents or systemic failures. But they happen, and pretending they don't leaves a blind spot in your data quality practice.

## The Same Tools Catch All Three

Here's what connects these stories: the same detection methods that catch accidental errors and systemic failures also catch deliberate manipulation.

Sohn spotted Schon's fraud through pattern analysis, the same technique data engineers use when monitoring pipeline outputs for anomalies. The junior researchers who caught Stapel noticed that his data was too perfect, a variation on the statistical tests that flag outliers. Knight Capital's erroneous trades were visible within minutes to anyone watching the market data feeds.

Range checks, duplicate analysis, statistical profiling, and metadata review work whether the bad data came from a fumbled keystroke, a misconfigured pipeline, or a calculated lie. The tools you build to catch one category give you a foundation against all three.

Sophisticated deliberate manipulation is specifically designed to evade detection. VW's defeat device software passed standard emissions testing because it was engineered to do exactly that. The more intentional the fraud, the more likely it is to target your existing checks.

The lesson isn't that basic data quality tools are sufficient for every case. Organizations without those tools have no chance of catching any of the three categories, and the same analytical instincts that flag accidental anomalies are what eventually unravel deliberate ones too.

## A Diagnostic Starting Point

When a data quality issue surfaces, the first question worth asking is: what kind of problem is this?

- **Could it be human error?** Random mistakes follow predictable patterns. They're distributed, individually small, and fixable with validation rules and input controls.
- **Could it be systemic?** If the same type of error keeps appearing, look at the architecture. Schema changes, integration mismatches, and silent pipeline failures produce errors that repeat until someone fixes the underlying design.
- **Could it be deliberate?** Unusually perfect data, missing audit trails, and resistance to sharing raw sources are warning signs. The same anomaly detection that catches accidents catches fraud.

The answer changes your response. Human errors need better validation. Systemic errors need architecture fixes. Deliberate manipulation needs investigation.

This post is the starting point for the "When Data Goes Wrong" series. The posts that follow will go deeper into each of these categories: the mechanics of "garbage in, garbage out," how pipelines introduce their own errors, the ways bias enters data, and the gap between where an issue is introduced and where it's finally discovered.

The causes of bad data are practically infinite. But the categories aren't. A welder in King Salmon taught me that thirty years ago, and every database I've worked with since has confirmed it.

## Key Takeaways

- **Bad data has three distinct origin types: human error, systemic failure, and deliberate manipulation.** Most data quality content treats all bad data as accidental. It isn't. The cause determines the response: validation for mistakes, architecture changes for systemic failures, and investigation for deliberate manipulation.
- **Human errors are constant and unavoidable.** Manual data entry error rates range from 0.55% to 26.9% depending on context (IBM, 2025). The goal isn't zero errors; it's fast detection.
- **Systemic failures are the most common and hardest to spot.** Pipeline execution faults account for 26.2% of data quality incidents across 11 million monitored tables (Monte Carlo, 2025). Knight Capital lost $440 million in forty-five minutes because dormant code was accidentally activated during a routine deployment (SEC, 2013). These errors repeat until the underlying design is fixed.
- **Deliberately fabricated data gets caught by the same methods that catch everything else.** Pattern analysis caught Schon's reused noise. Statistical improbability caught Stapel's too-clean results. Anomaly detection works regardless of intent.
- **The origin of a data quality issue changes how you respond to it.** Asking "what kind of problem is this?" before "how do I fix this?" saves time and prevents treating symptoms while the root cause persists.

## Sources

1. IBM. "Data Quality Issues and Challenges." *IBM Think*, 2025. https://www.ibm.com/think/insights/data-quality-issues
2. Monte Carlo Data. "Data Quality Statistics & Insights From Monitoring +11 Million Tables In 2025." *Monte Carlo Blog*, 2025. https://www.montecarlodata.com/blog-data-quality-statistics/
3. Zamanirad, S. et al. "Data Pipeline Quality: Influencing Factors, Root Causes of Data-related Issues, and Processing Problem Areas for Developers." *Journal of Systems & Software*, 2023. https://www.sciencedirect.com/science/article/pii/S0164121223002509
4. U.S. Securities and Exchange Commission. "SEC Charges Knight Capital With Violations of Market Access Rule." *SEC Press Release*, 16 October 2013. https://www.sec.gov/news/press-release/2013-222
5. American Physical Society. "September 2002: Schon Scandal Report is Released." *APS News*, August 2022. https://www.aps.org/apsnews/2022/08/september-2002-schon-scandal-report
6. Service, Robert F. "Physicist Fired for Falsified Data." *Science/AAAS*, 2002. https://www.science.org/content/article/physicist-fired-falsified-data
7. Beasley, M.R. et al. "Report of the Investigation Committee on the Possibility of Scientific Misconduct in the Work of Hendrik Schon and Coauthors." *Bell Labs/Lucent Technologies*, September 2002. https://media-bell-labs-com.s3.amazonaws.com/pages/20170403_1709/misconduct-revew-report-lucent.pdf
8. Levelt, W.J.M., Drenth, P.J.D., Noort, E. "Flawed Science: The Fraudulent Research Practices of Social Psychologist Diederik Stapel." *Tilburg University*, 2012. https://www.tilburguniversity.edu/sites/default/files/download/Final%20report%20Flawed%20Science_2.pdf
9. Enserink, Martin. "Final Report: Stapel Affair Points to Bigger Problems in Social Psychology." *Science/AAAS*, 2012. https://www.science.org/content/article/final-report-stapel-affair-points-bigger-problems-social-psychology
10. American Psychological Association. "The case of Diederik Stapel." *APA Psychological Science Agenda*, December 2011. https://www.apa.org/science/about/psa/2011/12/diederik-stapel
11. U.S. Environmental Protection Agency. "Learn About Volkswagen Violations." *EPA*, 2016. https://www.epa.gov/vw/learn-about-volkswagen-violations

## What's Next

This post introduced three categories of data quality problems. The next post in the "When Data Goes Wrong" pillar digs into one of the oldest principles in computing: [Garbage In, Garbage Out](/blog/garbage-in-garbage-out), and why the relationship between input quality and output quality is more complicated than the slogan suggests.

If you're new to the series, start with [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care) for the foundational concepts, then read [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) for what happens when these issues hit the bottom line.
