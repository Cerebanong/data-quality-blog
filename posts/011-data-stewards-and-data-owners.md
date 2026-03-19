---
title: Champions, Owners, and Stewards -- The Three Roles That Make or Break Data
  Governance
slug: data-stewards-and-data-owners
pillar: governance-in-practice
author: Kevin L Frank
date_published: '2026-03-19'
tags:
- foundations
- data-governance
- data-stewardship
- roles-and-responsibilities
- executive-sponsorship
- sarbanes-oxley
excerpt: 'Most governance content stops at two roles: owner and steward. But the role
  that actually determines whether governance succeeds or fails is the one nobody
  talks about -- the champion. Here''s how all three work together, why the champion
  matters most, and what goes wrong without one.'
seo_title: 'Data Champions, Owners, and Stewards: The Three Governance Roles Explained'
seo_description: 'Learn the three roles that make or break data governance: champions
  who drive authority, owners who set direction, and stewards who carry it out. Includes
  five anti-patterns and real examples from financial services.'
featured_image: images/011-data-stewards-and-data-owners-featured.png
---

A data quality issue surfaces in a meeting. Someone asks the obvious question: "Who owns this data?"

The room goes quiet. Or worse, three people point at each other.

The VP of Sales thinks IT owns it. The data engineer thinks the business owns it. The analyst who discovered the problem just wants someone to fix it.

I have worked in environments where governance roles were clearly defined, and in environments where there was little or no definition at all. The difference is night and day. But here is what I have learned after decades in financial services: the difference between success and failure is not whether you define data owners and stewards. It is whether someone at the top of the organization cares enough to drive the program.

Most governance content focuses on two roles: the data owner and the data steward. Gartner's governance framework identifies three. The third, the governance champion or sponsor, is the one most articles skip. It is also the one that determines whether the other two roles actually work.

In [What Is Data Governance?](/blog/what-is-data-governance), we covered what governance is and why it matters. This post answers the next question: who does it?

## The Restaurant Owner, the Chef, and the Line Cook

Think about a restaurant. Three roles make the kitchen work.

The **restaurant owner** sets the vision, funds the operation, and is accountable if the health department shuts the place down. Their name is on the liquor license and the health permit. They do not cook, but nothing exists without their commitment and capital. If the owner pulls funding, the restaurant closes.

The **head chef** designs the menu, sets quality standards, and decides what "good" looks like for every dish that leaves the kitchen. They are accountable for what comes out of the kitchen. If the chef leaves, menu quality drops and standards disappear.

The **line cook** executes those standards every day. They prep ingredients, maintain consistency plate after plate, catch problems in real time, and flag issues before they reach the customer. When a waiter comes back to the kitchen with a problem on a customer's order, the line cook is the first person they notify. If the line cook is absent, plates go out wrong.

Data governance works the same way.

The **governance champion** (sometimes called the executive sponsor) is the restaurant owner. They are a senior executive who commits organizational resources to the data program, removes obstacles, and ensures governance has sustained support from the top. Without a champion, governance programs close.

The **data owner** is the head chef. They are accountable for a **data domain** (a defined area of data, like customer data, financial data, or product data): they set direction, approve policies, and decide what "good enough" looks like.

The **data steward** is the line cook. They are responsible for that data day to day: they implement rules, monitor quality, and catch problems before they reach downstream consumers.

In RACI terms (Responsible, Accountable, Consulted, Informed), the data owner is the "A" and the data steward is the "R." The champion is the executive who ensures both roles have the authority and resources to succeed. As we established in [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care), data quality is a business concern, not a technical one. The same is true for all three governance roles.

As Robert Seiner argued in his Non-Invasive Data Governance framework (which we covered in [What Is Data Governance?](/blog/what-is-data-governance)), stewardship is not about creating new bureaucracy. It is about recognizing the people who are already caring for data and giving them formal standing to do it well. The champion makes that recognition official and ensures it sticks.

## What Each Role Actually Does

The analogy helps, but the details matter. Here is what each role looks like in practice.

### The Governance Champion

Gartner identifies the governance champion/sponsor as the first of three required governance positions, describing them as the executive who "ensures continued commitment and support from leadership" (Gartner, March 2024, G00788622). This is not a ceremonial role. The champion:

- Secures and sustains executive-level funding for the data program
- Removes organizational obstacles that owners and stewards cannot resolve on their own
- Represents data governance priorities in executive and board-level discussions
- Ensures governance decisions have enforcement authority, not just recommendations
- Sets the tone from the top that data quality is a business priority, not an IT project

Every financial organization I have seen succeed at data governance has had a passionate executive sponsor driving the program from the top.

### The Data Owner

A data owner is a senior business leader (not someone in IT) who has decision authority over a specific data domain. Gartner defines this role as "a senior business function leader who holds ultimate decision authority for the various data and analytics governance policies" (Gartner, March 2024, G00788622).

In practice, the owner:

- Sets quality standards and priorities for their domain ("accuracy of customer mailing addresses matters more than phone number formatting for our shipping operations")
- Approves policies governing who can access the data and what rules apply
- Decides what "good enough" looks like for data quality, which connects directly to the fitness-for-purpose argument in [What Makes Data Good?](/blog/what-makes-data-good)
- Allocates resources when quality issues need remediation
- Participates in governance boards and communicates priorities upward to the champion and downward to stewards

DAMA-DMBOK reinforces that data ownership is a business responsibility, not a technical one (DAMA International, 2017). The owner may never write a query or open a database. Their job is to make decisions about the data and be accountable for those decisions.

### The Data Steward

A data steward is a subject matter expert (SME) in the business who ensures governance policies are actually carried out. Gartner describes this as someone "responsible for ensuring data and analytics governance policies are implemented and monitoring information assets and people against those policies" (Gartner, March 2024, G00788622).

In practice, the steward:

- Curates data sources and maintains inventory
- Captures and enforces data quality rules
- Develops and approves business data glossary definitions
- Corrects data quality problems that automated processes cannot fix
- Monitors who is accessing and using the data
- Reports quality metrics to the data owner and governance board

The best steward candidates are not always managers. Gartner's research found that suitable candidates "are typically already performing most of the activities needed to be effective as a data steward" (Gartner, March 2024, G00788622). Exact Sciences, a healthcare company, took a "walk a mile in their shoes" approach: they shadowed business SMEs in their daily work and discovered that many were already doing stewardship activities without the title.

Rather than creating the role from scratch, they formalized what was already happening. That is Seiner's principle in action: find stewards, don't create them.

### A Note on Technical Stewards and Custodians

Two other roles are worth a brief mention. A **technical data steward** is an IT or data engineering role responsible for implementing quality rules in systems and pipelines. A **data custodian** manages the physical infrastructure: storage, backup, access provisioning.

The key distinction: a DBA who manages database access is a custodian, not an owner. Ownership is about business accountability for the data's meaning and quality, not technical custody of the systems that store it.

## When Roles Go Wrong: Five Anti-Patterns

The most common governance failures are not technology problems. They are people problems. Here are five patterns that reliably undermine data governance.

**1. "Everyone owns the data."** This sounds inclusive. In practice, it means nobody has specific accountability. When a quality issue surfaces, there is no escalation path and no one with authority to prioritize a fix. The problem lingers because no one can make the call.

I have seen two very different approaches to this with branch data at two different banks.

At Washington Mutual, a single department (Delivery Systems Planning and Development) was responsible for all financial center data. They generated it, maintained it, and distributed it to other parts of the bank. Anyone who needed branch data knew exactly where to get it, and that the quality was good.

The department head was the data owner. There was a subject matter expert everyone in the bank knew to reach out to for issues, questions, or edits. They even maintained their own database with a technical data steward (a role I filled in 1998 and early 1999).

At another bank, there were three different sources of branch data. No one department was responsible. The core banking system had its version, other versions existed to support vendors like security and facility management, and yet another version existed for retail operations.

Functions that needed the data, like compliance or business continuity, had to wade through the choices to find out what was true and relevant for their work. Downstream activities like my data warehouse and regulatory reporting had to resolve the differences between systems. The lack of a single owner increased both the number of people supporting the data and the risks associated with differences across sources.

**2. Swapping the titles.** Using "owner" and "steward" interchangeably causes real damage. People in steward roles start making decisions they lack authority for, and people in owner roles get pulled into operational work they should delegate. Gartner found this confusion significant enough to publish a dedicated research note on it in December 2025, specifically addressing how organizations conflate the two roles and slow their governance initiatives as a result (Gartner, December 2025, G00828929).

