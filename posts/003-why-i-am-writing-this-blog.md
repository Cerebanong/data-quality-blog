---
title: Why I Am Writing This Blog
slug: why-i-am-writing-this-blog
pillar: strategy-leadership
author: Kevin L Frank
date_published: '2026-03-06'
tags:
- foundations
- about-the-author
- career-retrospective
- data-quality-culture
excerpt: From tracking sled dogs on an Apple II+ in 1982 Alaska to investigating outlier
  soil samples on oil-stained beaches in Prince William Sound, data quality has been
  the thread through more than four decades of my career. Here's why I started writing
  about it.
seo_title: Why I Started a Data Quality Blog After 40+ Years
seo_description: Four decades of data work — from tracking sled dogs in Alaska to
  investigating oil spills — led to this blog. Here's the career story behind MacroQuality.
featured_image: images/003-why-i-am-writing-this-blog-featured.png
---

## A Kid, a Computer, and a Thousand Miles of Trail

During the Fall of 1982, I was fourteen years old and living in Nome, Alaska. Nome sits on the southern shore of the Seward Peninsula, about as far west as you can get on the North American mainland. It is also the finish line for the Iditarod Trail Sled Dog Race, roughly a thousand miles of frozen wilderness between Anchorage and our town.

That school year, the Nome Beltz High School computer classes had a project: build an application in the school's Apple II+ computer lab to track the Iditarod mushers. Alaska's oil revenues were pouring money into public schools, and our school had new computers that most schools in the Lower 48 wouldn't see for years. We wrote a program that recorded checkpoint entry and exit times, the number of dogs each musher had at each stop, and where they took their mandatory 24-hour rest.

I didn't know it then, but I was doing data quality work. We were building a system to capture, organize, and make sense of information so that people could trust what they were looking at. That's a pretty good definition of the jobs I've been doing for more than four decades since.

Rick Mackey won that year, finishing in just over twelve and a half days and becoming the first son of an Iditarod champion to win the race (Iditarod). Swenson, who had won three of the previous four years, finished fifth.

In 1982, my family also used our Alaska Permanent Fund Dividend to purchase a computer: a Franklin Ace 1000 (a clone of the Apple II+). That machine sparked a lifelong interest in technology that eventually became a passion for data, data quality, and data governance.

## Sampling the Air and Soil

A few years later, I was a biochemistry major at the University of Alaska Fairbanks. I worked in Dr. Dan Jaffe's lab on **arctic atmospheric chemistry**, tracking the distribution of anions (negatively charged molecules like sulfate and nitrate) that industrial pollution from Eurasia carried across the polar region. The research involved collecting samples and running **ion chromatography** (a lab technique that separates and measures dissolved ions) to characterize what was showing up in the Arctic air. It was meticulous, repetitive, and entirely dependent on consistent sample handling.

As an undergrad research assistant, my job was mostly data entry and monitoring the instruments as they ran samples. The least experienced person in the lab, I usually drew the night shift, watching the samples run through their process and entering the data into the campus VAX.

Then, on March 24, 1989, the oil tanker *Exxon Valdez* struck Bligh Reef in Prince William Sound and spilled more than 11 million gallons of Prudhoe Bay crude oil across roughly 1,300 miles of coastline. The cleanup effort that followed involved approximately 10,000 workers, 1,000 boats, and around 100 aircraft (NOAA). It was the largest environmental disaster in American history at the time.

I joined the bioremediation research project led by Dr. Ed Brown at UAF. **Bioremediation** is a technique that uses naturally occurring microorganisms to break down pollutants. In this case, the approach was to add fertilizers to oil-contaminated beaches, giving the indigenous oil-degrading bacteria the nitrogen and phosphorus they needed to multiply and consume the oil as a food source. It was a joint collaboration between Exxon, the EPA, NOAA, the Alaska Department of Environmental Conservation, and UAF (EPA).

## The Batch That Didn't Match

During the summer of 1990, our team was collecting tens of thousands of soil samples from beaches on Knight Island, Green Island, Disk Island, and other sites throughout Prince William Sound. The process was painstaking. We collected sediment from the shoreline, brought it back to the lab, and ran **serial dilutions** (a procedure where you progressively dilute a sample to isolate and count individual microorganisms). After incubation, we could quantify the number of oil-degrading bacteria per gram of soil.

