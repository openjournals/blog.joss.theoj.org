---
layout: post
date: 2023-15-05 01:00
title:  "JOSS publishes 2000th paper"
category:
- announcements
---

This week JOSS reached a big milestone – publishing our [2000th paper](https://joss.theoj.org/papers/10.21105/joss.05220)! It also happens to be our 7th birthday, and we thought we’d take this opportunity to review our submission stats from the last few years, discuss some of the changes to JOSS we’ve made of late, and reflect on some of the challenges we have faced as a journal.

## Submission summary

Everything discussed here is derived from the amazing work of [one of our editors](http://csoneson.github.io/) (thanks Charlotte!) who created our [submission analytics page](http://www.theoj.org/joss-analytics/joss-submission-analytics.html) which is built nightly based on data from the JOSS API. If you want to dig more into this analysis, the [source code](https://github.com/openjournals/joss-analytics) is available for you to do so.

### High level publication stats

2000 papers over 7 years means, on average, we’ve published 285 papers per year. An average isn’t quite right though of course, with our throughput being substantially lower in the early days.

Year 1 (May 2016 – May 2017): 57  
Year 2 (May 2017 – May 2018): 138  
Year 3 (May 2018 – May 2019): 254  
Year 4 (May 2019 – May 2020): 345  
Year 5 (May 2020 – May 2021): 338  
Year 6 (May 2021 – May 2022): 369  
Year 7 (May 2022 – May 2023): 366  

Note that JOSS closed for submissions between March 2020 and May 2020 due to the COVID-19 pandemic. This likely accounts for the drop in publications in year 5 (May 2020 – May 2021). Looking at the high-level breakdown, it seems like we’ve reached some kind of plateau of around [one paper published per day](http://www.theoj.org/joss-analytics/joss-submission-analytics.html#number-of-published-papers-per-month-and-year). If we were a business looking to grow revenue this lack of year over year growth might be of concern. However, as a volunteer-run journal, this is OK with most of us :-) 

### Submission scope and rejections

In July 2020 [we introduced](https://blog.joss.theoj.org/2020/07/minimum-publishable-unit) a test for ‘substantial scholarly effort’ for all new submissions. You can read more about the motivations for this in our [blog post](https://blog.joss.theoj.org/2020/07/minimum-publishable-unit) but this clearly had an effect on our rejection rate both in the pre-review stage, and during/post review.

<img width="920" alt="Screenshot_2023-05-03_at_11_27_29" src="https://user-images.githubusercontent.com/4483/236413997-99652832-6e6b-43aa-b000-8677b094bfa6.png">

We now reject between 15-30% papers at the pre-review stage, and around 5% during the actual review process itself (note this is in line with our goal to provide a constructive review process, improving submissions such that they can be accepted).

### Authorship

JOSS is no longer dominated by single author submissions. In fact, we are seeing some evidence of more authors per submission with the fraction of submissions with more than 5 authors now approaching 25%.

<img width="812" alt="Screenshot 2023-05-03 at 11 28 53" src="https://user-images.githubusercontent.com/4483/236414177-964ed03b-8392-4597-bf88-72fd4f449a53.png">

![Authors](https://user-images.githubusercontent.com/4483/236414321-286860bb-50f0-4787-a664-60fa7d4fe6f0.png)

### Citations

More than 200 papers have been cited > 20 times. About a third have never been cited. A few papers have  been cited *a lot*: [Welcome to the Tidyverse](http://dx.doi.org/10.21105/joss.01686) currently has nearly 6000 citations.

Papers in more than 6000 different venues have cited a JOSS paper, with the most common being bioRxiv, JOSS, Scientific Reports, Monthly Notices of the Royal Astronomical Society, and The Astrophysical Journal.

### Editor and Reviewer statistics

2093 unique individuals have contributed reviews for the 2000 papers published in JOSS, including [8 amazing individuals](https://gist.github.com/arfon/dfa38f0bbf89617160b350de8bc9f3c4#file-reviewers-md) who have contributed more than 10 reviews each! 

JOSS currently has 77 editors, 6 of whom are track Editors-in-Chief, and one Editor-inChief. 112 editors have served in total on the editorial board.

Unfortunately, our reviews are getting slower. We’re not really sure why, but this has been a noticeable change from our earlier days. Our average time now spent in review is approaching four months, whereas pre-COVID it was under three.

### Software statistics

JOSS reviews are primarily about the software, and so it would be remiss of us not to talk about that. Python is still the #1 language for JOSS submissions, used in part for well over half of published papers (~1200 out of 2000). R is #2 at 445 submissions, and C++ #3 (although of course C++ and C may be used together with another language).

Anecdotally we're seeing an increase in the number of authors submitting to JOSS to declare their submission ‘ready for use’ or declaring as a v1.0 release. This is also potentially supported by the peak close to 0 days between the repository creation date and the submission to JOSS. 

<img width="711" alt="Screenshot 2023-05-04 at 10 29 00" src="https://user-images.githubusercontent.com/4483/236414496-5155bb28-6f59-49ce-b3a8-6e6c4a488331.png">

The MIT, GPL (v3), and BSD 3-Clause licences are still used for the majority of submissions.

<img width="734" alt="Screenshot 2023-05-03 at 11 42 01" src="https://user-images.githubusercontent.com/4483/236423081-e2c2cb7d-17f3-4afa-8655-ac248374ecc3.png">

## Investments in tooling and infrastructure

JOSS has benefited from the kind support of the Alfred P. Sloan Foundation, the Gordon and Betty Moore Foundation, and a number of small development grants from NumFOCUS. This support has enabled JOSS to invest further in our infrastructure and tooling, highlights of which we describe below:

### Editorialbot for all of your GitHub-based review needs

Our former bot Whedon has now become Editorialbot, which is much more than a rename. Editorialbot is now its [own open source framework](https://github.com/openjournals/buffy) that can be used to manage review-like interactions on GitHub (i.e., not just publishing workflows). Currently, Editorialbot is used by rOpenSci, JOSS, SciPy Proceedings, with more coming soon. Thanks to Juanjo Bazán for all of his great work here!

As part of this work we’ve also extracted all of the legacy capabilities from the Whedon codebase to run as a series of [GitHub Actions workflows](https://github.com/openjournals/joss-papers/tree/master/.github/workflows).

### Investments in our Pandoc-based publishing pipeline

JOSS has always used Pandoc to produce our PDF papers and Crossref XML metadata, but the way we used it was… hacky. Over the past few years we’ve been fortunate to work directly with one of the Pandoc core team (Albert Krewinkel) to implement a number of improvements to how we use Pandoc within the JOSS publishing system, and also to contribute new capabilities to Pandoc itself, including improved ConTeXt support, support for JATS outputs, and more sophisticated handling of author names in the Pandoc frontmatter.
  
### Editorial tooling improvements

Last but not least, we’ve also made a bunch of small (and not so small) changes to the way that we handle submissions as an editorial team, including implementing tracks (and appointing a track EiC for each) and a reviewer management tool for searching for appropriate reviewers and tracking reviewer assignments.

Thank you!

Over these seven years of operations, JOSS simply wouldn’t work without the dedicated volunteer editors and reviewers (and of course the authors submitting their work). 

Arfon Smith (EiC, JOSS) on behalf of the whole editorial team.
