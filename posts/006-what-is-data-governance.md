---
title: What Is Data Governance?
slug: what-is-data-governance
pillar: governance-in-practice
author: Kevin L Frank
date_published: '2026-03-15'
tags:
- foundations
- data-governance
- data-management
excerpt: 'Data governance became a business requirement after corporate scandals forced
  regulators to ask: who owns this data, and who''s accountable when it''s wrong?
  Here''s what governance actually is, why you''re already doing it, and why it''s
  bigger than you think.'
seo_title: What Is Data Governance? A Practical Definition
seo_description: Understand what data governance really means, how it evolved from
  corporate scandals, and why your organization is already doing it — whether you
  know it or not.
featured_image: images/006-what-is-data-governance-featured.png
---

## When the Seventh-Largest Company in America Vanished

In October 2001, Enron Corporation reported a $618 million loss for the third quarter and a $1.2 billion reduction in shareholder equity. The announcements revealed what insiders had known for years: the company had used accounting loopholes, **mark-to-market accounting** abuse (recording projected future profits as current income, even when the cash hadn't arrived), and **special purpose entities** (off-the-books partnerships designed to hide debt) to conceal billions in losses from failed deals and investments (Wikipedia, 2024).

Two months later, on December 2, 2001, Enron filed for Chapter 11 bankruptcy. At the time, it was the largest bankruptcy in U.S. history. The seventh-largest company in America was gone.

Then it happened again. In June 2002, WorldCom admitted it had falsely reported $3.85 billion in expenses, a figure that eventually grew to $11 billion in total accounting fraud. Tyco, Adelphia, Global Crossing, and Qwest followed with their own scandals. Public trust in corporate financial reporting collapsed (EBSCO Research, 2024).

Congress responded fast. On July 30, 2002, President George W. Bush signed the **Sarbanes-Oxley Act (SOX)** into law (Britannica, 2024). SOX made executives personally liable for the accuracy of financial statements and strengthened audit independence. Its Section 404 went further, requiring organizations to implement and maintain internal controls over financial reporting (IBM, 2024).

Here's why that matters for **data governance**: SOX's requirements for accurate, tamper-proof financial reporting created a regulatory necessity for organizations to know who owned their data, what standards it had to meet, and who was accountable when it didn't. You can't certify the accuracy of your financial statements if you can't answer those questions. The era of informal, ad hoc management of financial reporting data was over for public companies.

## What Data Governance Actually Is

Most definitions of data governance read like they were written by a committee. [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care) described governance as the set of practices, policies, and standards that coordinate data management. That's accurate as far as it goes, but it doesn't capture the full relationship. Here's a better way to think about it.

**Data governance is to data management as audit is to finance.** The finance team runs payroll, manages accounts payable, processes transactions. The audit function doesn't do any of that work. Instead, it provides oversight: are the right controls in place? Are the standards being followed? Is someone accountable when they're not? Governance goes further than audit in one important way: it also sets the standards and defines ownership, not just checks whether they're being followed.

That analogy didn't come from a textbook. It came from a specific moment in my career.

I was working at Rabobank in 2017 when I took on responsibility for leading data management across the combined North American entities. Rabobank globally was taking a forward-thinking approach to managing data, with a global data governance council and international entities standing up their own councils to follow the global model. My big projects at the time were for the Finance and Risk departments, and I spent a lot of time talking to finance and risk leaders, compliance, and audit. The head of Data Governance for North America reported into Finance.

Because of Sarbanes-Oxley and the legal liability that comes with financial reporting, our CFO wanted to own data governance and have confidence in the quality of data flowing into financial and regulatory reports. I spent months in conversations about the control frameworks we used to keep enterprise data under control. And that's when it clicked: the data governance function should be overseeing data management the way the audit function was overseeing the bank's financial management.

The parallels were obvious once I saw them. I just hadn't seen them before.

## The Governance-Management Distinction

That's the relationship between governance and management. **Data management** (the set of operational disciplines for collecting, storing, organizing, and maintaining data) does the day-to-day work. **Data governance** provides oversight and accountability over that work. Governance defines the what, who, and why. Management executes the how (DAMA International, 2017).

Gartner describes two postures that governance can take. **Defensive governance** focuses on compliance, security, and risk mitigation: keeping the organization out of trouble. **Offensive governance** focuses on enabling data-driven value creation, analytics, and AI: helping the organization do more with its data (Gartner, G00834531, 2025).

Most organizations need both. The ones that treat governance as purely defensive miss the value-creation side entirely.

The same Gartner model identifies 10 components of a governance program: policy, processes, training, data literacy, identity and access management, security and privacy, master data management, **data quality**, metadata, and data observability (Gartner, G00834531, 2025). Data quality is one of ten. That distinction matters, and we'll come back to it.

## The Regulatory Cascade

SOX was not the first regulation to force governance, and it certainly wasn't the last. A pattern emerges when you trace the timeline.

**HIPAA** (the Health Insurance Portability and Accountability Act, 1996) required formal governance structures for healthcare data, addressing privacy, security, and accuracy long before most industries were thinking about governance at all. **SOX** (2002) extended governance requirements to financial reporting across every public company.

Banking tells its own version of this story. **Basel II** (2004) introduced operational risk as a category banks had to quantify for the first time, and its Pillar 3 disclosure requirements (mandatory public reporting on risk exposures and capital adequacy) forced banks to produce reliable, auditable data (Basel Committee, 2004). **Basel III** (2010), the regulatory response to the 2008 financial crisis, tightened capital and liquidity requirements and significantly expanded the depth and quality of risk reporting expected from banks (Basel Committee, 2010). Banks discovered they couldn't meet the new reporting requirements without better data governance.

That realization led to **BCBS 239** (2013), which codified 14 principles for risk data aggregation and reporting, requiring global banks to strengthen their data governance, infrastructure, and reporting processes (Basel Committee, 2013). **GDPR** (the General Data Protection Regulation, 2018) made data governance a requirement for any organization handling personal data of EU residents, with penalties that got everyone's attention (EWSolutions, 2024).

Each wave brought more industries into the fold. Healthcare first. Then financial reporting for public companies. Then a decade of progressively tighter banking regulation. Then privacy for everyone. The pattern is consistent: governance shifted from a best practice to a regulatory requirement, one industry at a time.

The gap between awareness and action is still wide. In Gartner's 2024 CDAO Agenda Survey, 89% of Chief Data and Analytics Officers said governance is essential to their organization, but only 48% reported having consistent governance policies across their organization (Gartner, G6903766, 2025). Almost everyone agrees governance matters. Fewer than half have actually made it consistent.

## You're Already Doing It

Here's the part that surprises most people: your organization is already governing data. You just might not be calling it that.

Robert Seiner, an internationally recognized governance consultant, calls this **Non-Invasive Data Governance (NIDG)**. His argument is straightforward: people in every organization are already making decisions about data definitions, access, retention, and quality. They decide who can edit a spreadsheet, what values belong in a dropdown, how long to keep old records. All of that is governance, happening informally, every day (Seiner, 2008).

The problem isn't that governance doesn't exist. The problem is that it's invisible, inconsistent, and undocumented. Seiner's approach formalizes existing accountability rather than imposing new bureaucracy. It recognizes people for the relationship to data they already have and builds from there (Seiner, 2008).

Gartner validates this perspective. Their research on AI-ready data governance found that big-bang, centralized approaches to governance often fail, and recommends phased, incremental implementation instead (Gartner, G6732134, 2025). The prediction is stark: Gartner estimates that 80% of data and analytics governance initiatives will fail by 2027 if they aren't tied to priority business outcomes (Gartner, 2024). (At their [2026 Data & Analytics Summit](/blog/gartner-2026-data-analytics-summit-key-takeaways), Gartner analysts went further: governance will be "the single point of failure" for AI ambitions, and AI governance may need a fundamentally different operating model than traditional data governance.)

That number looks less surprising when you consider the alternative. Organizations that try to build governance from scratch, as a separate layer of rules on top of existing work, create exactly the bureaucratic overhead that makes people resist. The organizations that succeed tend to start with what's already working and build structure around it.

Governance is oversight, not overhead. The distinction matters.

## Data Governance Is Bigger Than Data Quality

If you've been following this series from [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care), you might assume data governance is primarily about data quality. It's a common assumption, and a limiting one.

Different frameworks describe this relationship from different angles. That first post introduced the DAMA-DMBOK2 framework, which positions governance at the center of a wheel, coordinating knowledge areas that include data architecture, metadata management, data security, master data management, and data quality. In DAMA's model, governance oversees these disciplines. Data quality is one spoke in that wheel, not the hub.

Gartner takes a different view. Their 10-component governance model describes what a governance program itself consists of: policy, processes, training, data literacy, identity and access management, security and privacy, master data management, data quality, metadata, and data observability (Gartner, G00834531, 2025). Here, data quality is something governance includes, not something it oversees from above.

The frameworks describe different things, but they arrive at the same practical conclusion: data quality is one important element of governance, not the whole picture. Organizations that equate governance with quality miss most of what governance actually covers.

Governance and data quality do have a strong relationship, though. Governance makes quality sustainable by providing the standards, ownership, and feedback loops that prevent quality from being a one-time fix. Quality makes governance effective by giving the organization confidence that its policies are built on data it can trust. It's a virtuous cycle, and neither works as well without the other.

Consider what the first five posts in this series have covered. [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) showed that poor data quality costs large enterprises an average of $12.9 million per year, based on a survey of data quality vendor customers (Gartner, 2020). Governance provides the accountability structure to prevent those costs.

[Where Data Quality Issues Come From](/blog/where-data-quality-issues-come-from) identified three root causes: human error, systemic failure, and deliberate manipulation. Governance provides the foundation for preventing all three: standards reduce human error, architecture oversight catches systemic failures, and accountability structures make deliberate manipulation harder to sustain. No governance framework is manipulation-proof (as the Enron story at the top of this post reminds us), but without governance, there's no structure to catch it at all.

[The 6 Dimensions of Data Quality](/blog/the-6-dimensions-of-data-quality) defined the measurement vocabulary that governance provides the framework to apply. Everything we've discussed so far fits under the governance umbrella. This post is where the umbrella opens.

## A Governance Readiness Checklist

The "Governance in Practice" pillar of this blog is about practical steps, not theory. This series focuses on data quality, so the checklist below starts there. A full governance assessment would cover all ten components from security to metadata to policy. But data quality is where most organizations feel governance gaps first, and it's where the clearest quick wins live.

If your organization is starting to think about governance (or wondering whether you already have it), these questions can help you assess where you stand.

**Accountability:**
- Can you name the person accountable for each of your organization's most important datasets?
- When data quality issues surface, is there a clear path for who investigates and resolves them?

**Standards:**
- Do written standards exist for how key data elements are defined, formatted, and validated?
- Are those standards documented somewhere people can actually find them?

**Consistency:**
- When the same data element appears in multiple systems, do those systems agree on its definition?
- Is there a process for resolving disagreements when they don't?

**Measurement:**
- Are you measuring data quality against specific targets, or just reacting when something breaks?
- Do you know which of the [six dimensions](/blog/the-6-dimensions-of-data-quality) cost you the most?

**Communication:**
- Do the people who create and modify data understand what standards apply?
- When standards change, is there a process for communicating that to affected teams?

You don't need to answer "yes" to every question before starting. Most organizations answer "yes" to some, "sort of" to others, and "no" to a few. The point isn't perfection; it's visibility. Knowing where you stand is the first step toward building governance that actually works.

Governance adoption is accelerating. According to a 2024 survey by Precisely (a data quality and governance vendor) and Drexel University, 71% of organizations now have a data governance program, up from 60% in 2023. Among those organizations, 58% report improved data quality and 57% report increased collaboration as direct benefits (Precisely/Drexel, 2024). That 71% figure is worth reading alongside Gartner's finding that only 48% have consistent governance policies.

The gap likely reflects different maturity thresholds: having a program and having a mature program are not the same thing. McKinsey's research goes further: leading firms with effective governance have eliminated millions of dollars in cost and enabled analytics use cases worth millions more (McKinsey, 2023).

In [Why I Am Writing This Blog](/blog/why-i-am-writing-this-blog), I mentioned that this series would eventually cover how to build governance that works. This post is where that conversation starts. The question isn't whether your organization will adopt formal governance. It's whether you'll build it intentionally or let it grow haphazardly.

## Key Takeaways

- **Governance is oversight, not overhead.** Data governance provides accountability and standards over data management, the same way audit provides oversight over finance. It defines the what, who, and why; management executes the how.
- **You are already governing data.** People in your organization make decisions about data definitions, access, and quality every day. Formalizing that existing accountability (Robert Seiner's Non-Invasive Data Governance approach) is more effective than imposing governance as a separate layer of bureaucracy.
- **Regulation turned governance from a best practice into a requirement.** The cascade from HIPAA (1996) to SOX (2002) through Basel II, III, and BCBS 239 (2004-2013) to GDPR (2018) brought governance requirements to progressively more industries. Each wave was triggered by a crisis that exposed what happens without oversight.
- **Governance is bigger than data quality.** Data quality is one of ten governance components in Gartner's model. Organizations that treat governance as "just data quality" miss nine-tenths of the picture, including security, privacy, metadata, master data, and policy.
- **The gap between belief and practice is wide.** 89% of CDAOs believe governance is essential, but only 48% have consistent policies (Gartner, 2024). Closing that gap starts with understanding what you already have and building from there.

## Sources

1. Wikipedia contributors. "Enron scandal." *Wikipedia*. https://en.wikipedia.org/wiki/Enron_scandal
2. EBSCO Research. "Sarbanes-Oxley Act of 2002." *EBSCO Research Starters*. https://www.ebsco.com/research-starters/business-and-management/sarbanes-oxley-act-2002
3. Encyclopaedia Britannica. "Sarbanes-Oxley Act of 2002." *Britannica*. https://www.britannica.com/topic/Sarbanes-Oxley-Act
4. IBM. "What is SOX (Sarbanes-Oxley Act) Compliance?" *IBM Think*. https://www.ibm.com/think/topics/sox-compliance
5. EWSolutions. "The Evolution of Data Governance: Key Milestones." *EWSolutions*. https://www.ewsolutions.com/the-evolution-of-data-governance/
6. Basel Committee on Banking Supervision. "Basel II: International Convergence of Capital Measurement and Capital Standards." *Bank for International Settlements*, June 2004. https://www.bis.org/bcbs/publ/d128.htm
7. Basel Committee on Banking Supervision. "Basel III: International Regulatory Framework for Banks." *Bank for International Settlements*, December 2010. https://www.bis.org/bcbs/basel3.htm
8. Basel Committee on Banking Supervision. "Principles for effective risk data aggregation and risk reporting." *Bank for International Settlements*, January 2013. https://www.bis.org/publ/bcbs239.pdf
9. Seiner, Robert S. "What is Non-Invasive Data Governance?" *TDAN.com*, 2008 (republished 2016). https://tdan.com/what-is-non-invasive-data-governance/7354
10. DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge.* 2nd Edition, 2017. https://www.dama.org/cpages/body-of-knowledge
11. Gartner. "Gartner Predicts 80% of D&A Governance Initiatives Will Fail by 2027." *Gartner Newsroom*, 28 February 2024. https://www.gartner.com/en/newsroom/press-releases/2024-02-28-gartner-predicts-80-percent-of-data-and-analytics-governance-initiatives-will-fail-by-2027-due-to-a-lack-of-a-real-or-manufactured-crisis-
12. Precisely / Drexel University. "2025 Outlook: Data Integrity Trends and Insights." *Precisely*, 2024. https://www.precisely.com/data-integrity/2025-planning-insights-data-governance-adoption-has-risen-dramatically/
13. McKinsey & Company. "Designing data governance that delivers value." *McKinsey Digital*, 2023. https://www.mckinsey.com/capabilities/tech-and-ai/our-insights/designing-data-governance-that-delivers-value
14. Maguire, Joe. "Reference Architecture Brief: Data and Analytics Governance." *Gartner Research*, Document ID G00834531, July 2025.
15. White, Parker, Turkaly. "How to Design an Effective D&A Governance Operating Model." *Gartner Research*, Document ID G6903766, September 2025.
16. Christensen, Lydia. "A Practical Guide to Data Governance for AI-Ready Data." *Gartner Research*, Document ID G6732134, July 2025.
17. Gartner. "Data Quality." *Gartner*, 2020. https://www.gartner.com/en/data-analytics/topics/data-quality

## What's Next

This post introduced what data governance is and why it became a business requirement. The posts that follow in the "Governance in Practice" pillar will get more specific: how to structure a governance program, how to define roles and responsibilities, and how to measure whether governance is actually working.

If you're new to the series, start with [What Is Data Quality and Why Should You Care?](/blog/what-is-data-quality-and-why-should-you-care) for the foundational concepts, then read [The True Cost of Bad Data](/blog/the-true-cost-of-bad-data) for the financial stakes that governance is designed to prevent. [The 6 Dimensions of Data Quality](/blog/the-6-dimensions-of-data-quality) gives you the measurement vocabulary that governance provides the framework to apply.
