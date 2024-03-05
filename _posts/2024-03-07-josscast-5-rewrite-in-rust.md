---
layout: post
date: 2024-03-07 00:00
title:  "JOSSCast #5: Rewrite in Rust – Gui Castelão and Luiz Irber on Gibbs SeaWater Oceanographic Toolbox in Rust"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Rewrite-in-Rust--Gui-Castelo-and-Luiz-Irber-on-Gibbs-SeaWater-Oceanographic-Toolbox-in-Rust-e2glcu9" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)

Gui Castelão and Luiz Irber join Arfon and Abby to discuss their work implementing the Gibbs Sea Water Oceanographic Toolbox of TEOS-10 in Rust, and the role of instrument builders in science.

Gui is an oceanographer at the Scripps Institution of Oceanography, previously part of the Instrument Developing Group. Luiz is a Computer Science PhD at UC Davis and an avid Rustacean.

Gui’s website: [www.castelao.net](https://www.castelao.net/).Luiz’s website: [LuizIrber.org](https://luizirber.org/)

### Episode Highlights:

- [00:01:55] - Introductions to Gui and Luiz and how they got into open source
- [00:09:18] - GSW-rs – a Rust implementation of the Gibbs SeaWater Oceanographic Toolbox
- [00:17:13] - Why Rust?
- [00:19:53] - Instrumentation culture in oceanography (and astronomy!)
- [00:23:17] - Recognition and credit for software contributions in academia
- [00:27:47] - Publishing in JOSS
- [00:31:36] - Contributing to GSW-rs

Links Mentioned:

- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05988](https://joss.theoj.org/papers/10.21105/joss.05988)
- GSW-rs repository: [https://github.com/castelao/GSW-rs ](https://github.com/castelao/GSW-rs)
- Inception repository: [https://github.com/castelao/inception](https://github.com/castelao/inception) 
- Gui Castelao's website: [www.castelao.net](https://www.castelao.net/)
- Luiz Irber's website: [LuizIrber.org](https://luizirber.org/)
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))


### Transcript


[00:00:05] **Arfon Smith:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by researchers for researchers. My name is Arfon. 

[00:00:12] **Abby Cabunoc Mayes:** And I'm Abby

[00:00:13] **Arfon Smith:** And we're your hosts. Every other week we interview an author, or authors today, published in the Journal of Open Source Software. Also known as JOSS. 

[00:00:21] **Abby Cabunoc Mayes:** yeah, This is episode 5. We spoke with Gui and Luiz, and you'll hear a longer intro about the two of them. But I thought this was a very fun conversation.

[expand]

[00:00:28] **Arfon Smith:** It was fun. I think we've learned as budding podcasters that if you invite two people, you seem to talk even more. So it's a longer one, but it was fun. We covered a lot of ground. 

I think one of the things that I learned and reflected on as I was listening, especially to Gui talk, but also Luiz, was there's this work that gets done, the instrumentation work, the low level software that's used to operate these incredibly important instruments.

Oceanography is a pretty impactful research area, especially, in these times climate change and all the things, the reasons we need to care about the ocean. This was a really interesting conversation to have and learn about the hardware and the software and how that work is divided up their research areas.

And also just get to hear people who are excited about Rust. Which is kind of fun to listen to people who are passionate about programming languages. What about you?

[00:01:15] **Abby Cabunoc Mayes:** It was really interesting to hear their story going through this Rust implementation of an existing library. They're such strong Rust advocates. They were ready to go through it. It was fun also just to hear their journeys through open source and implementing this. And I learned a bit about oceanography. Yeah, let's play the interview!

[00:01:31] **Arfon Smith:** Yeah, let's go for it.

Today we're chatting with Gui Castelao and Luiz Irber about their paper, Gibbs SeaWater Oceanographic Toolbox of TEOS10 Implemented, I think Importantly, in Rust, although the Importantly bit isn't in the title, but I inserted that just for my own satisfaction. 

Gui Luiz, why don't you introduce yourself and tell us a little bit about your home institution and whereabouts you're based?

[00:01:54] **Gui Castelao:** I'm Guilherme Castelao, just Gui. I'm an oceanographer, currently at the Scripps Institution of Oceanography. And before I was in the Instrument Developing Group, which is related with when this project started . And now I'm working more with machine learning and climate. 

[00:02:12] **Abby Cabunoc Mayes:** Nice and Luiz?

[00:02:13] **Luiz Irber:** Yeah, so hello everyone I'm Luiz I I'm a computer science PhD at UC Davis. I work with bioinformatics mostly I Been doing Python for 20 years, doing Rust since 2017, and for my PhD research, I just love going into public genomic databases and downloading petabytes of data and making them searchable and useful.

I met Gui when we both worked in Brazil at the Brazilian Climate Research Institute. So I have a history of a bit of climate models , so that's my connection with oceanography. Nowadays, it's kind of fruggy.

[00:02:54] **Abby Cabunoc Mayes:** Oh, that's great.

[00:02:55] **Gui Castelao:** Well, now that Luiz mentioned that, that's interesting. One of the first open source packages that I wrote was an old version of this package in Python. This back like 2002, 2003 was one of my first submissions to PyPI.

[00:03:12] **Abby Cabunoc Mayes:** Full circle! And I think that's a nice segue. I was gonna ask a fun icebreaker question. Tell us a little bit about your open source journey. So, Gui, it sounds like you have a bit of a background doing open source.

[00:03:22] **Gui Castelao:** Yes. So, that started with around 2002, 2003 mostly Python at that time learning how to do it. One thing that's interesting on this whole process is how the community changed, right? At that time was hard to do open source, like, people didn't know how to use it well. Sometimes people would write to me complaining, like, really pissed, Oh, there is an error on your open source that you're making free for us to use. Like it was a selling product, right? I'm like, wait a minute.

[00:03:53] **Abby Cabunoc Mayes:** that still happens. But, go 

[00:03:56] **Gui Castelao:** Oh, That is much better now. But, I think just the community wasn't prepared. They didn't understand how things work, right? They were less material for us as well. Like, for me building stuff, we had to kind of figure it out how to do open source by ourselves.

Now there's so much teaching, right? So much guidance on the importance of doing documentation or testing or how to handle the community code of conduct, how you should not behave. It was a big change. It's great. I think we have things that we can improve, but it was a great progress.

[00:04:30] **Abby Cabunoc Mayes:** Nice, and Luiz, how were you introduced to open source?

[00:04:32] **Luiz Irber:** So in Brazil there was this kind of big festival which was called FISL, F I S L. It's the international festival of free software. And it happened on the capital of my state in Brazil, Rio Grande do Sul. So, since I was in high school, like in 2000, I would go with some friends to this festival in the capital and was like 5, 000 people, the largest ones, and just go around. There were booths for the community, like for Linux installations.

And so it was a place that I learned a lot. And then I started tinkering at home with installing Linux in MySphinx and so on. Then in 2005 it was my first time releasing open source software. I started working at another research institute in Brazil that was doing research for agricultural purposes.

I got into it as a research intern, and was kind of rewriting a package that was in Windows, and they promised on the funding that it would work on Linux, but no one had worked on that. And it was a C++ codebase, and I was like, how do I port this thing over to run on Linux? So, that's when I started using Python and a lot of GStreamer to handle the video components of the system.

I learned Python a bit before, but that was the point where I started really going deep into Python. And then in 2007, I think was the first time I attended the Brazilian PyCon. And that was like, just amazing. Like the Brazilian Python community is so nice. And I just learned so much from the community interactions, but also how to develop software. And because of that, I ended up doing my PhD was because of this Python community connection also. I found Titus not because he was a professor, I found him because he was doing a lot of testing in Python.

[00:06:33] **Arfon Smith:** That's super cool. And this is Titus Brown, of course, who's does a lot of open source work himself. I have a side question. I was going to ask you something different, but I'm going to have to ask you, Luiz, because I think your number's going to be higher than mine. How many distinct versions of Linux have you installed in your life?

Like, different flavors of Linux? Because you're describing a period where I feel like I was reinstalling my machine every two weeks with a different distro. I was trying them all out. I'm just curious if you had to, pick a number, how high is that number?

[00:07:00] **Luiz Irber:** I would probably say 15. The first time I nuked the Windows system in my computer and lost all my family data, was with a Brazilian distribution called Conectiva, which was derived from Red Hat. So, 

[00:07:15] **Arfon Smith:** What about yourself, Gui? Do you have a number? Top of mind?

[00:07:18] **Gui Castelao:** little bit less than that, maybe like 10, because I would install and reinstall and reinstall. Okay, now I figured it out, and then next week I just install the same one again. But my first, I think my first distro was Slackware, so it was quite intensive, quite a lot of time.

[00:07:35] **Arfon Smith:** What about you, Abby? Have you, have you got scar tissue from those experiences?

[00:07:39] **Abby Cabunoc Mayes:** Yeah, I had that period in my life. I think I'm only at two, though. I don't think I explored too, too far. I really liked Ubuntu, yeah.

[00:07:46] **Arfon Smith:** yeah, I remember mine's probably under 10, but I do remember being very proud of an install that I've done. Maybe like you, Gui, where you like install it and then you're like, Ooh, no, next time it'll be perfect, so you like start again. And then, I went and talked to some of my computational chemistry friends, and they're like, Well, if you really want to do it properly, you've got to install Gentoo.

And I was like, Oh my god, what is this? And you like compile your own kernel to start with. I was like, This is insane! And I remember spending like four days compiling. Like KDE or something, like whatever. And then I, but I'd set the flags wrong and it just didn't work. I had to go back to the start.

Anyway, that was during my PhD. So, you know, it turns out I had some spare time during my PhD. Anyway, that was a side note.

[00:08:31] **Gui Castelao:** I love Gentoo. Was the end of my PhD was, was everything that I used. Like, you feel like you're taking all the juice from the machine. And

[00:08:39] **Arfon Smith:** exactly,

[00:08:40] **Gui Castelao:** it's a mess, it's a mess to install the first time, but then to keep up, as long as you don't accumulate too much, just compiling the background. I didn't feel that much. 

[00:08:49] **Arfon Smith:** Yeah, that's cool. That's awesome. Okay, right, well I will bring us back to topic. Sorry for distracting everyone talking about their favourite Linux flavour from 20 years ago or whatever. But that was actually really fun to hear that. So, I wonder if we could just start, going back to this paper, this submission and this software, if you could start by telling us about TEOS-10.

Can you say a bit more about the sort of origin story of this software and why you started the project? 

[00:09:14] **Gui Castelao:** Let me talk about a little bit of GSW and then we move to how we start. So, the GSW is the idea behind, actually, is. We measure a bunch of things in the ocean, right, and there are some properties, for instance, one example density in the ocean is really important to be able to explain and understand why water is going one direction or the other, right? But it's quite difficult to measure directly in the ocean, so it's way more efficient to measure all the properties and guess what is the best. Usually, all the instruments that we use measure pressure, conductivity, and temperature, and with that we can guess pretty well what is the density. I guess this is the most common application on oceanography with GSW and what GSW provides which is important to make clear what we did was the software part for the Rust.

But there is a whole scientific C unit behind that actually proposed the relations. Right? This is very important and this is distinct. We build a software, but we have no credit for the science built behind that proposed those equations and those parameters. But what this great large community did was proposing relations.

If I have these three measurements conductivity, pressure, and temperature, what is the best guess for density for that place? And our electronics measured the three things. So that said, GSW It's a collection of those relations, and one big thing from the old version, the EOS-80, is that it was proposed in such a way that it's consistent.

Before the regressions were done like independently, so they could have inconsistencies, especially on deeper ocean. So the new one is a fully consistent formulation based on Gibbs. Yeah, I think I'll stop here. It's way more than that, but I think it's enough to give a picture.

How we start is a little bit different, I'll let Luiz tell this.

[00:11:03] **Abby Cabunoc Mayes:** Well, before we move on, GSW that's Gibbs SeaWater

[00:11:07] **Gui Castelao:** Yes, yes, yes.

[00:11:08] **Abby Cabunoc Mayes:** I did have a question around how you're getting these measurements. Is there a ship with sensors out there? 

[00:11:12] **Gui Castelao:** Good question. In the old times, oceanography was initially done with bottles. We just measure first at the surface, and there are special bottles that you could dive them and they will close. In a certain depth, and then you bring these bottles back, so we would sample water from 100 meters, 500 meters, 800 meters, so you could measure, oh, this is the salinity down there.

There are special thermometers that once they flip, they would lock, so you leave it stabilized there. They flip, they lock, and bring it back. Oh, this was the temperature down there. But this is very inefficient, right? Hours and hours to make a few measures.

Nowadays, we work with electronics. And the principle of the electronics that work in big ships, what are called rosettes, and these are like package of instruments, like, it's huge, it's huge full of instruments that you lower in the ocean with a big ship, or the instruments that I usually use to work with small robots that will dive by themselves.

The principle is the same, and the common measurements are, as I said, pressure, temperature, and conductivity. They record that, bring it back, and then how we guess. There is just the connection, so we have the electronics. The electronics is still there are errors on that, so we still measure with bottles nowadays that you can bring to the lab and measure with very high precision and calibrate the electronics.

And one of the ideas of this library on the start was to be able to bring more autonomous decision making for the sensors or the robots. So if you wanted to do like, to bring machine learning decision to the firmware of these robots, we need to have a more flexible language, right? Like, like Rust would attain.

Robust, need to be robust, because you just drop these robots, maybe they spend months and months by themselves, so we don't want bugs on that, like, segmentation fault in the middle So, if you want to bring more decision making on these, we need to build a firmware with a language that had more resource, and then these instruments, they need to make sense of the sensors.

For instance, what is the density, what is the pressure, where I am, you know, do I want to go up or down, and this would be the idea of, can we create a resource to produce a firmware for those instruments or sensors to make more autonomous decisions?

[00:13:32] **Luiz Irber:** Yeah, so I think the origin story on this is is a bit on like how I found out about Rust. During my PhD still to this day I work on a piece of software called sourmash that is the thing that allows me to do these comparisons on public genomic databases. But a big component on that is that I want to be able to run part of the software in the browser.

And sourmash used to be a Python and C++ code base. And in 2017, the best option was to use Emscripten to bring sourmash to the browser, or to rewrite everything in JavaScript. I tried in JavaScript, didn't work out because of like how we are dealing with integers. Then I was, okay, if I do Emscripten, I really complicate the build system for sourmash.

And then I was like, oh, there's this other language called Rust that's kind of like C++ but has packaging, has like integrated testing in the tooling documentation and so on. So I was like, I'll try it out. And I I've been doing Rust since, I really like the language and then I started evangelizing the language around, because that's what you do when you learn Rust apparently. I talked with Gui and then Gui started doing his things in, 

[00:14:51] **Arfon Smith:** is that Rust swag that you've got there, Gui? 

[00:14:54] **Gui Castelao:** That's a crab.

[00:14:55] **Abby Cabunoc Mayes:** yeah. The Rustacians, yeah. For anyone not watching the video, , , and Luiz both holding up their Rust swag. I do have a very soft spot for Rust. 

[00:15:05] **Luiz Irber:** Yeah. So then what happened is that in September of 2020, we started doing weekly Rust meetings to talk about Rust and like figuring out things together. Or like if we found something interesting, like we would show to each other. And then we started working on small projects to work with the language other than the work that we were doing in our jobs.

[00:15:32] **Arfon Smith:** It does seem like Rust gathers strong advocates, right? It feels like there's a lot of Julia advocates out there as well, right? People who adopt new languages. Well, I guess new languages only survive and grow if people get excited by them, right? 

[00:15:46] **Gui Castelao:** Exactly.

[00:15:46] **Arfon Smith:** Full disclosure, I've not written a single line of Rust ever, so maybe I should fix that now. It seems like I'm the odd one out on this podcast.

[00:15:53] **Gui Castelao:** One comment about the story that we start. So I'm an oceanographer, right? Full of oceanography, like undergrad, masters, PhD, everything. And, always enjoying coding but there are a lot of holes in my education on computer science. On the other side, Luiz is a full computer scientist, was cool like at the time of the when we were working with the climate model.

He was recently graduated, but he was teaching us a lot of things, and these meetings was a huge impact, like I imagine how much the scientific community could benefit of this, which was essentially pair coding, right? But it goes all the way from, oh, how do you set up your VI? How do you manage this?

How do you do that? And it turned me so much more efficient. These meetings were way more than Rust and update the week than what was happening, other things, but there was a lot of learning. And I think that the scientific community could improve a lot if people practice more of that.

[00:16:47] **Arfon Smith:** You're preaching to the converted here, but I love to hear it said, so I'm with you, I'm with you. Yeah, thanks for noting that. Okay, so I wanted to just pivot a little bit to audience here. So, you know, writing software, it sounds like, solving a problem that you faced yourself you know, you understand the problem well, but who's your sort of target audience?

Is it people like yourself, Gui? How broad is the user base here for this software?

[00:17:13] **Gui Castelao:** That's a very interesting question, so this library in Rust is not directly impacting like the community of Python users. It might one day they flip, instead of based on the C, now flip to be based on our Rust one, but I don't think this is for the general scientific community.

It can be behind the scenes, right? Like as crunchy number, efficient and robust crunchy number. But the way, how I see this more like, few more developers for sensors or high performance computing, anything. So that's what Rust brings is special, right? Is the efficiency, which means faster, but also demand less resource.

So if you're doing a firmware for a small sensor or a small robot that's very helpful if you're trying to crunch numbers and fast computer and trying to do that faster. That's the place. But most of the community nowadays I think uses Python. And I don't think we are replacing Python. I don't think we should.

[00:18:08] **Arfon Smith:** Yeah.

[00:18:08] **Gui Castelao:** So I think a small niche, but a very important one. And maybe a strong one behind the scenes. We still have a wrapper in Python like we do on the repository. But, yeah, not directly for the large community. What do you think, Luiz?

[00:18:24] **Luiz Irber:** Well, on the question on the target audience, I mostly work with bioinformatics, so like, I'm not the target audience for this library. So people that are working with oceans or this sort of measurements is the target audience. But as Gui said, there is a big spread also on that, on like, which niches are you covering?

Like, are you doing data analysis or do you want to deploy this, like, on firmware to run something? 

[00:18:49] **Arfon Smith:** Yeah, different software for different situations. Hearing you talk about this sort of picking the right tools for the right problem is actually reminding me a little bit of how astronomy works, where you have like very strong culture of instrument builders, people who are building the thing that will attach to the camera that will then go measure some fundamental constant about the universe. And there's all the software that gets built for that and in the most extreme settings, those instruments go into space, maybe like deep ocean work I would imagine in oceanography, you know, they're remote, the instruments.

And then there's also this sort of separation of, well, that's not the right tools for the people who are going to want to use that data and do their analysis. And so then it might be much more like scientific Python stack, notebooks, maybe popular machine learning libraries, that kind of thing. 

I have a question in there actually, which is: Does oceanography have a strong instrumentation culture? Like, are there people who just build instruments and think about that? Is that a career path that people follow in oceanography? Or do people usually do multiple different things?

[00:19:53] **Gui Castelao:** Yes, I think there is. When we started this library I was working the instrument development group of Scripps, it's 

like 

[00:20:01] **Arfon Smith:** There you go. There's the answer.

[00:20:03] **Gui Castelao:** just dedicated for that, and some of the standard instruments used today, they started there. there is this path. I agree with you. I agree with everything that you said.

And they are quite different. I think it's quite difficult to do both. There are few people, few geniuses that can walk both ways. But I don't think normal people like me should aspire that. And I also think one of the issues on that is the way the scientific community recognize this.

Right. And, and by the way, I think that's important job that JOSS is doing. If you dedicate too much time developing software, improving software like me, I was oceanographer and going towards the software development. If you invest too much time in these to do a good job, of course you're going to publish less if you're a normal person.

But the scientific community has trouble to recognize that. We still have. We are improving. We still have some ways, but we are much better already. And I think the contribution of JOSS is critical about that. So there is a way for you to produce a software that's reproducible that it people can understand how to do it that's tested and you can have a DOI and recognition.

Look I wasn't fully around. I was working, I was doing something. Maybe PhD didn't come with all these papers. But look, all the things that I built that people are using, sorry, I think I went a little bit off your question 

[00:21:23] **Arfon Smith:** But I think you're touching on some important topics. In astronomy, speaking from my experience watching colleagues, the challenges that software engineers face in academia is quite similar to the instrument builders, which is they're doing work that can result in papers, but it's often not immediate, and it's different kind of work.

Like if you build an instrument that a thousand people use over the next ten years. Over the next ten years they're probably going to cite you every time. So, oh, the long lead is great. You get tons of citations eventually. But, if you spend eight years working out how to build that instrument, you might publish like one or two conference papers in that very long period.

And so you don't look like a normal researcher because you're making something. And I'm always struck by that sort of similarity between software and hardware. And people especially I think face some of the same problems because we built universities around this idea that you're going to publish research all the time.

And that's the only way that we can judge somebody's output. So

it's interesting hearing you talk about it. Mm

[00:22:29] **Gui Castelao:** is it could be better the recognition of the leading developer, but it's hard to hide that kind of achievement, right? The part that I'm most concerned is that those things, they are not built by one person.

There is like a community doing little contributions, right? And these little contributions are the ones that I think disappear. I think we should have a better way to recognize that and give a chance. The point is not the ego side, right? We leave that aside, but what I mean by recognize is give the resource for that person to keep going. Maybe during the PhD we spent one year developing this thing that was an important component of a bigger thing.

We should put some money for this person. Let's go for another year, produce something else. You're doing great. Keep moving on. That's when I mean by recognition. I don't know if Luiz want to add something about this.

[00:23:17] **Luiz Irber:** Yeah, I will say that we tried with not sourmash, but another software in the lab to hack this publication system and be like every person that submits a pull request is an author in the paper. And that also led to so much discussion being like, Oh, but this person just fix a typo. And it's still software centric in a sense, because there's a lot of people that are also scientists that are not going to program something, but they come with use cases we discuss a lot on how to implement things and they don't have a pull request to go as an author. Software credit is complicated.

[00:23:54] **Arfon Smith:** I agree. You used the exact word. My favorite word in life these days is it's complicated. And I think this is a good example of that.

[00:24:02] **Abby Cabunoc Mayes:** Yeah, and I'm editing an episode we recorded but hasn't been released yet, where we do talk about how documentation is often, more important than the software itself for the humans using it. So that contributions to documentation is also really important.

[00:24:16] **Gui Castelao:** I think the DOIs, like the DOIs are not perfect at all, but I think they address part of this with the Creators category and Contributors, right, so you still can add people that give some contribution but not on the level to be a Creator an alter write and you can move things. I think I like that solution.

Which by the way I have a repo called inception which explaining how to use the dot Zenodo. So how you can automate release if you link with Zenodo. 

[00:24:44] **Arfon Smith:** Oh, nice. It'd be cool to get a link to that project. If you have some examples, we can put it in the notes.

[00:24:48] **Abby Cabunoc Mayes:** So I know we've talked a bit about Rust, and you're huge fans of Rust, but can you tell me a bit about the advantages of using Rust in this rewrite, and like, why you chose that?

[00:24:57] **Luiz Irber:** So I'll go answering that, I think the main benefit of this is that when we started working on implementing this library, we wanted to have something that was maintainable over time, but also as close as possible to the equations that are in the scientific paper. Because those equations are complicated and have a lot of parameters.

So, going with Rust has this benefit that it's a low level language performance wise, so we could do a lot of parameters in the compiler usually does a very good work of optimizing all that OA, across function calls and so on. But also because it's a low level language in that sense, it's a kind of a drop in replacement to a C library, for example.

So we can avoid this practice of rewriting everything in Rust, or like, making all the other projects that use GSW-C have to fix a lot of stuff to be able to support this and we could benefit like the other implementations of GSW that are usually based in the C version to benefit from our work. 

And a comment on GSW. GSW, the reference implementation, is in MATLAB. And there is a version written in C that's used by other languages like Python and R and Julia to have all these features available. So, what we were aiming for is to not replace just GSW-C, but be an alternative focus on keeping compatibility with the other libraries, but also increasing the correctness of the code and how we test, how we document, how we do everything.

And Rust was a good fit for that. 

[00:26:43] **Arfon Smith:** I love it.

[00:26:43] **Gui Castelao:** just, just reinforce, agree with everything, for me, two things that really raise here is that first is the low level. Because the interest of going to firmware, right? So the same code that go run on my laptop and on HPC, I can use to structure a firmware. And the second as Luiz said, is the zero cost abstraction that we can write the functions as close to the papers as they are.

So it's very easy to compare, to check, to validate without compromising the performance because the compiler will then organize the whole thing for efficiency. There are a lot of advancements, but these are the two ones that most attracted me for this.

[00:27:18] **Arfon Smith:** Awesome. Okay. So just a little bit of a pivot to talk about JOSS for a few. So I think your paper was one of the first of 2024 to be published. So congratulations for well, I guess maybe you would rather it was published as one of the last ones in 2023. I have no idea. I was curious if you could just say a bit more about why you published in JOSS?

You touched on this a little bit earlier, but what the motivations were for that and how was the review experience? Anything particularly of note that for both of you during the review?

[00:27:47] **Gui Castelao:** So it's not my first paper at JOSS, I think Luiz's as well, right? We reviewed papers there as well before, we really appreciate JOSS.

There are several reasons to publish with JOSS. And one of them is well, I'm having trouble to which one to say first. One of them, I think, is the culture, right? It's different than a typical review on scientific papers or proposals where people are just trying to find mistakes, find the trouble, find like, oh yeah, I found a flaw here. 

I always felt like, involved on JOSS. The culture is different. It's like, yes, let's publish this. What is the best that you can make? Let's sit together and like, oh yeah maybe if you improve this, it's strong, if you do that, it's strong, but always in a positive way, in the sense that we're going to do this. I don't know how long it'll take, but we're going to make it, and we're going to make it together. I think this is fantastic for everyone involved, but for the scientific community as well, right?

Another thing that's very important for me is the efficiency to be centric around developers, right? So instead of investing time on the document, let's invest time on the documentation of the software, which people, if the software is successful, this is what people are going to actually use and testing to be sure that it's doing what is expected and people understand.

So for us that are developing software, that's very efficient. I wouldn't say that's less work, but at least you feel that the work is all being put in the right place on things that will be useful for others. 

One final thing I mentioned before, I think it's great to create a space to recognize software developers, scientific software developers, right? So now you have a publication, have a DOI, and especially for the early career, they can show, look, This is what I did in the last years, and this is what I produced, and it's possible to track the scientific impact, right.

If you go on sourmash and look at all the publications that, that use behind, you can see like, oh yeah, we are thankful for Luiz to invest time on this, because look how all the science that came behind, and maybe the funding agents can recognize more and more these and support more.

[00:29:52] **Luiz Irber:** I will say when I started my PhD, when I got review requests together with other people in the lab, we had a checklist that was not as complete as JOSS, but every time I went to do a review of a paper, I would go check the repo and see is the code available? Can I install this? Can I run the software? 

And so when JOSS came around I might be a bit too excited to jump and start volunteering to do reviews. So like, during my PhD I did a lot of JOSS reviews. And that's also the reason why I'm wearing this sweater.

[00:30:26] **Arfon Smith:** noticed that. I suddenly saw the top of the logo. I was literally about to ask you.

[00:30:31] **Luiz Irber:** Heheheh

Heheheh 

[00:30:34] **Arfon Smith:** That's very nice. I promised I didn't send that to you.

[00:30:37] **Luiz Irber:** Well, eh, you 

[00:30:38] **Arfon Smith:** I probably did, because you've reviewed so much, right? Yeah, but a while ago. Yeah, that's very nice. Thank you for that.

[00:30:45] **Luiz Irber:** So it was always a focus for me. Science has to be reproducible, especially for the easier, with a lot of quotes, part of it, which is like, software is something that we can run. We can go and do a long term experiment, again, in the lab that will take 15 years to complete. But, software has a much lower bar to reproduce what is being written and published.

So, I really like JOSS because of that. And also, again, like everyone already mentioned, on raising the bar for the usability of software. Because I can't really use a paper as a dependency on whatever I'm building. I can use software to do more scientific research and figure more things out.

[00:31:28] **Abby Cabunoc Mayes:** That's great. And I'd love to hear from you, Luiz, also. What kind of skills do people need to contribute to this software? I see it's open for contributions.

[00:31:36] **Luiz Irber:** yes, it's open for contributions. I will say that probably reading equations and translating to Rust is the largest part. Because one thing we didn't mention is that GSW has a lot of functions that end up being derived from these equations. How many are the, like, it's more than a hundred for sure. 

[00:32:00] **Gui Castelao:** a hundred and a few, yeah, I counted that.

[00:32:02] **Luiz Irber:** And a big part of that is that there are some of the equations that are used more than others. So like we focus on the subset that the GSW-C was implementing. There are some that even GSW-C didn't implement based on the MATLAB reference implementation. So we still have some to finish implementing.

But I would say that we also structure each function that we are implementing in a way that the function, the documentation and the tests are close to each other. So if you're coming to contribute, you have a lot of examples on how to help and how to do that translation.

So pretty much like reading equations, translating that to Rust. It's a very C- like Rust. We are not doing too many fancy Rust things in the code base. And then, attention to detail and patience, because these equations can be quite long sometimes.

[00:32:58] **Gui Castelao:** Yeah, I'd say a lot of attention and patience. The priority is to do the correct thing. 

[00:33:04] **Luiz Irber:** Yeah, and we also set the developer infrastructure around. Like, we run all the tests in CI with GitHub Actions. We also set up to replace GSW-C in GSW-Python when the R one is not working that great yet. But we run the tests for GSW-Python on top of our implementation to see if we are matching everything.

So, we try to go, like, taking great care of how the functions are implemented, that we are getting all the scientific parts right, and then evaluating across whatever we can that can use this and has tests to make sure that's also correct across languages.

[00:33:47] **Arfon Smith:** I was just going to say, it sounds like you're being incredibly diligent with this library, which sounds entirely appropriate for the type of work that you're doing. Also I love that it sounds like it's a nice contributor experience that you've got set up there with the code, the tests, and the docs all together.

So definitely sounds like this project is open for contribution. I wanted to close this out by just asking you both how people can keep up with your work online, keep up to date with your work. Are there any particular places you would want people to follow you or subscribe to your work? Luiz, do you want to go first?

[00:34:18] **Luiz Irber:** Oh, I have a website up. It's called LuizIrber.org that has blog and talks that I give. I've been lowering as much as possible my consumption of Twitter and the likes. So, I do have Mastodon and BlueSky and Twitter accounts, but not very active over them.

[00:34:37] **Arfon Smith:** And what about yourself, Gui?

[00:34:38] **Gui Castelao:** I'm a little bit limited on the presence, but I have a website, castelao.net, and @castelao is my handle in GitHub, I think it's the best way to track me and see what I'm doing. 

But I have one question for you both. How can we contribute to JOSS? Like we already do reviews and we already do stuff, but we really think that this is an important thing.

One of the risks that I see is that this is so great that everybody's seen that and is jumping in. How do we scale that and how can we help more than just reviewing papers?

[00:35:13] **Arfon Smith:** Well, you're playing a huge part by reviewing already, and Luiz is actually an editor at JOSS as well, so he's double, double helping there. One of the sustainability challenges that we face as a journal is just not burning out reviewers and editors. So, I think the most concrete thing I could say is, if you have thoughts on how to make reviewing or editing at JOSS a more sustainable, process for the communities that you operate in that's always very welcome.

Send us great editor suggestions when we do public calls for new editors, because that happens semi regularly. We just closed that out most recently in December, and we're currently onboarding new editors. But yeah, it's a great question, and thank you for the care and attention. It's appreciated. I agree, JOSS is important, and we want it to thrive and survive for a long time. 

[00:36:03] **Gui Castelao:** Thank you. Thank you both.

[00:36:05] **Arfon Smith:** Yeah, okay, 

[00:36:06] **Gui Castelao:** rest of the team. 

[00:36:07] **Arfon Smith:** Abby, do you wanna, do you wanna wrap this up?

[00:36:09] **Abby Cabunoc Mayes:** This was a very fun conversation. I enjoy all the swag, all of the logo offs. It was lovely chatting with you both, and yeah, best of luck with this work. And I'm looking forward to seeing how it grows and how the community grows around it.

[00:36:21] **Arfon Smith:** Yeah, thanks for your time both.

[00:36:23] **Gui Castelao:** Thank you. 

[00:36:23] **Abby:** Thank you so much for listening to Open Source for Researchers. We love to showcase open source software built by researchers for researchers, so you can hear more by subscribing in your favorite podcast app. Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes, edited by Abby, and the music is CC-BY Boxcat Games.


[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/tZx0Ee7r_xI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>