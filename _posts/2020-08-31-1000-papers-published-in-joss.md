---
layout: post
date: 2020-08-31 00:00
title:  "1000 papers published in JOSS"
category:
- announcements
---

Today we reached a huge milestone at JOSS – we published our [1000<sup>th</sup> paper](LINK)! JOSS is a developer friendly, free-to-publish, open-access journal for research software packages. Publishing 1000 papers (and reviewing the corresponding 1000 software packages) over the past ~4 years has been no small feat. This achievement has been possible thanks to the efforts of our journal team and community of reviewers who have all given their time to make JOSS a success. We take this opportunity to review some of what we’ve learnt over the past four years and outline some plans for the future.

## A brief recap

Much has been written[^1] on the topic of research software, and the challenges that individuals face receiving credit for their work. Software is critical for modern research, yet people who invest time in writing high-quality tools often aren’t well rewarded for it. The scholarly metrics of the "impact" of a researcher’s work do a poor job of supporting software (and more).

JOSS was created as a workaround to some of the challenges for supporting software development in academia. Launched in [May 2016](https://www.arfon.org/announcing-the-journal-of-open-source-software), JOSS provides a simple, reliable process for receiving academic career credit (through citation of software papers) for writing open source research software. Authors write and submit a short article (< 1000 words) about their software, and JOSS reviews the paper _and the software[^2]_, [reviewing it for a variety of qualities](https://joss.readthedocs.io/en/latest/reviewer_guidelines.html) including function, (re)usability, documentation[^3].

In establishing JOSS, we wanted the editorial experience to be very different from a traditional journal, and _developer friendly_ – short papers authored in Markdown, review process [on GitHub](https://github.com/openjournals/joss-reviews/issues), open process and documentation – while at the same time following best practices in publishing depositing first-class metadata and open citations with Crossref, archiving papers and reviews with Portico, leaving [copyright for the JOSS papers with authors](https://joss.theoj.org/about#content_license) and more.

We describe the journal this way: JOSS is an open access ([Diamond OA](https://en.wikipedia.org/wiki/Open_access#Diamond/platinum_OA)) journal for reviewing open source research software. With a heavy focus on automation, our open and collaborative peer review process is designed to improve the quality of the software submitted and happens in the open on GitHub. 

## Some lessons learned publishing our first 1000 papers

### JOSS is meeting a need of the research community

Something unclear when starting JOSS was whether demand from the research community would be sufficient. A few years in, we can safely conclude that JOSS is meeting a real need of the academic community. 

It has taken us a little over four years to publish 1000 papers and before pausing submissions for two months starting in early March 2020 (to give relief to our volunteers during the pandemic), we were projecting to reach this milestone sometime in June this year. It took us a little under a year to publish our [100th paper](https://joss.theoj.org/papers/10.21105/joss.00248), and an additional 8 months to reach our 200th. In that time we’ve grown our editorial board from an [initial group of 10](https://peerj.com/articles/cs-147/#p-2) to [more than 50 today](https://joss.theoj.org/about#editorial_board). 

<img width="962" alt="Screen Shot 2020-08-25 at 14 07 30" src="https://user-images.githubusercontent.com/4483/91291592-2ecfd980-e78d-11ea-8052-289e93427e1b.png">

### People are reading and citing JOSS papers

Well over half of all JOSS papers have been cited, and many have been cited [hundreds of times](https://scholar.google.com/scholar?hl=en&as_sdt=0,38&q=source:%22Journal+of+Open+Source+Software%22). 

While not designed for it, JOSS is proving a useful resource for people interested in new research software: JOSS currently receives ~10,000 monthly visitors to the JOSS website and provides language (e.g., [https://joss.theoj.org/papers/in/Python](https://joss.theoj.org/papers/in/Python)) and topic-based (e.g., [https://joss.theoj.org/papers/tagged/Exoplanets](https://joss.theoj.org/papers/tagged/Exoplanets)) search filters and feeds.

### People are key

Every journal relies upon the expertise, knowledge, and time of their reviewers and JOSS is no different. *925* individuals have contributed reviews for our first 1000 papers, [many having reviewed multiple times](https://gist.github.com/arfon/dfa38f0bbf89617160b350de8bc9f3c4#file-reviewers-md). 

<center>
💖💖💖 THANK YOU 💖💖💖
</center>

Like many journals, as the number of submissions grows, JOSS has had to scale its [human processes](https://blog.joss.theoj.org/2019/07/scaling). Over the past few years we’ve added many more editors and [associate editors-in-chief](https://blog.joss.theoj.org/2018/12/call-for-editors#introducing-our-three-new-associate-editors-in-chief) to enable papers to be handled efficiently by the editorial team. Simultaneously, we’ve developed our editorial robot [_Whedon_](https://github.com/openjournals/whedon-api) from being an occasional assistant during the review process to being the backbone of the whole JOSS editorial process. 

### Automation is important

A big part of keeping our costs low is automating common editorial tasks where at all possible. The primary interface for editors managing JOSS submissions is a GitHub issue with the assistance of our [Whedon bot](https://github.com/openjournals/whedon-api) who supports a [broad collection of common editorial tasks](https://joss.readthedocs.io/en/latest/whedon.html). Other than having reviewers, editors and authors read papers, Pandoc-generated proofs _are the final version_, and no additional copy editing is done before a paper is published. PDF proofs and Crossref metadata are [generated automatically](https://github.com/openjournals/joss-reviews/issues/2180#issuecomment-646568350) by Whedon, and when the time comes, deposited with Crossref and published [automatically too](https://github.com/openjournals/joss-reviews/issues/2180#issuecomment-646569439).

<img width="966" alt="Screen Shot 2020-08-24 at 08 50 57" src="https://user-images.githubusercontent.com/4483/91291776-75bdcf00-e78d-11ea-9f96-cad8c501e758.png">

When starting JOSS, we thought that automation could be a big part of how things would work if the journal became successful. 1000 papers in, we believe it has been an absolutely critical part of our operations. We call this [chatops-driven publishing](https://www.arfon.org/chatops-driven-publishing).

### Financial support

JOSS is committed to providing a high-quality service to the community at no cost for authors or readers ([Diamond/Platinum Open Access](https://en.wikipedia.org/wiki/Open_access#Diamond/platinum_OA)). We’re transparent [about our operating costs](https://joss.theoj.org/about#costs) and have written about [cost models for operating an online open journal](https://blog.joss.theoj.org/2019/06/cost-models-for-running-an-online-open-journal).

While JOSS’ operating costs are modest, we’ve benefited from the support of a number of organizations including [NumFOCUS](http://numfocus.org) (the ‘[Open Journals](https://github.com/openjournals/governance)’ organization is a sponsored project of NumFOCUS), the [Gordon and Betty Moore Foundation](https://moore.org), and the [Alfred P. Sloan Foundation](https://sloan.org). It’s also possible to [donate to JOSS](https://numfocus.org/donate-to-joss) if you would like to support us financially.

## To the future! 

With 1000 papers published and a further ~170 papers [under review](https://github.com/openjournals/joss-reviews/issues) JOSS is _busier than ever_ and there’s little sign of demand from the community slowing. 

Over the next year or so, we’re going to be investing resources in a number of key areas to enable JOSS to scale further, improve the experience for all parties, and help others reuse the infrastructure we’ve developed for JOSS. We’ve captured much of what we want to achieve in this [public roadmap](https://github.com/openjournals/joss/blob/master/ROADMAP.md). All of this will be possible thanks to a new grant from the [Alfred P. Sloan Foundation](https://sloan.org), some highlights include:

**Smarter reviewer assignment and management:** Finding reviewers for a JOSS submission is still one of the most time-intensive aspects of the JOSS editorial process (though a large fraction of those we ask to review tend to accept, as they are excited by our mission). We think there’s lots of opportunity for substantially improving the success rate of finding potential reviewers through automation. Making sure we’re not overloading our best reviewers will also be an important aspect of this work.

**A major refactor of our editorial bot Whedon:** Whedon is a critical part of our infrastructure but has become hard to maintain, and almost impossible for other projects to reuse. We’re planning to rework Whedon into a [general framework](https://github.com/openjournals/buffy) with a set of reusable modules for common editorial tasks.

**Investments in open source:** JOSS relies upon a small number of open source projects such as Pandoc and pandoc-citeproc to produce scholarly manuscripts (PDFs) and metadata outputs (e.g. Crossref and JATS). We’re going to work with the Pandoc core team to generalize some of the work we’ve done for JOSS into the core.

For many of us on the editorial team JOSS is a labor of love, and it has been quite a ride growing JOSS from an experimental new journal to a venue that is publishing more close to 500 papers per year. For those of you who have helped us on this journey by submitting a paper to JOSS or [volunteering to review](https://joss.theoj.org/reviewer-signup.html), _thank you_ ⚡🚀💥.

_The JOSS editorial team._

[^1]: [https://doi.org/10.12688/f1000research.11407.1](https://doi.org/10.12688/f1000research.11407.1) &middot; [https://doi.org/10.1109/MS.2020.2973362](https://doi.org/10.1109/MS.2020.2973362) &middot; [http://doi.org/10.5334/jors.242](http://doi.org/10.5334/jors.242)
[^2]: Something hardly any other journals do.  
[^3]: The JOSS review structure was originally derived from the process developed by the [rOpenSci](https://ropensci.org) community for their software review.
