---
layout: post
date: 2020-07-01 00:00
title:  "Minimum publishing unit"
category:
- announcements
---

> tl;dr – JOSS is introducing new submission criteria whereby submissions under 1000 lines of code will automatically be flagged as potentially being out of scope, and those under 300 lines desk-rejected. This blog post describes some of the motivations behind this decision.

Sometime in 2020, JOSS will publish its 1000<sup>th</sup> paper – an incredible achievement by a volunteer team of editors and reviewers.

Since its inception a little over four years ago, the primary goal of JOSS has always been to provide credit for authors of research software. Quoting from the [original blog post](https://www.arfon.org/announcing-the-journal-of-open-source-software) announcing JOSS:

> The primary purpose of a JOSS paper is to enable citation credit to be given to authors of research software.

One challenge we've always struggled with as an editorial team is defining clear guidelines for submissions allowed (and not allowed) in JOSS. Our current submission criteria are [available online](https://joss.readthedocs.io/en/latest/submitting.html) and include language about software having to be a _significant contribution_, _feature complete_, and having an _obvious research application_. In these criteria we also explicitly exclude a category of software we generally call "minor utilities".

### The challenge of defining a unit of publication credit

We think of JOSS essentially granting "1 publication credit" for each software package that is reviewed and published in the journal. In empirical research, a publication is often the result of years of work. In engineering research, rarely does a paper represent less than one year of work. Other fields may vary, but let’s say that a scientific paper resulting from work measured in just months is rare or exceptional. 

Since the earliest days of the journal, there has been a range of views within the editorial team on what level of effort we should require from authors for a submission to be allowed in JOSS – some JOSS editors feeling that every useful piece of software should be considered, others believing that the "bar" for publishing in JOSS should be higher than it currently is. 

### Building trust in JOSS

As an editorial team we want JOSS papers to count the same as any other publication in the CV of researchers who write software. With career credit the [stated primary reason](https://www.arfon.org/announcing-the-journal-of-open-source-software) for starting JOSS, if this isn't true then the mission of the journal is at risk.

In reality this means that our editorial policy requires us to balance two competing needs:

1. Providing an excellent service to authors by offering peer-review of their software and the opportunity to receive career credit for their work.
2. Building the trust of an existing academic culture to accept a JOSS paper as equal to any peer-reviewed journal paper. 

These two aspects are in tension with each other because while we would dearly love to publish _any and all_ research software in JOSS regardless of size/scale and level of effort to implement, part of building and maintaining that trust with the community relies on us ensuring that our published authors can continue to expect JOSS papers to "count" in their future merit reviews and promotions.

### Updates to our submission requirements and scope-checking proceedures

Over the past couple of years, as the number of submissions to JOSS has grown, we've found that our existing [submission criteria](https://joss.readthedocs.io/en/latest/submitting.html) and [proceedures for rejecting papers as out of scope](https://joss.readthedocs.io/en/latest/editing.html#rejecting-a-paper) have been taking a significant fraction of our editorial team time. With a volunteer team of editors, it's essential that we use their time carefully and an update to our proceedures for handling scope assessments is long overdue.

Going forward we're going to adopt the following new proceedures:

**Automatically flagging small submissions**

As part of the [`pre-review`](https://github.com/openjournals/joss-reviews/issues?q=is%3Aissue+is%3Aopen+label%3Apre-review) process, incoming submissions that are under 1000 lines of code[^1] (LOC) will be automatically flagged as potentially out of scope by the EiC on rotation.

Submissions under 300 lines[^2] of code will be desk rejected with no further review.

**Mandatory "Statement of need" section in JOSS papers**

While this has always been preferred, a clear _Statement of need_ section in the JOSS paper is usually extremely valuable in helping the editorial team understand the rationale for the development of the software.

**Gauging the scholarly content of the software as part of the review**

Reviewers will be asked if the software under review is a ["substantial scholarly effort"](https://joss.readthedocs.io/en/latest/submitting.html#substantial-scholarly-effort) and guidelines will be provided on how they can make that assessment.

**A streamlined editorial review process**

Rather than each paper that is potentially out-of-scope being discussed in a separate thread on our editorial mailing list, JOSS is going to move to a weekly review of such papers by our editorial team. Topic editors will be asked to review papers flagged as potentially out of scope in their area and help the EiC team make a decision.

_Arfon M. Smith on behalf of the JOSS editorial team_

[^1]: In a high-level language such as Python or R. More verbose languages such as Java, C++, Fortran etc. will require more LOC.  
[^2]: We realize that introducing numerical thresholds may encourage some authors to unnecessarily "pad" their submissions with additional lines of code to meet our thresholds. As reviewers are already asked to judge the standard of the implementation as part of their review we expect that situations like these will usually be flagged during the review.
