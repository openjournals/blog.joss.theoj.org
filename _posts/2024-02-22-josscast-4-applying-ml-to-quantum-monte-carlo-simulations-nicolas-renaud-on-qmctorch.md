---
layout: post
date: 2024-02-22 00:00
title:  "JOSSCast #4: Applying ML to Quantum Monte Carlo simulations – Nicolas Renaud on QMCTorch"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Applying-ML-to-Quantum-Monte-Carlo-simulations--Nicolas-Renaud-on-QMCTorch-e2g2hrf" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)


Nicolas Renaud joins Arfon and Abby to discuss QMCTorch, a PyTorch implementation of real-space Quantum Monte-Carlo simulations of molecular systems, and work to promote research software as a research output.

Nico is the head of the Natural Sciences and Engineering section of the Netherlands eScience Center and Senior Researcher at the Quantum Application Lab. He focuses on the intersection of material sciences and machine learning.

You can find Nico on GitHub [@NicoRenaud](https://github.com/NicoRenaud) or the [Research Software Directory](https://research-software-directory.org/software/qmctorch)

### Episode Highlights
- [00:02:31] Introduction to QMCTorch – recasting Quantum Monte Carlo as a machine learning problem
- [00:09:30] Hardware requirements – run it on the cluster
- [00:11:05] Choosing PyTorch for QMCTorch
- [00:17:40] The Netherlands eScience Center and promoting research software
- [00:18:47] Publishing QMCTorch in JOSS
- [00:19:02] QMCTorch is open for contributions!
- [00:20:51] Future directions for QMCTorch


### Links
- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05472](https://joss.theoj.org/papers/10.21105/joss.05472)
- QMCTorch code repository: [https://github.com/NLESC-JCER/QMCTorch](https://github.com/NLESC-JCER/QMCTorch)
- PyTorch: [https://pytorch.org/](https://pytorch.org/)
- [A light in the dark: Quantum Monte Carlo meets solar energy conversion](https://research-software-directory.org/projects/a-light-in-the-dark)
- Nico on GitHub [@NicoRenaud](https://github.com/NicoRenaud)
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))



### Transcript

[00:00:05] **Abby Cabunoc Mayes:** Welcome to Open Source for Researchers! A podcast showcasing open source software built by researchers for researchers. My name is Abby.

[00:00:12] **Arfon Smith:** And I'm Arfon.

[00:00:12] **Abby Cabunoc Mayes:** And we're your hosts. Every other week we interview an author published in the Journal of Open Source Software, or JOSS.

[00:00:18] **Arfon Smith:** So who did we talk to today, Abby? What are we going to learn about?

[00:00:20] **Abby Cabunoc Mayes:** We talked to Nico, Nicolas Renaud.

[expand]

[00:00:22] **Arfon Smith:** Yep.

[00:00:23] **Abby Cabunoc Mayes:** about his paper, and, you know, honestly, reading the paper, I was a little nervous. I thought this would go a lot over my head, but it was actually a really interesting conversation. Both on the eScience Center in the Netherlands and hearing about the work that they're doing to promote more open source research software.

But also just a nice case study on why Nico decided to make this open source, how he's been approaching it and the tools that he's using to build this.

[00:00:45] **Arfon Smith:** Yeah, it was a bit of a journey through history for me personally as well. I used to do some computational chemistry in a previous life and so learning how some of that tooling has evolved was interesting for me. 

I think the thing that's kind of interesting about computational chemistry is it's historically quite a closed source field. A lot of mega packages, big, expensive licensed tools that you can buy. And so this I think is a really great example of people leveraging some of the more popular machine learning tooling, PyTorch, applying it to CompChem problems.

So yeah, it was super interesting. And as you say, the eScience Center seems to be really at the forefront of a lot of the best and most interesting work in research software engineering space.

[00:01:25] **Abby Cabunoc Mayes:** Yeah, and I think there's a lot of open stuff happening in Amsterdam especially. Because I know I used to work at Mozilla, and MozFest moved there

[00:01:33] **Arfon Smith:** Right.

[00:01:34] **Abby Cabunoc Mayes:** I've never been to Amsterdam, Stroopwafels are my favorite, I still really want to go one day. But

[00:01:43] **Arfon Smith:** us some or something.

[00:01:44] **Abby Cabunoc Mayes:** Yeah, yeah, Yeah.

But yeah, let's dive right into that interview.

[00:01:48] **Arfon Smith:** Sounds good.



[00:01:49] **Abby Cabunoc Mayes:** This is episode number four, and today we're chatting with Nicolas Renaud on his paper, QMCTorch, a PyTorch implementation of real space quantum Monte Carlo simulations of molecular systems.

Welcome, Nicolas. Or Nico, we'll call you Nico during this.

[00:02:04] **Nicolas Renaud:** Nick also works here. Yeah, thank you. Thank you for inviting me. Really happy to be here.

[00:02:09] **Abby Cabunoc Mayes:** Of course, how's it going in Amsterdam?

[00:02:11] **Nicolas Renaud:** Snowy, to tell you the truth. We have snow for the last week and it's not something we're used to, so it's a bit chaos everywhere. But it's very nice. It also means that it's sunny, which, you know. It's not a usual thing in the Netherlands, so pretty happy.

[00:02:23] **Abby Cabunoc Mayes:** That's good. It's snowy here, but not sunny here in Toronto.

[00:02:26] **Nicolas Renaud:** That's a bad mix. 

[00:02:27] **Arfon Smith:** It is cold. I can report it's cold in Edinburgh and not snowy and my kids are furious because about 40 miles away it is snowy and they would like that snow here, so there we go.

[00:02:37] **Abby Cabunoc Mayes:** Ah, too

[00:02:37] **Arfon Smith:** wintertime in the Northern Hemisphere

[00:02:38] **Abby Cabunoc Mayes:** but yeah, let's jump right in. Nico, do you want to tell us a bit about your background? And then maybe also QMCTorch?

[00:02:45] **Nicolas Renaud:** Yeah, of course so I come initially from a very academic world, right, so PhD, postdoc and all the rest in quantum chemistry slash material science, so that's really my background initially. But for four or five years now I'm working at a place called the Netherlands eScience Center, it's a publicly funded research center in the Netherlands.

Who focuses on research software, so developing research software together with partners and also using this research software to actually do some research with them and publish some results. And at the center, we don't necessarily focus in a given discipline, we work across all disciplines. So in the past couple of years, I've worked in biochemistry, in astronomy, in ecology, so a lot of different topics, but always with the focus on developing the tool that researcher needs to do their research.

We're pretty broad in that sense, and we're also pretty broad in terms of technology. So we use a lot of different toolings and we try to make the best choice each time. 

So the QMCTorch project came from a project in material science. So with collaborators here in the Netherlands at a university called Twente University in the east of the Netherlands, and with someone called Claudia Filippi, who is really one of the experts in quantum Monte Carlo simulation. And together with her, we started by refactoring to really improve the code that she has. It's called CHAMP. It's a code that has been in the community for a long time that has been used by many people to publish many results.

But at the same time, we decided to develop something new, right? And that's how QMCTorch came about. And the idea there was that while doing the project with Claudia, we kind of figured out that Quantum Monte Carlo at large could be somehow recasted as a machine learning problem. And so we decided to have a machine learning approach to the Quantum Monte Carlo problem.

And little by little, we built a couple of tools, and the last one was QMCTorch that we published a couple of months ago. So yeah, that's the genesis of the tools, in a nutshell. 

[00:04:29] **Arfon Smith:** It's really cool. I'm actually quite familiar with some of the work of the center you're at. There's lots of great software engineering going on and research software engineering.

I was curious if you could just backtrack just slightly and explain for the audience -- I would say this is software that helps understand chemical or system or material, I think you said material science for the particular application here. What's happening here? Is this quantum chemistry software? Is this computational chemistry? What's the broad umbrella that we're working with in here? And why do researchers use these methods?

[00:05:00] **Nicolas Renaud:** Yeah, so the broad umbrella would be quantum chemistry, so really looking at molecular systems or individual molecules, but through a quantum physics lens. So trying to describe this molecule at the highest degree of accuracy you can think of. And applications are quite broad, right?

So the projects that we were working on there, the application target was really developing new material for photovoltaics. So if you have molecules in photovoltaic cells, they're going to absorb lights and you want to know which lights, the frequency they're going to absorb, what's going to happen after this, how they're going to transform this light into electricity.

And of course, by tweaking the molecular structure, you can sort of tweak the overall performance of your solar cell, right? If I take a broader picture, that's really for that project that we're trying to work on. But there are many other applications, might it be for to design better material because of their strengths or better drugs, because they're going to bind to different proteins, right? So the target application are quite broad.

Quantum Monte Carlo itself is a very accurate method, right? It means that it's also quite expensive and it also means that you can only apply it to very small molecules usually, right? So that's what you see mostly in quantum Monte Carlo simulation, that you're gonna, you know, play with molecules that have a few atoms, right?

A dozen atoms. So very small molecule and really try to compute the property of this molecule as well as you can. Researchers are interested in quantum Monte Carlo approach because you can parallelize that very efficiently in a way, right? So you can really make use of very large infrastructure to compute your molecular properties.

So that's really one of the unique criteria for Quantum Monte Carlo, but it's still a very expensive method, right? It's a sub community of the quantum chemistry community that is really interested in it. Compared to more popular methods that people use on a daily basis. 

[00:06:36] **Arfon Smith:** So very high level, using a computer to simulate molecules rather than other ways. If I had a jug full of a molecule or some kind of liquid, I could do a physical experiment on it in the physical world, or I can simulate it, right?

So I think I understand the answer to this, but I'm just going to ask you just to verify, but these are computationally expensive because you're trying to keep track of every single, electron and proton. You're tracking the interaction, the quantum state of the system continually, right?

[00:07:04] **Nicolas Renaud:** Yeah, you're really trying to track all the interaction between all the electrons in your molecule, right? And you can have quite a lot of them if you have heavy atoms. How they interact together, but also how they interact with the nuclei of your molecule. And you do that at the quantum level.

So you're really trying to define what we call a wave function. So it is very complicated math objects that define where the electrons are, what level of energy they have. But it's something that becomes very expensive computationally very quickly, right? So that's why you need quite a large computational resource to run this calculation.

And of course, the goal is to do that on one side. So do all this computational work on one side and then go to your colleague who are in the lab and say, hey, I think that this molecule can do this. What do you think? And try to see if the two matches, right? And most of the time they don't, so we have to be honest, right?

Because, it's very hard to compute this accurately. And there are a series of different methods that allows you to reach this level of accuracy that you're after. And quantum Monte Carlo , if you do it well, if you define this sort of wave function in a proper way, and if you optimize it in a proper way as well, can really lead to very accurate results. But it comes at a price and the price is really a very high computational workload that you have.

[00:08:12] **Arfon Smith:** So, could you say a bit more about that? So it sounds like this is running on a cluster of machines. I don't run this software on my laptop, right? Or for a big molecule. 

[00:08:20] **Nicolas Renaud:** For big molecules, no. So if we look a little bit more on the software side of things, when you develop things, it's impossible to do the development and have your tests that run on a cluster somewhere. So there you have to break it down to something that is more manageable at a local level.

So if you take an H2 molecule, so a molecule with two hydrogen atoms, that you can do on your laptop and you can use this kind of system to actually do your development. But from a scientific point of view, that's maybe not super interesting, right? So if you want to go to a much larger molecule, then you need to take your software, put that on your favorite supercomputer that you have at your disposal, and then run your simulation there.

If you look at a very large molecule, you're going to take a couple of nodes of these supercomputers, or let's say, I don't know, 200 CPUs, right? And you're going to use them full time for a couple of days, maybe, right? So that's really the scale of the simulation we're talking we're talking about.

And quantum chemistry at large is very demanding in terms of computation. 

[00:09:11] **Arfon Smith:** So you always want HPC. You always want more compute. You can always use it. If you've got it, you can take it. Sounds like it.

[00:09:18] **Nicolas Renaud:** We work very closely with the Dutch National Super Computing Center, which actually just next door from us. So we do make use of the infrastructure quite intensively. But yeah, without this, you cannot do this kind of work. That's for sure.

[00:09:30] **Abby Cabunoc Mayes:** Cool, that makes sense. Going back a little bit, you mentioned the solar cells, and I saw that this was developed as part of the A Light in the Dark project. Can you tell me a bit about the outputs or what insights came out of using the software in that experiment?

Yeah.

[00:09:45] **Nicolas Renaud:** yeah, a very good question. The, so the code was really aiming at this application right? We had a couple of roadblocks, one of them being COVID and we, you know, we all suffered into this, so the project really ran mostly during COVID. And the project was really much more geared towards the software side of things, right, and the methodology development than the application, in a way, right?

So we did a lot of software, as I said, so the software is now on GitHub, is now openly accessible for everyone, and it's been used by a lot of people. And also out of this software, we managed to create a broader consortium that really aims at pushing quantum Monte Carlo methodology within the the material science community.

So that was one of the main outputs in terms of scientific outputs. It may be something to edit somewhere, but we didn't have that much, unfortunately, for that project. And partially it's because we looked so much on the method, right, and the PhD students working together with us did quite a lot of work on how to really optimize this, you know, electronic structure problem the best way possible.

So really on the mathematic foundation of this and its application, much more than towards the the application, right? So I kind of, I cannot tell you we found a very brand new molecule that is much better than all the other molecules, because in the end, we really focused on the software side of things.

[00:10:54] **Abby Cabunoc Mayes:** Well, it's great that QMCTorch still came out of that, and you still have things that are useful for the scientific community. So another question I had was why PyTorch? Why are you building this on top of PyTorch?

[00:11:05] **Nicolas Renaud:** So when I started that, that was a bit my first try at machine learning. At large, that was really the first time I was putting my hand into it. PyTorch at the time, and probably still now, was still, you know, very popular library with a very large ecosystem, with very good documentation. That's maybe why I decided to go to PyTorch.

That was actually the fastest one for me to learn compared to other workflows. It could have been done in other workflows, right? At the end of the day, you know, I just need something that gives me automatic differentiation and I can probably do the same. But I think thing that PyTorch did better than anyone else, at least at the time, was documentation and tutorials.

That was really something that was really strong at the time for PyTorch. That allowed me to really quickly get into it and integrate all these ideas together.

[00:11:46] **Abby Cabunoc Mayes:** Yeah, no, that makes sense. PyTorch was also my first foray back into machine learning when I was like, I want to play with this a little bit, and yeah, it's a good tool.

[00:11:54] **Arfon Smith:** So I was going to ask I've had a little bit of familiarity, but imagine 20 year old state of knowledge of some of the packages that people might use in computational chemistry. And I'm pretty sure I'm right in saying a lot of the big old school ones, like I'm thinking like Gaussian and Q-Chem and all these things, like most of them are closed source.

I think most of them are not open source packages. I was wondering if you could say a bit more about the state of open source software in computational chemistry today. Has that changed much since my knowledge of how the world was back in the mid 2000s? But also, why did you decide to release this as an open source package?

[00:12:29] **Nicolas Renaud:** So it's changing, I think. I have the feeling, at least, that it's changing. But you're right in saying that most of this very well known package are closed source. And most of them comes behind the license, right? Which is also, you know, a different business model that works well.

And the open source movement is not that strong in this community. I'm not fully sure why, I have to admit, because if we compare the work in other communities , where everything is open by default, right? So, yeah, computational chemistry at large and quantum chemistry in particular is a bit on a different approach there.

So it's still very much a little bit like this. You have more and more packages that comes open source and adhere to the open source model, right? But the big names are still very much what they were 20 years ago. I can confirm that . 

And the code we started with, so the code of Claudia, right? So CHAMP, it's called, but it was the same thing. It was closed source. But slowly by also advocating for the open source movement, what we managed to put that in the open source domain, right? But it's a change of approaching the code, right?

It's really a change of making the code available for everyone that wants to use it. And with this, of course, you need to also make sure that your code looks well, right? And that it's, you know, people look at it and say, okay, I understand how that works. So you also need documentation. So we also made a lot of effort there, right? To create documentation for our code. So that other people can also use it. And I think it's working well. I mean, it's always been a very good code, but now it's also open. 

And so why QMCTorch is open? Because that's what we do at the eScience Center. That's one of our funding principle, even, I would say, when we start the code from scratch, it's open. That's what it is. And this is because we are funded by the government. So it's only public money funding us, right? And therefore we have the feeling that all of that should be open. So when we start something from scratch, yeah, there is absolutely no question for us. This is how we work. And we do this on day one. 

There's also another thing that's, you know, some of our research partners, okay, I'm going to do all the work and at the very end of the project, I will open source the code, right? And okay, I understand. But we try to do that, you know, on day one, we start the project like this.

So that also forces you to write your code in a better way because it's public. Everybody can look at it and you don't want them to have a bad impression of your work. 

[00:14:24] **Arfon Smith:** I like to say to people that the best time to open source your code is at the moment you make the repo. It's just easier then. 

[00:14:29] **Nicolas Renaud:** don't 

have to think about it anymore.

[00:14:31] **Arfon Smith:** Nobody's looking, nobody's gonna laugh at you if you write bad code. I think that sort of fear of being watched is very real for some people.

[00:14:38] **Nicolas Renaud:** definitely.

[00:14:39] **Abby Cabunoc Mayes:** Yeah, no, big fan of working in the open. It is scary for sure

[00:14:42] **Nicolas Renaud:** Yeah. Yeah. 

[00:14:42] **Abby Cabunoc Mayes:** So did you start doing more open source when you came to the eScience Center? Or were you already doing open source before

[00:14:49] **Nicolas Renaud:** No, it's very much when I joined the eScience Center that I started doing this. I also admit that before I joined I was also a quantum chemist doing close source development. And it's really coming here that I was directly exposed to it. And you know, so we have a lot of training program both internally and externally that also help people learning how to do that best, right?

Once you have this sort of familiarity with it, it's also much easier to develop your code like that. But it was something I had to learn when I joined, that's for sure. Yeah,

[00:15:16] **Abby Cabunoc Mayes:** Yeah, that's awesome. Yeah, I think my first job, I the lab I was in, everything was published open source. Everything was released openly, and I'm so glad I did that. Otherwise, I wouldn't have seen how powerful it can be. 

[00:15:26] **Nicolas Renaud:** Yeah.

[00:15:27] **Abby Cabunoc Mayes:** I'm glad there are institutes like that.

[00:15:29] **Nicolas Renaud:** Indeed, yeah. And I have to say that it's also a good vision from the Dutch academic world who is really telling us to do this. So there is a strong vision for that to happen. And yeah, it's quite unique that there is, at least in Europe , such a big center, because we're about a hundred people working here now, who is really developing open source software for the research community, but it really comes from the top. It's really the Dutch government who say we should be doing this. So that's pretty unique, I think, in Europe.

[00:15:52] **Abby Cabunoc Mayes:** And I guess while we're on the topic of the eScience Center, I know in our emails when we're scheduling this, you talked about the research software directory and some other work that you're doing just to help promote research software as research output. Do you want to talk a bit about the other work that you're doing there?

[00:16:07] **Nicolas Renaud:** Yeah, of course. So the research software directory is something we've put together over the years, and I think we've had the first release couple of years ago, something like this, and it's really for people to be able to showcase their work as research software. So a place where they can highlight their research software, make sure that other people can find it and try to reuse it and try to understand what the code does.

So we started only with our organization and only our software there. Now we have about 50 ish organizations putting their software there as well putting also their projects. So we can link projects or research projects and research software to really put the software in its own context, right?

So we need for people who come from the outside to understand what the software does and what maybe they would like to use it. And overall, we're trying that for two things, A, to push for the development of open source software itself, right, to really invite people to do this, but also for research software to gain recognition in a way, right, so for the broader academic landscape to understand that it is a very real research output. 

Publishing a software is also something that is important for researchers, and that is not only papers and citations, but also the tool you're publishing and you're sharing with the community is equally important.

And slowly, we see change in this, right? In the recognition that research software has in the landscape. There's still a lot of work to do, but I think we're going in the right direction with this. And the Research Software Directory is one of the tools we're using to promote all of that. We also, with people from GitHub as well, we push for the citation file format quite a bit at some point, right?

So we're also helping that in the back. And that as well, it's another way of promoting research software as a main output and not as a byproduct of research.

[00:17:40] **Arfon Smith:** Yeah, you can Put a citation. cff file in your repo, or actually any citation file, and GitHub will detect those. That was a really nice collaboration with that group. This feels like a good segue to just ask briefly a little bit about, what was the primary motivation for publishing in JOSS?

Was there something you were particularly looking for as part of that review? Or was it more about, sharing the software with the world? Could you say a little bit about what was your thought process?

[00:18:05] **Nicolas Renaud:** It's something that we always encourage in all our projects when we develop software to consider a software publication, right? And JOSS is one of the prime journals that we recommend together with SoftwareX and a few others, of course. What I really like personally about JOSS Is that the review is on your code, right?

The paper is nice, the text, everybody gonna read it and maybe there's a nice picture, but the review is on your code, only on your code. And that is something that makes it very different from the other journals. And the interaction, especially for QMCTorch with the reviewer was actually really nice.

They pointed a very valid point, right? That any other review that is more on the paper would've completely overlooked,. So we really like that a lot, right? 'cause it's really doing the review of the software on the software. So yeah, we are big fans of JOSS.

[00:18:47] **Abby Cabunoc Mayes:** That's great. And it's really great that QMCTorch is open. So one thing I really love about open source is just the ability to build collaboratively with others and getting outside contributions.

Is QMCTorch open to outside contributions? If people want to contribute, how can they?

[00:19:02] **Nicolas Renaud:** It is very, and I will welcome any contribution, that's for sure. If they want to contribute, I think I set up a couple of templates in the issue, right, to either request features or report bugs. I had a couple of master's students who actually worked on it as well, right, doing the developments, and we developed it like this.

And, you know, it's still a very niche software, I have to be honest, right? It's for support of the quantum chemistry community. So a good understanding of the domain always helps, right? That's for sure. And willingness to use it, I think that's what I'm doing now. I really decided to publish the software first, right, and then to use the software to publish results.

So that's what I'm doing now. So if people want to collaborate and publish results with me, I will be very glad to do that together. But that's something I want to achieve this year, right, to really show now to a more domain oriented paper what the code can do, right, and how to use it, how to further develop it.

And one thing that is interesting, really, on the domain side of that. You know, if I go back to explain the quantum Monte Carlo problem, the thing that QMCTorch does that maybe other software are not really doing is allowing people to create quite easily, right, the way they want to describe their molecule.

So it's very complicated mathematical object, right? This wave function that we have, but in the way QMCTorch is built, we can really have like different modules that we can assemble. And people can define their little neural network that's going to compute a little part of the bigger wave function and experiment with it and see if it leads to better result or worse result.

And that's something I would like to see, right? To have a lot of library of this sort of sub module, right? To see how they perform. And once again, what's through PyTorch, right? We're doing really most of the heavy lifting. They really have to define a very simple function, very, you know, vanilla neural network.

And they can put that in QMCTorch and see what type of result you get. So that's really the plan that I have for this year. To experiment a little bit more with it and publish those results.

[00:20:51] **Arfon Smith:** That sounds like lots of work to do, lots of opportunities to exploit the software for great new science. Thanks for giving us that overview. I guess this maybe is a good place to wrap up. I just wanted to say, you know, how do people keep track of your work and what you're up to?

Is there a place online people can follow what you do? What's the best way to Keep up with the work that Nico is doing and you know, the development of QMCTorch.

[00:21:16] **Nicolas Renaud:** I'm not a big social media person, I think the best place to see what I'm doing is really GitHub. That's where I'm the most active. Right. It's not because you're here that I'm saying this. I think it's true. No, and all the development we do on all the project there.

Right. It's also something we do internally to see what people are doing at the center. Right. So we try to keep an overview of all of this. And that's really the main place where we publish everything we do in the end. Or the the Research Software Directory is another good place I should mention.

[00:21:38] **Arfon Smith:** Fantastic. Well, I think that's a wrap. Thanks again for your time today, Nico. It's been really interesting to talk to you.

[00:21:43] **Nicolas Renaud:** Oh, thank you for inviting me. Really happy to be here. It was really nice. 

[00:21:47] **Abby Cabunoc Mayes:** Thank you so much for listening to Open Source for Researchers. I loved that conversation with Nico. We showcase open-source software built by and for researchers. So please subscribe in your favorite podcast app. Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes. Edited by Abby and the music is CC-BY Boxcat Games. 


[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/P4fOMcQyadg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>