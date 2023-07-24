---
layout: post
date: 2019-06-04 00:00
title:  "Cost models for running an online open journal"
authors:
- danielskatz
- labarba
- kyleniemeyer
- arfon
category:
- blog
---
The Journal of Open Source Software (JOSS) is a free, open-access online journal, with no article processing charge (APC). We are committed to operating as a free service to our community, and we do so thanks to the volunteer labor of editors and reviewers, and by taking advantage of existing infrastructure. In this post, we examine the true costs of running a journal such as JOSS, and make the case that even when considering all services we don’t currently pay for, the true cost per paper would not exceed $100. Current APCs at many “gold” open-access journals exceed that by one or more orders of magnitude, (see, for example, [PNAS](https://www.pnas.org/content/early/2019/01/24/1900359116), [Nature](https://www.nature.com/openresearch/publishing-with-npg/nature-journals/), [IEEE](https://open.ieee.org/index.php/for-authors/article-processing-charges/), etc.)

### Real costs we \*have\* to pay

- Annual Crossref membership: $275/year
- JOSS paper DOIs: $1/accepted paper
- JOSS website hosting: $19/month
- JOSS domain name registration: $10/year

At 300 papers/year, this is $813, or $2.71/paper. This is what we actually pay today, covered by a grant from the Alfred P. Sloan Foundation.

JOSS is a fiscally sponsored project of NumFOCUS, through which we can receive donations. We remind authors about the opportunity to donate as part of the message announcing the acceptance of their papers. Over about 3 years of operation, we have received $285 in donations from a small number of individuals. (If you wish to donate now, use the NumFOCUS [secure form!](https://numfocus.org/project/open-journals))

### Services for which we don't currently pay

The one-time cost for initial development of Whedon, the service (bot) that runs in an issue tracker, and the JOSS web application that runs http://joss.theoj.org would have cost an estimated $50,000 (0.25 FTE). This was covered by a combination of volunteer effort by the JOSS EiC (Arfon Smith), and a small grant from the Sloan Foundation. If amortized over first 1,000 papers, this would add $50/paper during that period, but that's also the time when the journal needs to keep costs down to encourage submissions. Let's instead imagine we have to redesign and reimplement our system from scratch every 10 years, and add $5,000 per year for this.

In addition, we require some ongoing development of the existing system every year (adding features, fixing bugs, etc.), at an estimated cost of $5,000/year. This is now mostly done by volunteers, but also partly supported by the Sloan Foundation grant.

We currently host JOSS papers and run reviews on GitHub, which we don't pay for. If we had to pay for this, or we wanted to run our own system for some reason, we could use GitLab for issue tracking instead, at $50/month.

Another aspect is running the organization that publishes the journal. Currently, we depend on [NumFOCUS](https://numfocus.org/) as our fiscal sponsor to provide us with the ability to accept funds such as the Sloan grant and donations, to pay for needed items and services, and to provide some financial management/accounting services. This is paid for by the overhead on the Sloan Foundation grant, which is handled by NumFOCUS. If we were to pay for these services directly, they might cost $10,000/year.

Summarizing these additional potential costs:

- Reimplementation of software infrastructure every 10 years: $5,000/year
- Ongoing software infrastructure development and maintenance: $5,000/year
- GitLab instance: $50/month
- Financial services: $10,000/year

### Additional volunteer contributions

We depend on a set of volunteers to run JOSS. These include 
- 1 Editor-in-chief working 4 hrs/week (0.1 FTE)
- 4 Associate Editors-in-Chief (including the EiC), working a total of 10 hours/week, where the 4 rotate, so only one is on duty in any given week (0.25 FTE)
- 27 Editors (including the AEiCs), working a few hours per week (~1.5 FTE)
- 651 reviewers (as of 30 May 2019), working when assigned a paper

JOSS does not pay any of these people. Nor are these roles in other scholarly journals paid positions (with rare exceptions), whether open access or not, whether the publishers are for-profit or not. We are [aware](https://www.scienceguide.nl/2019/04/so-what-about-editor-compensation/) that some publishers/journals pay stipends to the editor-in-chief (ranging from a few thousand dollars to in some cases ten to twenty thousand), and a couple of publishers/journals have in-house salaried editors.

### Editing/Design

We rely on authors to provide "camera-ready" articles, though we help them generate these articles via an automated system that accepts markdown text and author-supplied images. We do not work directly with the authors to improve their article design/layout. Editors and reviewers do suggest changes to wording in articles as part of the review process, but we do not provide or apply professional copy-editing, which a few journals do. Given that the average journal doesn't provide more author services than we do, and many provide less (editors do not provide as much language/grammar help), we will not consider any costs associated with these services.

### Marketing

We do not have any marketing costs, other than giving out some stickers from time to time, at minimal cost. While we recognize that some large publishers regularly attend conferences where they have booths and have other marketing costs, we will not consider any costs associated with marketing since we don't really do any.

### Summary

Here are all the costs associated with running JOSS, assuming 300 papers/year:

- Costs we now pay: $813/year
- Services for which we don't currently pay: estimated at $20,600/year
- Volunteer editor services: 1.85 FTE effort or $370,000 (@$200,000/FTE)
- Reviewer time (not paid for in almost all journals, nor costed by JOSS)

This would lead to a valuation of the work required per paper of about $1,300 (excluding reviewer efforts), but given current practices regarding editor compensation, including just $10,000 as editor stipend (likely on the high side of today's practices), we obtain a total annual operating cost of $31,413, requiring an article processing charge (APC) of about $100 per paper.

If we were a for-profit organization, we would also add a profit margin. While 10% is considered a good profit margin in many industries, 30-35% is more common in scholarly publishing. This would still only lead to an APC of about $140/paper.

Existing publishers and professional societies might consider adopting an online and [open infrastructure like JOSS’s](https://github.com/openjournals/joss) to reduce their costs. In any event, JOSS will continue to be openly accessible and free to publish.
