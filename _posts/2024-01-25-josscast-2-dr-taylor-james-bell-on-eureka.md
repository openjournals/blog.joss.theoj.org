---
layout: post
date: 2024-01-25 00:00
title:  "JOSSCast #2: Astronomy in the Open – Dr. Taylor James Bell on Eureka!"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Dr--Taylor-James-Bell-on-Eureka-e2ersul/a-aasohms" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)


In this episode of Open Source for Researchers hosts Abby and Arfon explore the world of open source software in astronomy with Dr. Taylor James Bell, a BAER Institute postdoc at NASA Ames. Eureka! is an end-to-end pipeline designed for JWST (James Webb Space Telescope) time series observations. We chat about the motivations behind Eureka!, its unique features, and the democratization of exoplanet science.

Join us for an engaging conversation that unveils the complexity of time series observations, the power of open source, and the exciting future of Eureka! and JWST discoveries.


### Links
- Paper: [Eureka!: An End-to-End Pipeline for JWST Time-Series Observations](https://joss.theoj.org/papers/10.21105/joss.04503)
- [Code repository](https://github.com/kevin218/Eureka) 
- [James Webb Space Telescope](https://webb.nasa.gov/) (JWST)
- Nature paper using Eureka!: [A broadband thermal emission spectrum of the ultra-hot Jupiter WASP-18b](https://www.nature.com/articles/s41586-023-06230-1) 
- Taylor’s website: [www.taylorbell.ca](http://www.taylorbell.ca/) 
- [@taylorbell57](http://github.com/taylorbell57) on GitHub
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))



### Transcript

[00:00:04] **Abby:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by researchers for researchers. My name's Abby

[00:00:11] **Arfon:** and I'm Arfon.

[00:00:13] **Abby:** and we're your hosts. Every other week we interview an author published in the Journal of Open Source Software, JOSS, and this is episode two . We're chatting with Dr. Taylor James Bell on his software Eureka! and the paper's called Eureka!: an end to end pipeline for JWST time series observations.

[00:00:30] **Arfon:** So this is an exciting episode for me, we get to dig into some of the open source software that's been built for the James Webb Space Telescope, which is a mission I used to work on in a previous life. This is a groundbreaking scientific observatory that's in space right now and doing great science and it was really interesting to chat with Taylor about the work he's doing with the team.

[00:00:49] **Abby:** Yeah, and even for me as not an astronomer who didn't quite understand everything about exoplanets, I still really enjoyed just his experience trying to build the software in a way that is community focused and not just publishing a paper and having it go out

[00:01:05] **Arfon:** Absolutely. Yeah. Looking forward to jumping in.

[00:01:08] **Abby:** Let's do it.. Taylor, do you want to say a little bit about yourself? 

[00:01:12] **Taylor:** Yeah, I'm a BAER Institute postdoc here at NASA Ames in Mountain View, California. I work on studying the atmospheres of exoplanets, so planets orbiting distant stars. And to do that, I do a lot of data analysis and recently open source software. 

[expand]


[00:01:29] **Abby:** That's amazing. 

Just to kick us off, why did you start this project, this piece of software? 

[00:01:34] **Taylor:** it was initially started by two of my colleagues, Kevin Stevenson and Laura Kreidberg, two faculty in astronomy. and they're both well respected experts in the analysis of Spitzer and Hubble space telescope data.

But we wanted to prepare for the JWST launch, which was coming up in about a year from then. So the two of them have written software for Hubble and Spitzer and wanted to get ready. And they wanted to do something different this time. Their code for Hubble and Spitzer, sometimes it was open source, sometimes it wasn't, but it was never community built, community driven and really truly open source. Not just open source, but like well documented and user guides and documentation and all of these things. So they reached out to a broad group of experts in the fields to get involved and make it a large team project.

And so about a dozen of us joined the team. and just naturally through those collaborations, I rose to a kind of primary contributor level in the team. 

[00:02:39] **Abby:** That's awesome. and I should have mentioned before, we are talking about Eureka!. 

[00:02:42] **Arfon:** Yeah, I was going to say this is really cool for me to hear about this piece of software, Taylor.

I used to work at Space Telescope Science Institute in Baltimore, which is where the James Webb Space Telescope is operated from. And so it's really nice to see such a rich sort of ecosystem of open source tools that are being developed around the Webb Telescope. That seems to be turning out to be, a defining feature of this mission as compared to earlier missions.

I guess, actually other space missions have been good at this. I know Kepler was very strong, especially in the K2 phase of the mission was really strong on open source and community software as well. 

[00:03:15] **Abby:** Yeah, so related that do you have a strong background in open source?

Or is this your first time doing something open source? 

[00:03:21] **Taylor:** So my undergrad was in physics, but I did a minor in computer science. I took about a half a dozen classes or more. Taking, a lot of programming principles and practices and stuff like that. So I got some experience. In the kind of 2018 to 2020, I wrote two open source packages.

One of them falls nicely into the open source and well documented and, all of those things. That was a simulation tool, a pretty basic little tool to model what an atmosphere might look like. Like what an observation of a planetary atmosphere might look like. And then I also built a pipeline for Spitzer. I co developed that.

It was open source, but again, not in that regime of actually, broadlly usable by people. 

[00:04:08] **Arfon:** I was going to ask about who your target audience is for this software. So I know a little bit about what Webb is doing and looking at the atmosphere of exoplanets. Maybe I'd be, I think, helpful to just explain a little bit about what the telescope's doing, what type of observations it's making, and who cares about those kind of observations? Would you mind sharing a little bit of just background. Who, uses this and why, that's interesting? 

[00:04:33] **Taylor:** For sure, yeah. Eureka! targets time series observations. So these are observations that, , monitor something over a length of time.

And so we're monitoring changes in brightness. The primary use case that we've developed it for, which is all of our developers primary science use, is to observe exoplanets. So we look at transits, eclipses, things where we're looking for a change in brightness of the combined system of fractions of a percent.

And we're looking for very small features. A lot of existing institutional code is not excellent for time series observations because time series observations are very different from just taking a single snapshot of a galaxy. You have to treat the data in very different ways when you're treating single snapshots. You really want to know how bright is every individual source absolutely. How many exact number of photons are coming from that. Whereas for time series, you want to know very precisely how that number is changing. You don't care what the constant value is. You just care how it changes. and yeah, there's a lot of differences there.

We built this pipeline for researchers. We've built it in no small part for our own use. and that's been part of our big success is that all of us developers are very actively using the code. But really one of the driving motivations behind it was that programming ability shouldn't define scientific success.

[00:05:59] **Taylor:** And so there's a lot of, especially early career researchers and people all over the globe that want to participate in exoplanet science, but don't have the programming ability to do to build a complete pipeline from scratch that is independently verified and things like that. 

It's a huge feat and it was something that the community struggled a lot with Hubble and Spitzer. And yeah, our target demographic really ranges from undergrad researchers working for professors and the professor gives them a single observation all the way to faculty and postdoc who just want to quickly crank something through.

[00:06:35] **Abby:** I really resonated with what you said about how the ability to code shouldn't determine your ability to do research and how this open source code is really democratizing science in a way that we haven't seen in a while.

So that's exciting.

[00:06:46] **Arfon:** Yeah, I was going to ask, it's related on that. How low is that barrier? I know a little bit about where the JWST data ends up. A lot of it is in the MAST archive at Space Telescope and I think you can get it in the European archives as well.

Can I just go download some data and run this tool? How turnkey is it for, an end user? 

[00:07:04] **Taylor:** That's something we've been struggling with in two mutually opposing ways. One is, yeah, a lot of JWST data, there's an initial proprietary period of about 12 months or something, but then eventually it becomes public and so anyone can look at it.

Then, there is some amount of analyzed data that is archived along with those raw data, and that's not particularly good quality at this point in time. STScI, the Space Telescope Science Institute, is working on improving that data quality. But in the meantime, it's in a fairly rough state for time series observations.

And then for actually using Eureka! to get science data out. We're fighting kind of two opposing directions. One is we want it to be really easy and accessible for everyone to use. No programming, obviously, but minimal barriers. And so we're working on, making better documentation, making better templates.

So that basically you just need to specify where your inputs and outputs are and you can get a half decent first result. But something that we have learned with Hubble and Spitzer is that what works well for one observation almost never works perfectly for another observation. It might work okay, but that doesn't mean your results are going to be ideal or even necessarily exactly right.

And so there's some amount of fine tuned fiddling that needs to be done, and some amount of intuition that needs to be done of what do you check to make sure that what you're getting out is reasonable. And so we don't want people to think of Eureka! as a black box, that they just put something in, they get something out, and they're like, okay, fine. I'll write my paper on that.

And so one of the things that we're doing is we're putting out a lot of log information, but trying not to overwhelm people, just give them some heuristics of what's going well but also plot, plot all kinds of things because humans are pretty visual creatures and then being able to just click on all the things and gain some intuition for oh, if I change this parameter, this thing changes in some desirable or undesirable way.

And yeah, just really trying to graphically demonstrate things to people.

[00:09:20] **Arfon:** Awesome. That's really cool. It sounds like. I probably could, as long as the data is outside the proprietary period, I probably could take the software for a spin, but you'd need to be a little careful, which I guess makes sense. It might work, but you'd want to be careful and really validate the kind of outputs you were getting before putting those, results in a paper or anything.

[00:09:40] **Taylor:** Yeah, the way, I think of it is it's the default values are great for a quick first look, Do I have an atmosphere? Did I catch a transit? Did the observations work? And then when you want to get to publication readiness, when you have to twist all those little knobs. 

[00:09:53] **Arfon:** I actually have a side question, which is, how do you know when to look? So I think if I understand what's right, what you're saying is, you're looking at an exoplanet. You're interested in atmospheres, which means you're looking for an exoplanet as it goes in front of the star that it's orbiting. JWST is not looking there all the time, right?

Instead doing other things. So how do you know when to make the observation? Is that, a hard thing to figure out? Is that something that Eureka! does as well? Or is that a separate thing? 

[00:10:22] **Taylor:** No, yeah, that's separate. JWST for, the vast majority of its time is not, at least for exoplanet stuff, it's not looking for anything new.

It's, not looking for new planets. It's looking to characterize well monitored planets so that we know the orbital period so Kepler is a great example. It's observed a hundred transits of the thing because it has an orbit of a day and so just by staring at it for a month you catch 30 transits and you know exactly when it's going to transit. And then ,doing some fancy fitting you can try and figure out when it should eclipse based on what you think it's orbital eccentricity is and things like that.

Yeah, just a lot of Kepler's laws and using the Kepler space telescope as well as excellent ground based telescopes like loss is.

[00:11:09] **Arfon:** Cool. Awesome. Thanks for that. So I guess one of the thing I'd be really curious to learn about is what, how does this Eureka! package differ from what's already available? I think exoplanet science is not brand new. It's relatively recent. Are there other tools that people use where you're finding a gap in what was possible?

Can you say a bit more about what people might have done before Eureka! even, or what they're doing alternatively today if people aren't using the tool. 

[00:11:34] **Taylor:** Yeah, so there's numerous alternatives at present for JWST data. Most of them are developed specifically for JWST data. I find that is a very good thing, especially early on in telescope's life, having many different people do many different things, and then we've worked somewhat on comparing those pipelines at the end, because, yeah, it's great if you have multiple things, but if that means a hundred different papers get published using a hundred different pipelines, and you don't know if you can compare planet A to planet B because they're different so it's great to have multiple pipelines but also need to compare them.

As for how Eureka! differs to them many pipelines are focused on just dealing with a single instrument on JWST. JWST has four primary science instruments. You have NIRCam, NIRISS, NIRSpec, and a mid infrared detector, MIRI. and within each of them, you also have multiple different filters and different observing modes.

You have spectroscopic data, you have photometric data, where you're just taking images instead of spectra. There's really a diverse amount of possibilities. and exoplanets uses basically all of them. Not all of the modes, obviously, but an enormous amount, and all four instruments. And at present, we're the, one of the few that targets all four instruments with all exoplanet specific observing modes.

We're currently missing the NIRISS instrument but we've just got funding just earlier this week to implement NIRISS code in there. That's one big differentiation. Another is that it is community developed and community supported. There's, about a dozen of us who have contributed large parts, but we get almost weekly, if not more often issues submitted through GitHub, which , allows us to help support people.

A lot of pipelines that just exist, yes, they might be hosted on GitHub, but it's hard to get anyone to respond. Whereas there's many of us who try and work with people, help them get up and running. and compared to what existed before JWST, it's complex with all of these different instruments but in some ways, some of the instruments are quite like Hubble, and some of the data is like Spitzer.

And this, pipeline is kind of Frankenstein bits of Hubble and Spitzer code that was previously written by Laura, Kevin, and I as well as some other people. And so it's drawing on all of that together. and at present, we allow Hubble and JWST data to be fitted with Eureka!. It's my personal aspiration that someday we might add Spitzer, but Spitzer is now decommissioned, so it would mostly be for, archival research, which takes a lot of energy to build something new for something that's just archival research.

There's also the Space Telescope Science Institute does have its own software to support observers. One of its big weaknesses, in my mind, is lack of plots. There's no plots that are made. You can save intermediate results, but a lot of people just want to run the pipeline and not, have to interject a bunch of things to make plots or force save every intermediate result and then plot it after.

And so that's, one big thing that we're doing is just really making visible all of the intermediate results. And then we also are, we call it an end to end pipeline, where we go from raw pixels to planetary spectra. And in truth, there is slightly further you can go of turning planetary spectra into okay, what's that atmosphere made out of? Is there carbon? Is there carbon monoxide? Stuff like that. 

But we do largely end to end. Stuff which is, again, not something that the STScI pipeline does, and, something that is often done by other community pipelines. 

[00:15:44] **Abby:** That's amazing. First off, congrats on the funding. That's always huge to get that, especially in the research space.

I also really resonated with what you were saying about being community built I do think a lot of the power of open source comes from building with the community and with others. So how are you getting the word out to the community? Is this why you published in JOSS, the Journal of Open Source Software?

What else are you doing to bring the community together? 

[00:16:05] **Taylor:** Yeah, it was definitely a large part of why we published in JOSS A), to make sure people heard about us, have a nice, clean way to publicize the pipeline and its state at that point. We, also were quite involved in early release science.

JWST came with early release science observations, which were community proposed observations that would test JWST and in many of the key science cases and collect some open public data for the community to learn on and do a lot of these pipeline comparisons.

And so a lot of, I think every ERS Early release science paper had Eureka! on it. and an advantage of having a dozen developers on it and also just making it open source. Several of the analyses that have been published so far are not by Eureka! developers. We've also been working on leading, tutorial sessions and doing workshops at the Sagan Summer Workshop held at Caltech this past summer.

We held two hands on sessions, training people how to go from pixels to light curves, and light curves to planetary spectra. And that was a free conference to attend, either in person or virtually. and so we had hundreds of people participating in that, primarily early researchers, but also some faculty and stuff like that.

And so that Sagan Summer Workshop covered the Eureka! pipeline which takes us from pixels to planetary spectra, and then two different methods of going from planetary spectra to atmospheric compositions. And yeah, just doing a lot of kind of outreach like that and then also just letting our work speak for itself. We're comparable to a lot of pipelines, we're easy to use. Encouraging people to check them. 

[00:17:58] **Abby:** Yeah, that's great. And I do love the workshop method for getting people on board. Are you finding that a lot of these users become contributors eventually or start contributing in small ways? 

[00:18:09] **Taylor:** That hasn't yet happened. It's, still very early days.

We haven't even released version 1. 0. We're on 0. 10, I think we just released. We, have had community members contributing code. But that workshop was, only a couple months ago. We do get issues submitted by the workshop attendees and, others, which helps. But primarily it's been us developers solving issues for people at this point and less people contributing their own solutions.

[00:18:37] **Abby:** Right. I do think that issues are a valid form of contribution to open source. That's very important.

[00:18:43] **Taylor:** Good point. 

[00:18:43] **Arfon:** I was actually going to say I mean Abby and I probably spend a lot of our lives doing this. Maybe you do as well, Taylor, but, when you go and look at a project open source project, you can get a sense just by clicking around if stuff's happening, are there issues being opened and closed, are there pull request being opened and merged. And Eureka! looks great. There seems to be tons of activity on the project, which looks fun and it looks like it's really a healthy project.

Lots of people opening issues, lots open, but lots have also been closed. It's always a good sign to see that. yeah, congrats on a really, nice project. 

I wanted to ask a little bit about the review process that you went through. So just to explain very briefly, this of course, Taylor, the JOSS review process is an open one.

It happens on a GitHub issue. A couple of people come and go through a checklist driven review process and then ask questions and suggest improvements. I know it was a bit over a year ago, so I know it's a little while ago, but I wondered if you had any things you wanted to share about that review. Did it help you as authors of the software? What was your kind of lasting experience from that? 

[00:19:45] **Taylor:** Before Eureka!, all pipelines that I've written and all pipelines that I can immediately think of that were written were never published in themselves. They were always like, I've got these new Spitzer data, so I wrote a pipeline. I tersely write what the pipeline does in the paper, but it really it's a science paper. So as a result the referees of that paper really don't focus that much on the pipeline. It's left to the developer of that pipeline to cross validate it with other pipelines and make sure that they didn't drop the square root of two anywhere or things like that. With JOSS, it's still on you to not drop, square roots of two and stuff, but it was much more focused on the pipeline and on the documentation and making sure that there's, an easy way to install the pipeline and tutorials and things like that.

Which was significantly beneficial to the pipeline. It was great to really have the spotlight on the pipeline itself. 

[00:20:50] **Arfon:** Typically you'd have astronomers reviewing a piece of astronomy pipeline. These people could be users I guess, or proto users. You could imagine review might touch on code quality, documentation, installation. Was there a particular area where you're like, oh yeah, this is significantly improved some outcome here, or was it just a fairly broad analysis by the reviewers? 

[00:21:08] **Taylor:** I'd say the area in which we most improved as a result of the JOSS review is documentation. It was something we had spent a significant amount of time on, and post facto writing documentation, which is always the wrong way to do things, because it's so miserable to read other people's code.

Again, most of this was written for Hubble and Spitzer, many years ago, and so it's even the people who wrote it don't necessarily remember what they wrote. I spent a lot of time writing documentation and like trying to make it uniform. In preparation for the JOSS review, and then the JOSS reviewers pointed out even more situations where, it could be improved, which definitely made things a lot better.

I'll admit we still have a folder of old functions that were written initially in IDL and then converted to Python, but the comments never changed. But we have 30, 000 lines of code and at least at the start we weren't being paid for developing this, and so it was us donating our time.

Now that we have some money, we can Invest more time in this, but again, 30, 000 lines of code, you can only do so much. We really focused on the user accessible layers of things and a lot of the really deep stuff that's five, six functions deep is where you start getting a lot of computation.

But the documentation and the the way of installing the pipeline were definitely improved.

[00:22:32] **Abby:** I guess related to that, this does sound like it's one of the bigger open source projects and definitely one of the more community focused open source projects you've ever contributed to. And I know the JOSS review process is really focused on getting that stability or that groundwork you need to build that flourishing community.

Any big surprises come your way working open source or working openly? 

[00:22:51] **Taylor:** I think the initial surprise that I had was, at how functional we were working with, a dozen people working on the code. There's so many opportunities for people trying to do the same thing and, overlapping and, then you have nasty merge conflicts and stuff.

But, yeah, at the start we had the core dozen or so of us would have a Zoom meeting every week or two weeks to divide up some tasks. But then I've been surprised at how well things have kept running. It hasn't fizzled out because that's so easy to happen. A lot of projects start and then people are kind of like eh, good enough.

We definitely have less contributions because the pipeline is getting to a good state. I mean, a better state. But there's still a lot of interest from many of the members and the community interest is ramping up as time goes and we're starting to see more and more pull requests which is, yeah, takes the burden off of us too if people, are, writing it like they have an observation of two planets instead of one, and they have to do some special stuff to the code, and then they just contribute that, rather than us having to be like, oh, we have to build something from scratch, if people are doing this, and they do it for themselves, and then people have been very willing to just offer that back to the community in a in- kind donation, which is awesome.

[00:24:19] **Abby:** I love that. The piece that surprised you is just how well collaboration and open source is working. It's perfect. 

[00:24:25] **Arfon:** That's nice. Yeah. 

I wonder if I could take us back to the web and science just for a moment. I was curious, like the, software's existed for a while. I think you mentioned that you built Eureka! to be ready for the early release science program.

As a bit of a space nerd, I was myself, I was curious, are there any results that you're particularly excited about from JWST? Related to Eureka! or not, are there any things that are really memorable for you and, or, things that you're anticipating would be, really exciting discoveries that you're hoping to see in the not too distant future. 

[00:24:59] **Taylor:** Yeah, I think one was all of the early release science observations. We had observations with all four instruments. I was just stunned by the beauty of the data and the remarkable quality of it. I've talked a lot about Hubble and Spitzer and both of them, their raw data was kind of ugly for exoplanet science.

There's just a lot of noise and a lot of dealing with 1 percent systematics to get to 0. 01 percent astrophysical signal. Whereas here we're dealing with noise that's at or below the astrophysical signal. And so just the astrophysical stuff just pops up.

One example is the carbon dioxide detection on WASP 39. This was the first paper put out by the ERS team. And that's just a great example of run it through first time, you didn't fine tune everything and then boom, you see this feature that we've been looking for a long time.

That was super exciting. More recently I just had a paper come out in Nature where we used Eureka! and another pipeline to to find methane in a exoplanet atmosphere. And so this is something that we've been looking for a long time in transiting exoplanets. But Spitzer was photometric, and its filters were very broad, and so it averages together a lot of different wavelengths all into a single point.

And so methane would be mixed with water, and carbon monoxide, carbon dioxide, and there's a whole big mess of things, and so really saying that there's methane in the planetary atmosphere has been very tough, but with that paper, yeah, you could just see the bump and divot caused by methane, and yeah, that's been really exciting too. 

[00:26:44] **Arfon:** So this is just the higher resolution spectra is that why you can see it. It's not convolved with some other, signature, 

[00:26:51] **Taylor:** Higher, resolution spectra and, just higher, signal. Just JWST is so much larger. 

[00:26:56] **Arfon:** Bigger mirror! 

[00:26:57] **Taylor:** Big, bigger mirror, better resolution, and vastly smaller systematic noise components all together make it possible.

[00:27:07] **Abby:** That's great. So it does sound like this project is open for contributions. What kind of skills do I need to jump in? 

[00:27:14] **Taylor:** So it's all written in Python. Yeah, we've considered doing some Cython to make some core things faster, but as of right now everything's Python. So it's primarily just Python and GitHub.

Just knowing how to use those two. Basically the only things you need to know how to contribute. There's open source data that you can mess around with and try things out and see what works for you, what doesn't. We do have a community policy to make sure that your contributions are appreciated and respected and that everyone else is also respected.

Yeah, it's, basically GitHub, Python and then some time. 

[00:27:51] **Abby:** That's great. and any any scientific knowledge needed? 

[00:27:54] **Taylor:** We, try to be somewhat pedagogical with some of the stuff. Especially the, first four, Eureka!'s broken into six stages. The first two stages are just really dealing with nitty gritty JWST specific pixel stuff.

And for that we rely on the software built by STScI, their JWST pipeline. But then we tweak it in some ways. Then the middle stages are data analysis. They're not really science focused. It's like how do you go from pixels to a spectrum. 

And then stage five is where you get into a little bit of science. What does exoplanet transit look like? And there's great open source packages that we've been using for that. And then stage six is just stapling together a hundred different wavelengths, just put them all into one section. So yeah, fairly minimal requirements for learning the science behind it.

[00:28:47] **Arfon:** Cool. 

I think I've stared at bits of the JWST pipeline in the past, so maybe I'll find some of that code in there too. So what's the best way that people can stay up to date with your work, Taylor? It sounds like you had a Nature page recently, so congrats on that. But how can people find you online and, keep up to date with Eureka! and its latest releases?

What's the best way to for folks to keep track? 

[00:29:08] **Taylor:** Probably the best way is my personal website, www.taylorbell.ca. I have all my socials and stuff linked on there and I try to keep it up to date. There's some blog posts of some science I've done and many of them are just placeholders where I'll eventually write stuff, but yeah. That's a good place to keep track on me and find my GitHub and things like that, too. 

[00:29:32] **Arfon:** Cool. Thanks. And future releases of Eureka!? Is GitHub the right place to keep track of that as well?

Is that where you would release new versions? 

[00:29:40] **Taylor:** Yeah, yeah, we just released version 0. 10 probably two weeks ago, and we're working actively on version one right now where we'll not really add any new features, but just make the maintenance a lot more sustainable on us and just reorganize things and do some backwards compatibility breaking to make things easier for users and developers.

[00:30:00] **Abby:** Nice. So that's on GitHub. That's taylorbell57, I believe. We'll link all this in the show notes so people can go find those. But thank you so much, Taylor, for joining us. This is a great conversation. 

[00:30:10] **Taylor:** 

Thanks so much for having me.

[00:30:12] **Abby:** Of course. 

[00:30:12] **Arfon:** Yeah, and congrats on a really nice piece of software. It looks really great. I wish you all the best and I hope, there are many future releases. it looks really great. So thanks again for telling us about your package. 



[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/qB7hL93yxdA?si=ltRBUOtSiWZ5EsxV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>