**3. Assigning ownership to IT.** When IT "owns" the data, business accountability evaporates. IT manages systems and infrastructure, not the business meaning of customer records or financial data. Gartner's governance framework places all three business stakeholder roles (champion, owner, steward) within business teams for exactly this reason (Gartner, March 2024, G00788622).

**4. Creating steward roles as extra workload.** Handing someone a new title and a list of new responsibilities on top of their existing job is a recipe for resentment and burnout. Gartner's research warns directly against this approach. The alternative, demonstrated by Exact Sciences, is to identify people already doing stewardship work and formalize their accountability with support, not extra burden (Gartner, March 2024, G00788622).

**5. All governance, no champion.** Stewards who identify issues but have no owner to escalate to. Owners who set policies but have no executive to secure funding or remove obstacles. Policies exist on paper, but nobody at the top is driving the program.

This is governance theater: the appearance of structure without the substance of authority. Of all five anti-patterns, it is the most common and the most damaging.

## Why the Champion Matters Most

The Enron and WorldCom scandals collapsed two of America's largest companies. Enron CFO Andrew Fastow was sentenced to 6 years for fraud and conspiracy. WorldCom CFO Scott Sullivan received 5 years for securities fraud. These cases sent a clear message about the consequences of corporate fraud.

In direct response, Congress passed the Sarbanes-Oxley Act in 2002. Section 302 requires CFOs to personally certify the accuracy of financial reports, with civil penalties for non-compliance. The law goes further in Section 906: willful violations carry criminal penalties of up to $5 million in fines and up to 20 years in prison.

The message to every CFO in America was clear: the data behind your financial reports is now your personal problem.

The effect in financial services was immediate. CFOs suddenly needed to trust the data behind the reports they were signing. In my experience, many became active champions and sponsors of data governance, not because they developed a passion for metadata management, but because their personal exposure depended on data accuracy.

You won't find a Gartner report titled "SOX Made CFOs Care About Data." But anyone who worked in financial services after Enron knows exactly what happened. I have seen it firsthand at four financial institutions:

At **Washington Mutual**, the CFO championed centralized data warehousing and governance. At **Rabobank, N.A.** (a national association bank that no longer exists, distinct from its sibling Rabobank North America), the CFO drove the data program with the same conviction. At **Rabobank North America** (a separate organization from Rabobank, N.A.), the CFO again served as the governance champion. At a **fourth institution**, the Chief Experience Officer took on that role.

The pattern was the same in every case. Having a senior executive who was passionate about good quality data meant data warehousing projects were funded, data governance programs were in place, and professional staff was hired. If there was an issue, there was a top-level executive who could be brought in to resolve it. In every case, these champions were passionate about hiring good leaders and listening to the advice their chosen data leadership provided.

The lesson extends beyond financial services: the most effective governance programs are those where someone with genuine skin in the game is driving the program. When accountability carries real consequences, governance stops being optional.

## How It Scales: From Startup to Enterprise

These roles look different depending on the size of your organization.

In a **small organization**, one person may serve all three functions. The titles may not exist. But the functions still do: someone commits resources (the champion function), someone decides what quality standards apply (the owner function), and someone monitors and maintains them (the steward function). Even a five-person team benefits from knowing who fills each role.

In a **mid-size organization**, dedicated stewards begin to emerge, often formalized from existing SME roles. This is where Seiner's "find, don't create" approach works best. Owners are typically business unit leaders or department heads. The champion is often a VP or director with budget authority.

A **large enterprise** adds multiple layers: enterprise stewards, domain stewards, technical stewards. Gartner recommends a "lead business data steward" as a central coordination point across peer stewards (Gartner, March 2024, G00788622). Formal governance boards handle ownership assignments, often supported by a Chief Data Officer or Data Governance Council. The champion may be the CDO, the CFO, or another C-suite executive with enterprise authority.

There is no single right governance model. The 2025 State of Enterprise Data Governance Report found that senior data leaders at Fortune 1000 companies are roughly evenly split: 36% use a centralized model, 36% use a federated model, and 29% use a hybrid approach (percentages rounded; Board.org, 2025). The right structure depends on your organization's culture, data maturity, and business needs.