The goal was to measure whether fertilized beaches were producing more microbial activity than untreated control sites. They were: the landmark *Nature* paper that came out of this work later confirmed biodegradation rates three to five times faster on treated beaches (Bragg et al., 1994).

But during one particularly large sampling session, we needed help processing the large number of samples. We were on the clock to get the samples incubating within our required timeline. A group of scientists from another part of the project, people who hadn't been through the serial dilution training, stepped in to help us process all the samples. They received on-the-job instruction during what was already a busy processing day.

Months later, when we analyzed the data, that batch was a clear outlier. The numbers showed a statistically significant spike in oil-degrading bacteria compared to the surrounding data points. The question was obvious: Did the untrained team introduce systematic error in the dilution procedure? Or had warmer weather that particular week genuinely produced a bloom of microbial activity?

We didn't have the mechanisms in place to determine which explanation was true. No separate process log tracked who performed each step. No parallel control had been run with the experienced team on the same samples. The data point sat there, ambiguous, carrying two completely different stories depending on which interpretation you chose.

I genuinely don't know for certain.

That uncertainty is exactly the point. When your process doesn't capture enough context about how data was collected, you lose the ability to interpret what the data means. The numbers themselves looked precise. The spreadsheet was neat.

But without reliable metadata about the collection process, a single outlier batch became unanswerable. In environmental science, unanswerable questions can mean the difference between a valid finding and a flawed conclusion.

## A Two-Digit Problem

After college, I spent seven years working at Northern Testing Laboratories, Inc. and Quest Environmental, doing everything from microbial analysis and drinking water testing to asbestos identification and metals analysis on an ICP (inductively coupled plasma spectrometer, an instrument that identifies metals by heating samples to temperatures hotter than the surface of the sun). I also took on IT responsibilities, managing the lab's computer systems.

In 1997, I discovered that the lab's **LIMS** (Laboratory Information Management System, the software that tracks every sample from intake through analysis and reporting) stored dates with two-digit year fields. Sample hold times and expiration date calculations would break when "00" arrived and the system interpreted it as 1900 instead of 2000. A sample with a three month expiration period arriving on November 1, 1999, would be assumed to have expired 99 years and 9 months ago the moment we checked it in.

The lab owners were resistant to investing in an upgrade. I left. I didn't want to be responsible for maintaining a system that couldn't do the job it was designed to do. A data quality problem drove a career decision.

That decision led me to Washington Mutual. I started in June 1998 doing Y2K preparation, and before the calendar turned, the bank sent technical staff like me to branches to reassure customers that their financial data was safe. Across the banking industry, confidence was shaky: in March 1999, only 76% of customers felt confident about Y2K, and almost two-thirds planned to withdraw cash before New Year's Eve. By November, after months of industry-wide outreach, confidence had climbed to 90% (Federal Reserve Bank of Minneapolis, 1999).

I stayed at WaMu for over a decade, through its seizure by federal regulators in September 2008, the largest bank failure in U.S. history, and a year into the JPMorgan Chase acquisition that followed.

## Four Decades of the Same Lesson

The rest of my career has followed the same thread. At Extended Results, I led a team of BI developers supporting nine projects for four clients. The Rabobank years spanned three U.S. entities, where I led the construction of three different enterprise data warehouse solutions at RNA (a story I told in detail in [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data)), at RaboAgrifinance, and at Rabo Diversified Services. During that time also came two years leading data system development and operations for a healthcare eligibility software developer, Social Interest Solutions.

Today, I work at a mid-sized regional bank, leading an enterprise data solutions team.

Every one of those roles involved some version of the same question: Can we trust this data enough to act on it?

Often the answer is yes. But, more often than you'd expect, the answer is "not yet." And the work of getting from "not yet" to "yes" is what managing data quality is about.

## Why This Blog Exists

I've spent more than four decades collecting these lessons, and most of them live in my head, in conversations with colleagues, in notes from projects that are long since finished. This blog is my attempt to get them out where they might be useful to someone else.

This is not a sponsored blog. I'm writing independently, sharing what I've learned from decades of work across environmental science, banking, consulting, healthcare technology, and enterprise data management. If something I've seen can save you time, help you make a better case to your leadership, or just make you feel less alone in the fight for better data, then the writing was worth it.

