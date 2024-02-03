---
layout: post
date: 2024-02-08 00:00
title:  "JOSSCast #3: Studying Superbugs – Juliette Hayer on Baargin"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/episodes/Studying-Superbugs--Juliette-Hayer-on-Baargin-e2fa787" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>


**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)


Juliette Hayer joins Arfon and Abby to discuss Baargin, an open source tool she created to analyze bacterial genomes, especially those resistant to antibiotics.

Juliette is a PhD Researcher at the French Research Institute for Sustainable Development (IRD, Institut de Recherche pour le Développement), at the MIVEGEC research unit, where she implements computational biology methods for bacterial genomics and metagenomics to understand the circulation and transmission of antimicrobial resistance. 

You can find Juliette on GitHub ([@jhayer](https://github.com/jhayer)), [ResearchGate](https://www.researchgate.net/profile/Juliette-Hayer-2), and X ([@juliette_hayer](https://twitter.com/juliette_hayer)).

### Episode Highlights
- [00:02:21] Introduction to Baargin: Juliette explains that Baargin stands for Bacterial Assembly and Antimicrobial Resistance Genes Detection in Nextflow. She developed it to analyze the genomes of drug-resistant bacteria in various environments.
- [00:06:20] Multiplex Sequencing: Juliette discusses the challenge of assembling genomes for multiple strains simultaneously using high-throughput sequencing technologies.
- [00:07:21] Next-Gen Sequencing and Assembly: The conversation delves into next-generation sequencing, the assembly of short reads, and the emergence of long-read technologies for comprehensive genome analysis.
- [00:09:59] Target Audience: Juliette identifies microbiologists as the primary audience for Baargin, emphasizing its user-friendliness for researchers producing genome data.
- [00:12:50] Nextflow in Bioinformatics: Juliette explains the role of Nextflow in bioinformatics and its popularity, highlighting its benefits for scalable and reproducible workflows.
- [00:17:03] Open Source Philosophy: Juliette shares her commitment to open source principles, advocating for transparency, reproducibility, and collaborative contributions in research.
- [00:19:20] Research Using Baargin: Juliette discusses her published studies, including the identification of drug-resistant E. coli transmission in Chile and ongoing projects in Vietnam and Cambodia.
- [00:20:14] Publishing in JOSS: Juliette describes the benefits of publishing in the Journal of Open Source Software (JOSS), emphasizing the focus on code and transparent review processes.
- [00:23:27] Documentation Importance: The hosts discuss the significance of documentation in software development, with Juliette highlighting its critical role in ensuring usability.
- [00:26:03] Contributions and Skills: Juliette welcomes contributions to Baargin, mentioning that comfort with git and Nextflow is essential for potential contributors.
- [00:28:27] Future Roadmap: Juliette outlines plans for extending Baargin, including adding tools for predicting resistance genes, improving detection of mobile genetic elements, and enhancing multi-locus sequence typing.


### Links
- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05397](https://joss.theoj.org/papers/10.21105/joss.05397 )
- Baargin code repository: [https://github.com/jhayer/baargin](https://github.com/jhayer/baargin ) 
- Nextflow: [https://www.nextflow.io/](https://www.nextflow.io/ )
- Study using Baargin: Multiple clonal transmissions of clinically relevant extended-spectrum beta-lactamase–producing Escherichia coli among livestock, dogs, and wildlife in Chile: [https://doi.org/10.1016/j.jgar.2023.07.009](https://doi.org/10.1016/j.jgar.2023.07.009 )
- Juliette on GitHub ([@jhayer](https://github.com/jhayer)), [ResearchGate](https://www.researchgate.net/profile/Juliette-Hayer-2), and X ([@juliette_hayer](https://twitter.com/juliette_hayer)).
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))



### Transcript

[00:00:05] **Arfon Smith:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by researchers for researchers. My name's Arfon.

[00:00:12] **Abby Cabunoc Mayes:** And I'm Abby.

[00:00:13] **Arfon Smith:** And we're your hosts. The way this works is that every other week we interview an author published in the Journal of Open Source Software and talk about their work. Today we talked with Juliette about Baargin, this software that's responsible for assembling genomes for these bacteria that have resistance to drugs, antibiotics.

When I choose to worry about the world, this is the thing I worry about. The fact that we have these bacteria that are increasingly becoming resistant to antibiotics. It seems like a really important piece of software for potentially the future of humanity.

[expand]


[00:00:46] **Abby Cabunoc Mayes:** Yeah, no, I definitely agree. Whenever I'm taking antibiotics, I get worried. It's like, do I really need this? . I don't help more superbugs come around.

Yeah. 

[00:00:54] **Arfon Smith:** for sure . And also, I had a year back in 2007 to 2008 working in Bioinformatics Institute. I think you've spent time in bioinformatics too. 

[00:01:04] **Abby Cabunoc Mayes:** Yeah, yeah, I actually have a degree in bioinformatics and then I joined bioinformatics lab. I worked there for about five years. So I probably should have known a bit more about bioinformatics when we were talking with Juliette. I also realized I'm still calling it next gen sequencing.

It's been a decade. Is this still the next gen? Who knows?

[00:01:21] **Arfon Smith:** yeah, yes, but we'll forgive you. I think fine. Yeah, it was called NGS, right? I think as I remember it as well. 

[00:01:29] **Abby Cabunoc Mayes:** Now it's high throughput sequencing, is what she said. probably the more modern way to talk about it.

[00:01:36] **Arfon Smith:** So the sort of TLDR for today's episode is, existential risk to humanity --pay attention , listen to two out of date people talking about bioinformatics, and updating their working vocabulary on the topic.

[00:01:48] **Abby Cabunoc Mayes:** It was great hearing her experiences both in JOSS, but also just creating these workflows for other bioinformaticians to use. 

[00:01:54] **Arfon Smith:** For sure. Shall we jump into the conversation?

[00:01:57] **Abby Cabunoc Mayes:** Let's do it. 

[00:01:58] **Arfon Smith:** This is episode 3 and we're talking with Juliette Hayer about their paper Baargin and Nextflow Workflow for the Automatic Analysis of Bacterial Genomics Data with a Focus on Antimicrobial Resistance.

That is a long sentence but it is a great paper so we're going to talk about it. Juliette is a PhD researcher at the French Research Institute for Sustainable Development, and welcome to the podcast, Juliette. 

[00:02:21] **Juliette Hayer:** Thank you very much for Inviting me.

[00:02:24] **Abby Cabunoc Mayes:** Of course. Just to dive right in, so I know before we started recording, you told us how to pronounce Baargin. Can you tell us what that stands for? I know it's an acronym, and maybe a bit about why you started it?

[00:02:36] **Juliette Hayer:** Yeah. So the acronym to start with is

[00:02:39] **Abby Cabunoc Mayes:** Editing Abby here. So we lose Juliette's audio for just a split second and she's explaining the acronym. So Baargin B A A R G I N stands for Bacterial Assembly and Antimicrobial Resistance Genes detection in Nextflow. I'll let Juliette continue to explain why she started the project.

[00:02:56] **Juliette Hayer:** But the way I started is that in the framework of my research program at IRD, so at the MIVEGEC research unit where I work, part of my work is to implement bioinformatics tools to investigate the circulation of antimicrobial resistance bacteria and antimicrobial resistance genes between human, animal and the environment. 

I collaborate a lot with other researchers from Southeast Asia, Africa, and also South America. And so in this context, I developed Baargin. 

You may know some bacteria that you can actually find everywhere, like the Enterobacteria. Some are very famous, like Escherichia coli E. coli also called. They can be found in any kind of environment and some of them can become pathogen. For human or for animals. And some of them can also become highly resistant to drugs through antibiotics. So that's what we study. And, it is actually also the overuse and the misuse of the antibiotics that's leading to this high amount of resistance among the bacteria.

And, it's maybe worth, noting that WHO has said it's a major problem for public health this, antimicrobial resistance. So in some of the research that we do, with the collaborator in Southeast Asia, Africa, and South America. We use genomics and metagenomics approaches to investigate the circulation of these bacteria and their resistance genes.

So the genome is all the genetic material of the bug, of the bacteria, and that's what we study, and we try to sequence with high throughput sequencing technologies. And within this kind of project, we are producing quite a large amount of data that needs to be analyzed, and we need to compare these different bacterial strains, and that's why I started with Baargin. I wanted to develop a bioinformatics workflow that would be easy to use, flexible, and highly scalable to be able to analyze hundreds of different strains at the same time. So that's how I started.

[00:05:14] **Abby Cabunoc Mayes:** So when you're actually doing the sequencing, you're putting hundreds of strains all at once that get sequenced all together. Is that correct?

[00:05:21] **Juliette Hayer:** exactly.

[00:05:21] **Abby Cabunoc Mayes:** Yeah, that's very different than what I've seen before. I haven't done bioinformatics in a long time, but usually it's one specimen, yeah.

[00:05:31] **Juliette Hayer:** exactly. So now you can multiplex, we say, put several strains at the same time on the same flow cell for sequencing and you get a very high throughput of data. So then you, of course, have to split what belongs to who , but you can sequence many at the same time.

And currently in the project. One project in Cambodia that I'm working with, we have about 700 genomes of bacterial strains, mainly Enterobacteria. So that's also why we needed something like this.

[00:06:04] **Abby Cabunoc Mayes:** Yeah, that's really interesting because even just with regular high throughput sequencing, it's a challenge to put the genome back together again. The genome assembly is still tricky, but here it's just another layer where you're putting together multiple different genomes.

[00:06:19] **Juliette Hayer:** So you do it in parallel, yes. The genome assembly is the step that takes the most computing resources of course, but we have now very nice tools that have been developed for doing that and that are quite efficient and do not use that much as they did before.

The one I have included in Baargin is called SPAdes. It's one of the most famous for assembling bacterial genomes. It's very powerful, but, the thing with Nextflow, the workflow manager that I've used to develop Baargin is that it can parallelize the job for like hundreds of strains at the same time.

So that's what's cool. Depends also on your hardware as well.

[00:06:59] **Abby Cabunoc Mayes:** Yeah, and just for anyone listening who's unfamiliar with next gen sequencing, and you can correct me if I'm wrong, Juliette, but there, they, instead of just reading a genome one letter at a time, it like splits it all up into tiny pieces, sequences them all, and then tries to stitch them all back together.

So it's a fun computational challenge, I think. but yeah.

[00:07:20] **Juliette Hayer:** Correct.

[00:07:21] **Arfon Smith:** So, both Abby and I, I think, have been in past lives worked at Bioinformatics Institute. So I actually worked for a year, at the Wellcome Trust Sanger Institute in Cambridge, which was the, one of the places that sequenced the original human genome. So I know a little bit about what were called next generation sequences back in 2008 or something, I guess.

I was curious, what's the hardware that you're using here? Is it those very short read sequences that are being assembled together? Or is it, I know there's some like nanopore stuff that was sort of magical future looking stuff. Like, what's the actual tech that's running under the hood here?

[00:07:59] **Juliette Hayer:** Yeah. So we actually use both. We use basically the short reads technology, which is now, the market is led by Illumina still. The length of the sequences that are produced is usually 150 base pair. So you get two sequences for the same basic sequence, and then you get a lot of them. So that's very high throughput, which is very, very nice.

But then you need to get the assembler reconstruct the longer pieces, which we call contigs. the longer sequences. And sometimes it can be difficult. Most of the time, you cannot get the full chromosome of the bacteria in one go with this. So now they develop the long read technologies like, PacBio and Oxford Nanopore technologies.

And we also use that because that is very amazing to get the full structure of the chromosome or of the plasmids as well, which are the small circular pieces that also run into bacteria and usually carry a lot of resistance genes. So it's also nice to get their structure fully. And the best of the best is to combine both.

So we get the very high quality because of the high throughput of the short that we can map on the long reads. So align, and then you get a perfect resolution of the genomes. And Baargin can take both, either only short reads, or it can take short and long reads as an input, or the already assembled contigs if you wanted to assemble it by yourself before and just go with the rest.

[00:09:38] **Arfon Smith:** That sounds really powerful. It sounds like you've thought about all these different technologies and made it very flexible for different scenarios. Who's your sort of proto typical user? Is it a researcher or would you expect a sort of analyst or an engineer to run this code?

Who do you find uses your software most? 

[00:09:56] **Juliette Hayer:** So my very first audience are my colleagues in my research group and also my collaborators abroad. Some of them really needed something like that. Of course, because it's in Nextflow, you have to run it with the terminal, so you have to have some basics in Unix, just to get it to run. But yeah, the main audience is microbiologists because I think many people nowadays, researcher or engineers or lab technician, they will produce genome data for their strains because now it's something that you do basically every day that, okay, you get a new strain. You will sequence it.

It can be a researcher or other people, but definitely working with microbiology. But yeah, I would advise to have some skills in UNIX. I didn't make a user interface yet, easy click button thing. But that maybe should be in the plan,

[00:10:54] **Arfon Smith:** That's okay, I think there's a whole collection of tools out there that don't have like a nice GUI. The interface is the terminal.

I was actually curious, say I buy myself a sequencer or I wanted to use this tool, are people typically running on big clusters? Is there lots of compute under the hood? Like, how big are the jobs? It probably depends on how much data you have. But, typically what sort of hardware would people be running this tool on?

[00:11:19] **Juliette Hayer:** So I think basically if you have just a nanopore, plug to your laptop and you just sequence maybe, let's say, four or five strains of enterobacteria that have a genome that is like maybe five megabases, something like that. You could run it on a laptop. I think that would be fine. If the assembly can go on, then you're fine.

Of course, you can customize the databases that are used for detecting the antimicrobial resistance genes and the plasmids, and also to make the annotation of the genome after all. If you have a lot of space, if you have an HPC in your lab, it's better if you want to run a lot of strains at the same time, and also to install the larger databases that also provide more power of prediction.

I made it so it could be installed just in a laptop with minimal databases, just to get some results first.

[00:12:19] **Abby Cabunoc Mayes:** Yeah, so if I get my hands on a Nanopore, and I really want to know what bacteria is growing in my bathroom, I could maybe, if it's not too big, potentially sequence it. And run it through Baargin 

[00:12:28] **Arfon Smith:** , Let us know if you take that project on as a side hustle. Abby,

[00:12:32] **Abby Cabunoc Mayes:** I will, yeah.

[00:12:33] **Arfon Smith:** the results. Laughter.

[00:12:34] **Abby Cabunoc Mayes:** So you talked a little bit about Nextflow. Can you tell us a bit about its role in bioinformatics? I think Nextflow is more recent than what either Arfon or I have used. So, it would be great to hear, what it does.

[00:12:46] **Juliette Hayer:** Nextflow is a great, workflow manager. Of course, there are others that exist, so you have different schools with different kind of people. I know there is also SnakeMake. I haven't used it that much, even though I really like coding in Python, and SnakeMake is based on Python.

But Nextflow, I think they started around 2015 maybe. I hope I'm not wrong, I haven't checked that before. But I started using it in, 2017 or 18 when I was then at that time in Sweden and I enjoyed really a workshop that I went to in Barcelona where I started learning about Nextflow and how to use it and how to run pipelines and then I met first people of the NF Core community.

I don't know if you have heard about this, so that's how Nextflow became very big in bioinformatics, because a few people that started using Nextflow for building bioinformatics pipeline, they met together and they started a real community and they started to put some guidelines on how you should develop a Nextflow pipeline for bioinformatics.

So I think they are huge nowadays because they have put out many pipelines, and many that are really highly used by people in bioinformatics.

[00:14:10] **Arfon Smith:** So Nextflow sounds like it's super popular. Yeah, I was also familiar with Snake, SnakeMaker as well. I've not used either. I know they're both popular and there are other tools. Again, I've like aware of like Galaxy workflows. I think that's another tool.

[00:14:23] **Juliette Hayer:** That's different. Yeah,

[00:14:24] **Arfon Smith:** that's another one again.

There are a bunch of reasons to use a workflow management tool, but one of them is just reproducibility and the ability to reliably execute a set of tools those tools. It makes tons of sense. I was curious though, that workflow is executing Baargin at some point, it's gonna be a step in the process.

What other tools before this one were available for these kind of tasks? Did you find yourself unhappy with what was already available? What else people might use if they're not using the software you've created? 

[00:14:54] **Juliette Hayer:** So, maybe just one point about Nextflow again that I'm not sure I have mentioned, but it's based on the language Groovy, which is itself based on Java, and I haven't that, so that's that's worth it. For the other tools that can do several things as what Baargin does, yes of course they exist because many people work on this kind of questions.

One that comes to my mind seem to be really great is Bactopia. I think this is also made in Nextflow but it's huge, it's very complex, it's , in my opinion, quite not easy to install for any user. So, for bioinformaticians and people that are skilled and that know what they are looking for, in the bacterial genome already and which sub workflow they know what they want to do, use, then I would definitely go for Bactopia.

For me, I wanted really something more simple than this and that really had a focus on detecting the plasmid features and the antimicrobial resistance combining different tools that can predict resistance genes. 

And there are also other great tools that exist, but can be specific only for one bacterial species. Like I know about Kleborate, which is a pipeline, also very nice, but only for Klebsiella species, which is a kind of bacteria. 

So that's how I ended up coding Baargin. Also to distribute it to our collaborators that not necessarily have the the computing power that is required for installing very large workflows with a lot of databases and all.

So I wanted something lightweight as well.

[00:16:36] **Abby Cabunoc Mayes:** It was interesting hearing you talk about these, workflow systems, especially Nextflow and things like Galaxy, and how they've built a community around that through best practices and these conferences and stuff.

I know you've made it primarily for your collaborators, but, do you think there's room for this to be more widely used with others? Why did you make it open source to begin with, I think was the real question that I was asking around, but go ahead. 

[00:17:00] **Juliette Hayer:** Yeah, so why did I make it open source? Because I'm a researcher and I'm working with collaborators for from other academic institutions all over the world and I think everything we do should be open source. That's really something I believe and in France in the academic institutions we prone a lot for open source and even more at my institution at IRD. So that is really something that I could not imagine differently. 

Also for reproducibility and for all the people to be able to contribute, that's also important. And to know what they're doing when they are running that, they can go into the code and it's not a black box.

So I think for me, that's very important.

[00:17:46] **Abby Cabunoc Mayes:** So Juliette, have you run many studies using Baargin yet?

Any interesting insights you want to share?

[00:17:51] **Juliette Hayer:** So, me and my collaborators and students are using Baarging a lot. I have one study published where we collaborated with Chilean colleagues, where we identified the transmission of super resistant E. coli between wild animals and livestock and companion animal in farms within and between farms in central Chile.

So that was one study. And then we have other studies ongoing in Vietnam, in different hospitals where we isolated Klebsiella strains where that also are resistant to carbapenem and colistin antibiotics. So that's also interesting. One of my students is working on that. And we have an ongoing project with Institut Pasteur in Cambodia and Battambang Hospital in Cambodia, where we have a lot of bacterial genomes.

That's the one I talked about before, about 700 different bacteria that we collected from patients to start with, that came to the hospital with resistant infection and we went to their household to collect also bacterial strains from their environment, food, and animals that they have.

We have not published that yet, but we are studying, analyzing the results at the moment. So that will be interesting results that will come soon, hopefully.

[00:19:16] **Abby Cabunoc Mayes:** Yeah, it sounds like actual useful information that will help people in the world. So, that's great 

[00:19:22] **Juliette Hayer:** yes

[00:19:23] **Abby Cabunoc Mayes:** cool, so we'll link the published studies in the show notes. 

[00:19:25] **Juliette Hayer:** Yeah, it's really to try to understand how the resistance circulates between the humans and the animals and their environment, like what do they carry, which resistance genes they carry and how do they share it. But yes, I will send you at least the publication that is already published and will keep you updated for the next steps.

[00:19:49] **Abby Cabunoc Mayes:** Yeah, that's great. Yeah, we'll include that in the show notes for sure. 

[00:19:51] **Arfon Smith:** If we could just switch tracks for a second and just talk about JOSS and the fact that you published there. Looking at the paper, I think it was back in October 2023 when the paper was finally published. I was curious if you could just say a bit more about, why you published in JOSS and tell us a little bit about that experience.

[00:20:09] **Juliette Hayer:** So the first idea came from one of my co authors, Jacques Dainat, who had already published in JOSS, and he told me about how amazing was the experience, and how we should always do that when we publish bioinformatics workflows or tools, because everything is centered on the actual tool or pipeline.

And that is central. And also the fact that the code is revised as well, is reviewed by other people that also know about what you're doing and probably are in the same field, because you can choose the reviewers. You have a list of potential reviewers in JOSS that you can select and you have an idea of what they are working with.

And of course, you can visit their GitHub, so that also helps. So that was one great thing, and also everything is open during the review process and transparent. Anyone can see what's happening with the code, and you can get very nice input from the reviewers to also improve your code and the documentation, which is very important.

If I had not published in JOSS, maybe I wouldn't have put that much effort in writing a well structured documentation with examples and tests and all these things that are actually very good for a workflow, for bioinformatics workflow, because I have seen a lot of other workflows that could be published in more standard life science journals.

And then, what? Usually they are almost impossible to install or there is no documentation because they didn't need to do that to publish it. So here, yeah, I think it's good that the code and the documentation is at the center of the whole thing. And also, discussing with the reviewers over GitHub, a tool that we use on a daily basis, that also makes things very convenient.

[00:22:08] **Arfon Smith:** Sounds like you had a good review experience. I just had a quick look over the review again, before this conversation and it looked like it was a super productive conversation and lots of good feedback. I think you're right. One of the key areas where I think authors get most value is the review of documentation. It is so valuable to have somebody know nothing about your tool and just, start with a fresh blank slate, new machine, new environment.

There's probably another name, which is like Journal of Open Source Documentation or something. It's the software of course, but usability often begins with great docs and clearly defined dependencies. But it's just so hard to be objective as the author of software when thinking about what would somebody need to know and the sort of undocumented steps. If we had to look where most changes get made as a result of a JOSS review, my guess would be docs every time.

I think it's the most common area of change and just reinforces that software is not just about the code executing on the machine, but it's all the bits around the side that are so important for the humans as well who are going to be operating that software 

[00:23:21] **Juliette Hayer:** Yeah, 

[00:23:22] **Abby Cabunoc Mayes:** One thing I do like about that process is just how it pushes you to make it more usable for a broader group. I know we talked about, like, are you building that open source ecosystem? This is one step towards that, having that good documentation so others can

[00:23:34] **Juliette Hayer:** That's true,

[00:23:35] **Abby Cabunoc Mayes:** jump in and use it.

Is there anything else you learned going through this review process or you're grateful for?

[00:23:40] **Juliette Hayer:** Yes, they really insisted on running test, so it's not easy to make unique testing and continuous integration when you work with workflows, so I'm very open to suggestions for that and to contribution if people want to help with this, because it's not an easy and trivial task. They gave some hints and some input regarding things that I should try . 

I haven't completely done it, but I have made a full test that can test where you can test all the mandatory steps of the pipeline, but it doesn't test process by process. So that was useful to really make me think about the things that I should improve from that point of view also.

[00:24:20] **Arfon Smith:** Testing something like a workflow tool is probably pretty hard, right? There are some things where we have this challenge with JOSS where we, as part of the review process, as you probably remember, the actual language is a little unusual. We say reviewers must be able to objectively test the functionality or verify the functionality of the software.

So we don't say, you must have a million unit tests and 99 percent test coverage. What we're trying to get to is: You need to be able to verify that this thing works. And that seems like a reasonable thing. But, there are a number of times when that actually can be quite hard. You know, when it's a complex system, maybe it's running on a cluster.

It's really hard for a user to verify that. Custom hardware often makes it hard for people where, you know, you need a particular variant of a GPU or something. Another one is actually just complex user interfaces. If it's just a command line tool with standard inputs and outputs, that can be quite easy to write normal tests.

If it's a really complex set of interactions the user has to do, the testing can be a huge amount of the work, actually. So, yeah, I hope we find the balance there. 

[00:25:33] **Juliette Hayer:** But I think that's something very nice with JOSS is that at least it forced you to have a test that is running on the machine of other people, which not everyone can pretend to have when they publish.

[00:25:47] **Arfon Smith:** It's true. It's true. Absolutely. Yep,

[00:25:49] **Abby Cabunoc Mayes:** So you mentioned that you're open to testing contributions. So if people do want to contribute, what sort of skills do they need? What languages? What sort of background are you looking for? 

[00:25:58] **Juliette Hayer:** I think they need to be quite comfortable or confident using git and Nextflow. That's the basic, because the workflow is coded with system DSL 2. So I have all the steps as modules. All the processes are in separated modules that can be reused in other workflows as well. So it's quite easy if you can code in the Nextflow to add a new module and then, clone the repo and change the main script accordingly to add the step you want to be added in the middle, in the full workflow. So people that also want to modify a part of it or add a step that I did not necessarily have in Baargin already, they can do that, they can clone or fork or suggest me to add If it's something that should be added, of course.

[00:26:51] **Arfon Smith:** It sounds like contributions are welcome, which is great. I was going to say, are there obvious things that you're personally interested in extending the software with at this point? Or is it mostly sort of done for your needs and your collaborators needs?

[00:27:05] **Juliette Hayer:** For the needs we have now, it's mostly done, but no, some tools, I'm already thinking about changing them or adding other options. Because I really like combining different methods for doing the same thing. And so I have at the moment two different tools for predicting the resistance genes, as I said before.

I would be happy to add new ones that are coming. But then I would need to work on harmonizing the results. Which is not necessarily easy because they use different databases, and usually genes in the databases, they can have different names and all, so that's an all different story. But that would be fun, I think.

For the multi locus sequence typing I want to add, now I have a very basic tool that's working on seven genes for typing the bacteria. And I want to add another tool that would use much more genes to base the typing on. So that's the first thing I want to do.

And then there are others, of course. I would like to improve all the detection of the mobile genetic elements. That's something I really need to work with. Investigate other tools that are to be included.

[00:28:22] **Arfon Smith:** Sounds like you've got quite a roadmap ahead of you, actually.

[00:28:24] **Juliette Hayer:** Yeah.

[00:28:25] **Abby Cabunoc Mayes:** yeah, and it also sounds a bit like the kind of contributions that would be most helpful is Other users that have their own use case and they want to add different parts of the workflow and change up a little. Is that, yeah. Cool. Awesome. So if you're listening and you want to use Baargin, Juliette here welcomes your contribution.

[00:28:43] **Arfon Smith:** Sounds like it.

[00:28:44] **Abby Cabunoc Mayes:** Just to close us off, how can people find you online and keep up to date with your work?

[00:28:48] **Juliette Hayer:** So they can find me on GitHub, of course, under @jhayer , where Baargin is released, and you can find me on Researchgate and on X, and it's Juliette underscore Hayer.

[00:29:01] **Abby Cabunoc Mayes:** Perfect.

[00:29:01] **Arfon Smith:** Awesome. 

Yeah. Well, Juliette, thank you so much for coming and being part of the JOSSCast. It's been great to talk to you today about the Software, Baargin, I'm still not saying it right, I'm

[00:29:13] **Juliette Hayer:** It's okay.

[00:29:14] **Arfon Smith:** it's okay, I'm getting better. Okay, Baargin and the problems it solves, it sounds incredibly relevant, I know, I worry about anti bacterial resistance. I think that's a really important thing for humanity to be working on. I'm grateful for the work that you and your team are doing, and for publishing in JOSS.

[00:29:33] **Juliette Hayer:** Thank you very much for having me.

[00:29:41] **Abby Cabunoc Mayes:** Thank you so much for listening to Open Source for Researchers. This is our first episode that we've released since our launch. It's been amazing to see the response. Thank you so much for subscribing for telling your friends for sharing on social media. We love to showcase open-source software built by and for researchers. So subscribe to hear more in your favorite podcast app. 

Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes, edited by Abby and music is CC-BY Boxcat Games. 


[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXCyPMMicEM?si=wRFVSIp_zXge9Pr0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>