What the data does show is that governance challenges are growing, not shrinking. A 2024 survey of 565+ data and analytics professionals by Precisely (a data governance vendor) and Drexel University found that 51% of organizations now identify data governance as one of their biggest challenges (an 89% increase from just 27% in 2023), even as 71% report having a governance program in place, up from 60% the year before (Precisely/Drexel, 2024). More organizations are doing governance, but more are also struggling with it. Getting all three roles right is one of the most direct ways to close that gap.

## Starting Monday Morning

You do not need a multi-year governance program to start getting these roles right. Here is where to begin based on where you are today.

**If you have no roles defined:** List your most important data domains (customer, product, financial). For each, identify who currently makes decisions about that data (your de facto owner), who currently maintains it (your de facto steward), and which executive would care most if that data caused a problem (your de facto champion). Make it official.

**If you have owners and stewards but no champion:** This is the most common gap. Identify the senior executive whose outcomes depend most on data accuracy. Make the case for their active involvement. Without executive sponsorship, your owners and stewards are operating without air cover.

**If you have the titles but they are confused:** Run the restaurant test. For each person with a governance title, ask: do they fund the operation and keep the doors open (champion), design the menu and set the standards (owner), or execute those standards plate after plate (steward)? Realign based on the answer.

**If you have stewards but no owners:** Your stewards lack authority. Identify the business leader accountable for each data domain and formalize the owner role. Without this, stewards will burn out escalating issues that never get resolved.

In recent years, I have found Seiner's recommendation of identifying existing talent to be the right direction. Rather than designing roles on paper and looking for people to fill them, look for the people already doing the work and build the structure around them. And above all, find your champion. Everything else follows from there.

## Key Takeaways

- **Three roles, not two.** Most governance content focuses on owners and stewards. Gartner's framework adds the champion/sponsor as the first required role. In my experience, the champion is the single biggest predictor of whether a governance program succeeds.
- **Data owners are accountable; data stewards are responsible.** The owner sets direction and policy for a data domain. The steward implements and enforces it day to day. Both roles are essential; neither works without the other.
- **The champion drives authority from the top.** Without a passionate executive sponsor, governance programs starve for resources, lack enforcement authority, and devolve into governance theater.
- **Ownership belongs to the business, not IT.** IT manages systems and infrastructure (the custodian role). Business leaders own the data and the decisions about it.
- **Find stewards; don't create them.** The best steward candidates are people already doing the work informally. Formalize existing accountability rather than piling on new responsibilities.
- **Start with your champion.** Identify the executive whose outcomes depend on data accuracy. Everything else follows from their commitment.

## Sources

1. DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge, 2nd Edition.* Technics Publications, 2017.
2. Seiner, Robert. *Non-Invasive Data Governance: The Path of Least Resistance and Greatest Success.* Technics Publications, 2014.
3. Bickel, Amy. "How to Drive Business Stakeholder Engagement in Data Governance." *Gartner*, March 2024. ID G00788622.
4. Di Maso, Valeria and Rajat Pandey. "D&A Governance: Defining Data Owners' vs. Stewards' Role in Finance." *Gartner*, December 2025. ID G00828929.
5. Enterprise Data Strategy Board. "2025 State of Enterprise Data Governance Report." *Board.org*, 2025.
6. Precisely and Drexel University LeBow College of Business. "2025 Outlook: Data Integrity Trends and Insights." September 2024.
7. Sarbanes-Oxley Act of 2002, Pub. L. 107-204, Sections 302 and 906.
8. U.S. Department of Justice. Sentencing records for Enron and WorldCom executives.

## What's Next

Now that you understand the three roles that make governance work, the next post in this series will explore the full cast of characters involved in data quality: [Roles and Ownership in Data Quality](/blog/roles-and-ownership-in-data-quality). 

If you haven't read our introduction to data governance, start with [What Is Data Governance?](/blog/what-is-data-governance), which covers what governance is, how it evolved, and why your organization is probably already doing it.

For a look at why clear ownership matters when things go wrong, see [Where Data Quality Issues Come From](/blog/where-data-quality-issues-come-from).