But I don't want this to be a one-way broadcast. The most valuable thing about working in data for this long is the conversations: the colleague who sees a problem from an angle you missed, the reader who has a better solution than the one you proposed. I hope the comments on these posts become that kind of conversation.

I have strong opinions and real experience, but I know I don't have every answer. If you've seen something I haven't, I want to hear about it.

The first two posts in this series laid the foundation: [what data quality is and why it matters](/blog/what-is-data-quality-and-why-should-you-care), and [what it costs when it goes wrong](/blog/the-true-cost-of-bad-data). From here, the topics get more specific and more practical. We'll look at where data quality issues actually come from, how to measure quality, how to build governance that works, and how to write the code that catches problems before they reach production.

I've been doing this work since before most data quality tools existed. Pull up a chair.

## Key Takeaways

- **Data quality work doesn't always announce itself.** A fourteen-year-old tracking sled dogs on an Apple II+ was doing data quality work. So is anyone who organizes information so that other people can trust it.
- **The cost of missing metadata can be permanent.** On the beaches of Prince William Sound, a single batch of samples became ambiguous because the sample processing didn't capture who performed each step or allow parallel validation. Two completely different interpretations were equally plausible, and the data alone couldn't resolve the question.
- **Data quality problems drive real career decisions.** When I discovered a lab system that couldn't handle the year 2000, I left. When a bank's data infrastructure had gaps that prevented suspicious activity from being surfaced, the consequences eventually reached hundreds of millions of dollars (a story told in detail in [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data)). These aren't abstract risks.
- **More than four decades of experience across industries tells a consistent story.** Environmental science, banking, consulting, healthcare technology: the specifics change, but the underlying pattern repeats. Organizations that can't trust their data can't act on it effectively.
- **This blog is a conversation, not a lecture.** I'm sharing what I've learned, but I expect to learn from readers too. Your experience and perspective make the conversation richer.

## Sources

1. Brown, E.J., Resnick, S.M., Rebstock, C., Luong, H.V., Lindstrom, J. "UAF radiorespirometric protocol for assessing hydrocarbon mineralization potential in environmental samples." *Biodegradation*, 2(4):121-127, 1991. https://pubmed.ncbi.nlm.nih.gov/1368153/
2. Lindstrom, J.E., Prince, R.C., Clark, J.C., Grossman, M.J., Yeager, T.R., Braddock, J.F., Brown, E.J. "Microbial populations and hydrocarbon biodegradation potentials in fertilized shoreline sediments affected by the T/V *Exxon Valdez* oil spill." *Applied and Environmental Microbiology*, 57(9):2514-2522, September 1991. https://pubmed.ncbi.nlm.nih.gov/1662935/
3. Bragg, J.R., Prince, R.C., Harner, E.J., Atlas, R.M. "Effectiveness of bioremediation for the Exxon Valdez oil spill." *Nature*, 368:413-418, 1994. https://www.nature.com/articles/368413a0
4. U.S. EPA. "Bioremediation of Exxon Valdez Oil Spill." *EPA Archive*. https://www.epa.gov/archive/epa/aboutepa/bioremediation-exxon-valdez-oil-spill.html
5. NOAA. "Exxon Valdez." *NOAA Damage Assessment, Remediation, and Restoration Program*. https://darrp.noaa.gov/oil-spills/exxon-valdez
6. Federal Reserve Bank of Minneapolis. "Y2K and public confidence in the banking system." *Federal Reserve Bank of Minneapolis*, 1999. https://www.minneapolisfed.org/article/1999/y2k-and-public-confidence-in-the-banking-system
7. Iditarod Trail Committee. "1983 Iditarod Race Results." *Iditarod*. https://iditarod.com/race/1983/

## What's Next

Now that you know who's writing this blog and why, the series moves into practical territory. The next post examines where data quality issues actually come from. Most people assume bad data is always an accident. Sometimes it is. Sometimes the system itself produces it. And sometimes, someone made it bad on purpose. The origin matters because it changes everything about how you respond.

If you're just joining the series, start with [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care) for the foundational concepts, then read [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) for the financial and operational stakes.
