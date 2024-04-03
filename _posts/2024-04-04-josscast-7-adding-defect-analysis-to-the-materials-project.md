---
layout: post
date: 2024-04-04 00:00
title:  "JOSSCast #7: Adding defect analysis to the Materials Project – Jimmy Shen on pymatgen-analysis-defects"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Adding-defect-analysis-to-the-Materials-Project--Jimmy-Shen-on-pymatgen-analysis-defects-e2htv5a" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)

Jimmy Shen sat down with Arfon and Abby to discuss the role of defect analysis in semiconductor research, the Materials Project, and the development of pymatgen-analysis-defects.

Jimmy is a postdoc at the Lawrence Livermore National Laboratory where he tries his best to automate himself away.

You can follow Jimmy on GitHub [@jmmshn](https://github.com/jmmshn), [Linkedin](https://www.linkedin.com/in/jmmshn/), or on [Google Scholar](https://scholar.google.com/citations?user=m3EreJcAAAAJ&hl=en).

### Episode Highlights:

- **[00:02:19]** Introducing pymatgen-analysis-defects and the Materials Project 
- **[00:07:09]** pymatgen packages
- **[00:07:36]** Importance of defects in semiconductor research
- **[00:11:19]** Target audiences and alternatives
- **[00:15:11]** pymatgen-analysis-defects in the broader open source ecosystem
- **[00:18:15]** JOSS review
- **[00:19:12]** Contribute to pymatgen-analysis-defects

### Links:

- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05941](http://joss.theoj.org/papers/10.21105/joss.05941)
- pymatgen-analysis-defects repository: [https://github.com/materialsproject/pymatgen-analysis-defects](https://github.com/materialsproject/pymatgen-analysis-defects)
- Jimmy on ([GitHub](https://github.com/jmmshn), [Linkedin](https://www.linkedin.com/in/jmmshn/) [Google Scholar](https://scholar.google.com/citations?user=m3EreJcAAAAJ&hl=en))
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))
- [Donate to JOSS](https://numfocus.org/donate-to-joss)

### Transcript:

[00:00:05] **Arfon Smith:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by and for researchers. My name is Arfon

[00:00:12] **Abby Cabunoc Mayes:** And I'm Abby.

[00:00:13] **Arfon Smith:** and we're your hosts.

Every other week, we interview an author published in the Journal of Open Source Software, JOSS.

This is episode seven, and today we're chatting with Jimmy Shen about their paper, pymatgen-analysis-defects: a Python package for analyzing open source Point Defects in Crystalline Materials. Jimmy is a postdoc at the Lawrence Livermore National Laboratory, which I've been to. I've sat outside on the big sign.

It's I've not been in, but I've sat on a wall which got like, very nice, nice California day

[expand]

[00:00:44] **Abby Cabunoc Mayes:** you got a

[00:00:44] **Arfon Smith:** years ago. I actually probably can dig out the photo if you're interested. 

[00:00:48] **Abby Cabunoc Mayes:** In the show notes!

[00:00:49] **Arfon Smith:** yes I learned today that defects are good if you're a semiconductor researcher. So that's today I learned.

[00:00:57] **Abby Cabunoc Mayes:** And I, so I don't think very much about hardware. Computers just work magically for me. So this was a nice way to get into more of the nitty gritty, and it was interesting hearing the kind of research that's being done to make them even more efficient. 

[00:01:09] **Arfon Smith:** I did. For a minute, I got a little bit lost in my head with the, you do semiconductor research with computers to make computers better doing semiconductor research. So it's like this weird recursive loop. I think it makes sense.

[00:01:24] **Abby Cabunoc Mayes:** Yeah,

[00:01:24] **Arfon Smith:** Yeah, I think it's fine.

[00:01:25] **Abby Cabunoc Mayes:** own tail is what Jimmy said. 

So. 

[00:01:28] **Arfon Smith:** Yes, exactly. Yeah. So, and it turns out this is a very rich ecosystem of Python tools, I think which was cool to learn about.

What else? What else did we learn?

[00:01:37] **Abby Cabunoc Mayes:** I think, yeah, the other big thing for me was that giant ecosystem of the Materials Project, and just seeing how that ecosystem's able to thrive and just bring in more people. been really interesting.

[00:01:49] **Arfon Smith:** Yeah, I agree. Side note, I had not noticed that the same group had published so much in JOSS, so there you go, that shows how much attention I'm paying. But that's fine. Actually, no, in my defense, probably some of that stuff will have gone through material science track, some of it will have gone through, the computer science track, so they will have been managed by different editors and editors in chief.

But, it's cool. They're clearly producing a lot of great software and this was a really nice project to hear about today. So,

[00:02:13] **Abby Cabunoc Mayes:** Alright, let's play the interview.

[00:02:14] **Arfon Smith:** let's go.

Welcome to the podcast, Jimmy.

[00:02:16] **Jimmy Shen:** Hi. How you guys doing?

[00:02:17] **Abby Cabunoc Mayes:** We're

[00:02:18] **Arfon Smith:** Good. Great.

[00:02:18] **Abby Cabunoc Mayes:** Great to have you here.

[00:02:19] **Arfon Smith:** All right. So Jimmy, tell us about why you started the project. What does this code base do?

[00:02:23] **Jimmy Shen:** Yeah so The project itself is an extension of a much bigger project called pymatgen, which we think about as the object oriented interface to material science and chemistry, and it's what's being used to power the Materials Project, which is a very popular online repository of data and search engine for materials properties. it's in fact, I think, basically the most popular materials informatics platform on earth. And a lot of modern day material informatics is really focused on automating quantum chemistry workflows and generating and curating a lot of data from these workflows into predictions, scientific insights, and also data for machine learning models to then make more novel predictions. So, this code is really kind of designed to work independently as a defect analysis package for one thing, but it's also designed to work with a lot of the automation tools that we've been building over the last couple of years including another recent publication in JOSS for this package Jobflow which is a decorator based general high performance computing workflow engine that can help you orchestrate and manage lots and lots of calculations on your high performance computing system. 

So it'll automatically define pieces of work that you need to do in Python and serialize those of work and put them onto a database of tasks to complete. And then once it completes those tasks, it'll grab, store the data and and put them into its proper format on a combination of MongoDB and AWS S3 storage options. So basically this package is really meant to interface with the surrounding ecosystem of Materials Project packages and make automation of point defects in semiconductor materials a lot more accessible than was previously possible.

[00:04:39] **Arfon Smith:** That's really interesting background, Jimmy. Thanks for that setup. 

On an earlier episode, we had another person talking about some quantum chemistry packages and some work that they've done.

I was curious if you said, you know, there's, for a given defect, there may be multiple different calculations run, which makes a ton of sense. Are you typically doing those with the pymatgen project as well? Or could you say what packages those are that you're using, or is that part of pymatgen?

Could you say a little bit about the actual calculation piece and where that happens and who does it?

[00:05:10] **Jimmy Shen:** So yeah, so basically we try to be very cognizant of the fact that like we're doing a lot of software development and like a lot of times the tools that we build are not material science specific at all. So basically every time we kind of identify a whole area of problems that need solving you try to solve a very particular problem first.

So for workflow automation . There is a package, it's Jobflow, that is not quantum chemistry aware at all. It has no idea about any of the kind of eventual goals that we're trying to reach, it's just there to serialize jobs and put the tasks that you need onto a database. So the fundamental thing for defining pieces of work, is a separate package that doesn't consider material science.

There are kind of weird interdependencies between all of these packages, but we try to isolate out individual pieces of computer science ideas, like workflow definition and workflow automation into separate packages, and then basically at the very end, you slap pymatgen, which you can think about it as the object oriented interface to quantum chemistry. You slap that on top of whatever set of general Python tool you build and then you get a new kind of framework for doing something. 

Yeah, so in this instance we basically take this package and quite a few other things and you combine these with Jobflow. There's a another package that's going to come up. It's been out for a while It'll be published very soon called atomate2, which is basically combining all of the new material science development that we've done on different parts of pymatgen and possibly other codes. Combine this with Jobflow and you get a lot of formal definition of quantum chemistry workflows. 

[00:07:09] **Abby Cabunoc Mayes:** Another reason why I was excited about this, this paper was actually nominated by one of the editors because it was part of the Materials Project ecosystem. It was nice to hear just you talk about that a little bit. 

I did have a question about defects. So I understand building a database super important, especially in this AI age. We need clean data that we can use to get really valuable insights. But why would we want to be studying defects? I'm not as familiar with the material space.

[00:07:36] **Jimmy Shen:** So, the end, well, maybe not the end goal, but like a very, very important part of this is understanding the operation properties of semiconductors. So, a lot of what we do is kind of feels like a snake eating itself. So, it's

[00:07:53] **Abby Cabunoc Mayes:** Ouroboros.

[00:07:53] **Jimmy Shen:** we're, yeah, because we're using ridiculous amounts of computing power to run these quantum chemistry calculations to predict the properties of semiconductor materials to then eventually make better chips to then eventually do more quantum chemistry calculations. So, so,

[00:08:13] **Abby Cabunoc Mayes:** fun, okay.

[00:08:15] **Jimmy Shen:** So, semiconductor by themselves, they're actually pretty boring. But when they have dopants and defects in them, that's when all of their kind of interesting properties come out . And then the entire semiconductor industry, a lot of their control and manipulation of silicon up until this point is through manipulating the defects and dopants.

So a lot of the important properties of high quality semiconductor materials are 90 percent determined by the defects. 

[00:08:50] **Arfon Smith:** So it's a defect because it's not a sort of perfect, uniform molecular structure or something, but it's actually a designed defect. Defects are good

[00:08:58] **Jimmy Shen:** Yeah, so

[00:08:59] **Arfon Smith:** are better than others. Presumably, is that the right way to think about it?

[00:09:02] **Jimmy Shen:** Yeah, so the real way to think about this is like you imagine you have silicon. There's four electrons for every silicon. You know doing atomic orbitals in high school, right? The atomic some of them are filled some of them are unfilled and then when you kind of squeeze all the atoms together, all of these orbitals they interact with each other, but they still look kind of the same, right?

You have filled orbitals and you have unfilled orbitals. That's kind of what's happening in a pristine crystal. And if you have silicon and then you introduce something else that usually has one extra electron in the silicon, you introduce that into the lattice, then that extra electron, it would tend to go into one of the previously unfilled orbitals, and there's a gap between these orbitals.

So now he's kind of stranded by himself up here. So the important difference is when you're completely filled or completely empty, the electrons aren't able to move. It's really when you have this like little bit of space, either when you remove an electron from these filled bands or you introduce an electron into the unfilled bands, they're really free to move because they have nothing else to interact with in a very hand wavy argument. So all of the electrons that are actually being carried throughout your devices, they come from defects and dopants in them. Like if you had completely pristine silicon without you pumping a huge amount of electricity into them, it's not gonna have any mobile electrons.

So yeah, so that's where the general interest in defects come from, right? And then a lot of materials development in the semiconductor industry is really focused on kind of understanding and manipulating the charge carriers in these defects. So basically, yeah, having a database of these basic properties would be really, really useful in that area.

[00:10:57] **Abby Cabunoc Mayes:** Okay yeah that makes a ton of sense. Thank you for that throwback to highschool.

[00:11:00] **Arfon Smith:** I was going to say, yeah, I'm drawing atomic shells and valences in my head as you were speaking. So I'm seeing it. So you talk about this sort of database of different defects and their properties, like who's the target audience, I guess, for the software, but maybe also for the outputs of the software. Could you just talk about what audiences are you serving with this work?

[00:11:18] **Jimmy Shen:** Yeah, sure. So, the final database, whatever form it takes, we're still In the process of figuring all of that out, because, these are some of the most expensive workflows that we developed in terms of computational cost. So how much of this we're going to run and where it'll eventually get hosted, we're still not sure. But we can use kind of, examples from kind of previous types of work, so if we think about cathode, like battery cathode materials. So that's something that gets hosted on the Materials Project. And that really is being used by just a lot of material science researchers across the world. So ideally there will be one component of this, which is just a basic search engine type situation where you come in and you filter for properties and quickly access some information that you need, right?

And then there'll be another part of this where you programmatically access a lot of these properties, and then try to do computational research on top of them. Whether that's, AI focused , building more advanced machine learning models for these predictions, or whether you're just interested in tweaking these because you might be just doing research on a particular material. You might want to tweak these calculations to fit your own needs, right? 

So those are the kind of two end target audiences for the data. And the target audiences for the code is basically everyone who's trying to do the same type of stuff that I am. So when I was doing my PhD, you could get a decent chunk of your PhD done by doing a handful of these calculations, and now we're in the process of scaling this up to tens of thousands or hundreds of thousands of money permits.

[00:13:17] **Arfon Smith:** Nice. And it also makes sense why LBL is involved, right? I mean, a place where there's lots of computers computationally intensive sort of research is often is there often something in the U. S. that the national labs are very involved in, right?

[00:13:30] **Jimmy Shen:** yeah, you can't really do this at like normal university scale. 

[00:13:35] **Abby Cabunoc Mayes:** I did have a question about alternatives. Why would a researcher choose this piece of software rather than something else?

[00:13:41] **Jimmy Shen:** so I think the main reason for choosing this is, like, it's completely integrated with all of the other tools. So there's actually been work within our group that have tried to tie these defect simulations with the automation work engines that we have, right.

And that proved to be extremely difficult. And that ended up not combining due to various technical reasons. So over the last six or seven years all of those technical hurdles came down, right? So we gradually got rid of basically hurdles related to object storage, hurdles related to manipulating volumetric data. So, our general workflow engine which It's this Jobflow thing that was recently published, that got a lot better. So it went from basically you having to learn a new system to design all of your workflow with. The new workflow engine is really just you write general Python code with some caveats. You put the right decorators on things and then everything just ties together automagically. So it's a lot easier, especially when you're writing really complex workflows,

Things that were essentially impossible with the old stuff, it becomes almost trivial in the new way of doing things. So it's when those technical hurdles came down, we're like, okay, yeah, there's enough tools here. We can actually build this.

[00:15:11] **Arfon Smith:** I'm just going to ask about the sort of broader ecosystem. I mean, it sounds like you're working on a really rich set of packages and capabilities in the Materials Project, but how does this project fit in the sort of broader open source ecosystem? Like, what are the important dependencies that you have that you aren't working on yourself?

Like, obviously Python's a big dependency for you all, but like, what are the things out there in the ecosystem do you sort of take? As a hard dependency for the project? Can say a A bit about that?

[00:15:41] **Jimmy Shen:** Yeah. So one of the packages here is called Monty. This was developed and named, I think, around 2011. So the fact that they called it Monty, it kind of gives you an idea of like how crucial they think a lot of the capability is.

[00:15:59] **Arfon Smith:** Yeah,

[00:15:59] **Jimmy Shen:** basically like that's just a extension toolkit to Python that we use at every step of the process. So that's a pretty hard dependency, and that's just really like a lot of tools for serializing and deserializing data, and processing data in a way that's commensurate with our very MongoDB and very JSON focused data workflow. So I would say like that's the sort of root of this kind of very, very big tree. And then on top of that, you have pymatgen, which is the base package that does a lot of the object definitions that a lot of these later packages that are focused on quantum chemistry rely on. And then from that, I think there's a lot of different things that have branched out, some of them affiliated with Materials Projects, some of them not. There's a lot of action happening in this space. And basically pymatgen and Monty are kind of at the root of this branching tree of packages.

[00:17:08] **Abby Cabunoc Mayes:** Nice. Are you using MongoDB to build this database of defects?

[00:17:12] **Jimmy Shen:** Yeah, so.

[00:17:14] **Abby Cabunoc Mayes:** like MongoDB.

[00:17:15] **Jimmy Shen:** yeah, the, actually we were always on MongoDB but one of the things that we kind of realized was a barrier for a lot of the work a few years ago was the fact that MongoDB alone wasn't enough. So we actually natively now support this Chimera storage scheme where like everything looks and feels like MongoDB at a top level, but like lower down, large objects are kind of automatically serialized into, AWS storage, so they're automatically put there, but then at the top level from query, it behaves as if it's still a MongoDB object. We want to make sure the scientific researchers aren't spending too much time worried about the flow of data and everything, so that way if you set up this one config file properly, you should be able to just perform queries and have a combination of MongoDB and AWS S3 take care of everything on the back end.

[00:18:15] **Arfon Smith:** For sure. I wanted to switch tracks a little bit and just talk about JOSS for a second and ask firstly, why did you decide to publish there and how did it go?

[00:18:23] **Jimmy Shen:** Yeah. so basically I heard really, really good things from my friend about the review process for JOSS. It's open, so that's really a brush of fresh air for junior researchers because it feels really nice to just have that process be out.

And the outcome of the process is you know, I think a lot of us care a lot about the overall quality of our code. So everyone that I've talked to has said that they were able to improve their code quality significantly just as part of this process, because it's really hard to get another person to look at a repo that carefully. Usually, right? So that was just an opportunity that I didn't want to pass up.

[00:19:12] **Arfon Smith:** Nice. Great. I'm glad to hear that worked out well for you.

[00:19:15] **Abby Cabunoc Mayes:** Yeah. And back to the software itself if other people want to contribute to pymatgen analysis defects, how can they help you? What skills do they need?

[00:19:23] **Jimmy Shen:** Yeah so I think like anyone that's interested in defect science and anyone that's interested in materials in general, I think there's always things that they can do to help, right? There are tools within here that are not actually defect specific. Like one of the main, workflows that we use to discover new cathode materials , it utilizes tools that are built within this package, right?

So, that was something that existed previously. And then we kind of realized conceptually that this was the best place to put it. So yeah, anything in the pymatgen ecosystem could always use more help. 

And then if it's related to point defects in any kind of material.

So if you care about an isolated atom in a crystal for any reason, I think a good place to contribute some of that code is, within this namespace package by itself. Right, but the more important thing is just people invest in the pymatgen ecosystem in the first place.

[00:20:27] **Abby Cabunoc Mayes:** Yeah, and I think especially with the broader Materials Project, I think that's a good call to action. 

[00:20:32] **Jimmy Shen:** Yeah.

[00:20:32] **Arfon Smith:** Jimmy it's been really fun to hear about your work today and the whole collaboration, the whole ecosystem of tools you're actively developing in. How can people keep up to date with your work either in open source or academically more generally, do you have places you would want people to to follow you?

[00:20:50] **Jimmy Shen:** Yeah. So I have a Google Scholar. I have a Google Scholar and I have a GitHub. I think if you're a researcher, that's kind of what you live out of.

[00:21:00] **Arfon Smith:** Yep. That sounds like a good combo. Yep.

[00:21:03] **Abby Cabunoc Mayes:** Yeah, well, we'll put both of those in the show notes.

[00:21:05] **Jimmy Shen:** Yeah.

[00:21:05] **Arfon Smith:** Absolutely. Again, thank you so much for your time today. It's been really fun to learn about your work and thanks again for sharing pymatgen-analysis-defects with us. It's been really, really nice conversation.

Thanks. Thank you again for your time.

[00:21:18] **Jimmy Shen:** Alright, thank you guys.

[00:21:19] **Abby Cabunoc Mayes:** Thank you so much for listening to Open Source for Researchers. We showcase open-source software built by and for researchers, you can hear more by subscribing in your favorite podcast app. 

The Journal of Open Source Software is a community-run journal relying on volunteer effort. If you'd like to support JOSS, please consider making a small donation towards running costs at numfocus.org/donate-to-joss. That's N U M F O C U S.org/donate-to-J O S S. 

Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes. Edited by Abby and music CC-BY Boxcat Games. 


[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/Zpxmppy0Wwo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>