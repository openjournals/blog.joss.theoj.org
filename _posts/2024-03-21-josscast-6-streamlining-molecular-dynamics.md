---
layout: post
date: 2024-03-21 00:00
title:  "JOSSCast #6: Streamlining Molecular Dynamics – Marjan Albooyeh and Chris Jones on FlowerMD"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Streamlining-Molecular-Dynamics--Marjan-Albooyeh-and-Chris-Jones-on-FlowerMD-e2hc06f" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)

Marjan Albooyeh and Chris Jones chat with Arfon and Abby about their experience building FlowerMD, an open-source library of recipes for molecular dynamics workflows.
 
Marjan and Chris are both grad students in Dr. Jankowski’s lab at Boise State University where they use molecular dynamics to study materials for aerospace applications and organic solar cells. Before joining the lab, Marjan was a machine learning researcher. Chris learned to code when the lab’s glove-box went down and he never looked back.

You can follow them both on GitHub: Marjan [@marjanalbooyeh](https://github.com/marjanalbooyeh) and Chris [@chrisjonesBSU](https://github.com/chrisjonesBSU).

### Episode Highlights:

- **[00:00:12]** Introduction to FlowerMD and its creators, Marjan Albooyeh and Chris Jones.
- **[00:02:54]** Explanation of molecular dynamics simulation process and applications.
- **[00:05:10]** Insights into FlowerMD's development process and design goals.
- **[00:09:26]** Target audience for FlowerMD and its usability for researchers.
- **[00:11:30]** Importance of reproducibility in research facilitated by FlowerMD.
- **[00:16:18]** Challenges faced building FlowerMD.
- **[00:19:52]** Experiences with the JOSS review process.
- **[00:22:39]** Contribute to FlowerMD!
- **[00:24:08]** Future plans for FlowerMD and building a research community.

### Links:

- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05989](https://joss.theoj.org/papers/10.21105/joss.05989)
- FlowerMD repository: [https://github.com/cmelab/flowerMD](https://github.com/cmelab/flowerMD) 
- Chris Jones's GitHub profile: [@chrisjonesBSU](https://github.com/chrisjonesBSU)
- Marjan Albooyeh's GitHub profile: [@marjanalbooyeh](https://github.com/marjanalbooyeh)
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))
- [Donate to JOSS](https://numfocus.org/donate-to-joss)

### Transcript:

[00:00:05] **Abby Cabunoc Mayes:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by researchers for researchers. My name's Abby.

[00:00:11] **Arfon Smith:** And I'm Arfon.

[00:00:12] **Abby Cabunoc Mayes:** And we're your hosts. Every other week we interview an author, and in this case two authors, published in the Journal of Open Source Software, or JOSS. 

This is episode six, and today we're chatting with Marjan Albooyeh and Chris Jones about their paper FlowerMD: flexible library of organic workflows and extensible recipes for molecular dynamics. 

So it was great to hear about their work.

[00:00:33] **Arfon Smith:** It was. 

[expand]

[00:00:35] **Arfon Smith:**It's a really tidy submission had a really fast review, and I think rightly so, I think it's really well put together piece of software.

[00:00:41] **Abby Cabunoc Mayes:** Yeah, and it's interesting how it's taking a lot of different open source software in this field, and then, links them all together into FlowerMD. So that people can just really focus on the science, they don't have to think about building this workflow every single time. They really thought about making this useful for others.

[00:00:57] **Arfon Smith:** Yeah, Marjan talks really nicely about the process they went through to really design the software and get the right sort of abstraction so that it was super usable for their community of users.

So I think that's our first student submission on JOSSCast, right?

[00:01:12] **Abby Cabunoc Mayes:** I believe

[00:01:12] **Arfon Smith:** students have been involved, but I think this is it.

I, personally, I learned to write software during my PhD. Uh, I don't think it would have been worth publishing in JOSS bluntly. Uh, but, honestly, but, um, I think, you know, It's cool to hear about some grad students producing some nice tools for their research area and publishing in JOSS.

[00:01:32] **Abby Cabunoc Mayes:** .So yeah, excited for you all to listen to the interview.

[00:01:35] **Arfon Smith:** yeah, let's jump in.

[00:01:36] **Abby Cabunoc Mayes:** Marjan and Chris, do you want to give yourselves a brief intro before we dive in?

[00:01:39] **Chris Jones:** Sure. So, we're both students in Dr. Eric Jankowski's lab at Boise State University. We're in the College of Engineering in the Micron School of Material Science and Engineering. In this lab we use molecular dynamics to study materials for aerospace applications and also looking at materials for organic solar cells. 

[00:01:58] **Arfon Smith:** cool. And what about yourself, Marjan? 

[00:02:00] **Marjan Albooyeh:** Hi, I'm Marjan. 

I'm a second year master's student here at the Computational Materials Engineering Lab at Boise State. My previous background was in computer science. But I decided to continue my academic research in material science, so that's why I joined this lab. And we've been doing molecular dynamics research for most of the time combining it with like other tools, like machine learning and analysis.

[00:02:26] **Arfon Smith:** Very cool. Well, welcome to the podcast. I guess I wanted to kick us off by just checking that everyone knows what molecular dynamics is because I think I know and I could guess an answer, but I'd love to hear you both just explain a little bit of background about what molecular dynamics is, when researchers might use it when maybe you wouldn't use it.

Like, what's the elevator pitch for molecular dynamics and why it is a thing that's used, for example, in material science?

[00:02:54] **Chris Jones:** Okay. So, there's lots of different simulation methods that scientists and engineers are interested in, and they all span an array of time and length scales. And with molecular dynamics, we're kind of down in the nanosecond to microsecond and the nanometer to micrometer length scales.

And with MD, we're simulating particles, so atoms and molecules and their bonds between the atoms.. And the main thing here is that we're just using classical physics, so we're not making any considerations for quantum mechanics or anything like that. So we just use Newton's equations of motions, and we have all these forces and interactions between the particles, and we can calculate the positions of particles and how that evolves through time.

[00:03:35] **Marjan Albooyeh:** Yeah, so I think in general, molecular dynamics is a great tool to see the evolution of the particles in a box over time see like how the particle moves and what kind of shape or like structure they end up getting after you start your simulation and the cool thing about the molecular dynamics engines that are out there is you can tweak parameters.

You can change parameters related to your simulation and see how those changes actually affect the final output of your trajectory.

[00:04:05] **Arfon Smith:** And so if I understand it correctly , you wouldn't use molecular dynamics to simulate a single molecule. That would be more like a quantum chemistry package like density functional theory or some other, you know, super, where you care about electrons and all the quantum states.

So it's not that, it's a bigger systems than that. Is that fair? 

[00:04:26] **Chris Jones:** Yeah, that's right. And then and then it's smaller than other simulation methods, like finite element analysis, where you might simulate like a shape, like an airplane wing or something, and how that interacts with airflow or something like that. So like things that large, you cannot use MD for.

[00:04:43] **Arfon Smith:** Okay. And, and is this very standard in like material science? Is this a thing? Is this the sort of standard at this kind of resolution of detail? That allows you to understand the properties of materials? Is that why it gets picked?

[00:04:54] **Chris Jones:** Yeah, it's a popular choice. There's also Monte Carlo, which can study the same levels of length and time scale, but it's a different algorithm that it follows. I think which one is better than the other kind of depends on the application and the questions you're trying to answer.

[00:05:08] **Arfon Smith:** Well, thanks for the background. That's really interesting.

[00:05:10] **Abby Cabunoc Mayes:** And back to FlowerMD, this is a super cute name um, I believe. I believe the acronym was spelled out in the paper title but can you tell me a little bit about why you started this project, and maybe how you came up with the name. Did you purposely try to spell flower? I always wonder.

[00:05:27] **Chris Jones:** I guess it's a backronym. We wanted a nice acronym and flower was cool. So we kind of forced it to fit the features of the software. 

[00:05:37] **Marjan Albooyeh:** We changed the name. 

[00:05:38] **Chris Jones:** We changed the name a couple of times before we settled 

[00:05:41] **Arfon Smith:** Side note, this seems to be a pattern in all areas of research. You're like, God, that's really close to this word that would be cool. Okay, how can we change this?

[00:05:51] **Chris Jones:** Yeah. 

[00:05:51] **Marjan Albooyeh:** Yeah. Right before we started to actually find the name, we were like, we are not going to do acronyms. It's just like, something that everybody does. Let's do something like cool. But at the end we were like, okay, maybe this acronym works better because it tells exactly what we want it to tell.

So, yeah.

[00:06:09] **Chris Jones:** So why we started the project. An anecdotal experience that we experienced in this lab is some of the students before me had their own research project they're working on, and they created their own package that kind of puts the different pieces together to allow them to study and answer the questions they want to answer. And it was a great package. 

And then, when I started, I started with a new project that was looking at similar kinds of things, but trying to answer different questions. What ended up happening is that a bunch of the choices that the previous students made when designing their package were kind of ad-hoc to their project. 

So a lot of the things in that package I couldn't use for my project. So it's kind of in a spot where I had to start over from scratch to make my own package to work on my project. And so I did that and I was working for a while and then another student joined the lab with another project that was similar, but just a couple of things were different.

And again, I kind of made the same mistake in my package where I just made all these assumptions about the project I was working on and hard coded into this workflow. And so we were faced with the possibility of having to write a third package from scratch, where, again, a lot of the stuff is kind of the same from one package to the other.

So before we did that we just took a step back to think about, okay, how can we write a package that's doing these types of workflows and experiments that we want to do, but doesn't make any assumptions about the questions of the project or the goals of the project. So we started over with Flower and I think Flower would work now for any of these three projects we're working on and others.

So it's kind of the design goal for Flower. And I think the story that we experienced is something that's very common in academic research. Especially computational academic research where everyone's kind of developing their own tools at their desk. A lot of these workflows and tools aren't being shared.

There's not a lot of standards in place for some of these things. And we just end up with a lot of repeatable work, and it's not necessarily 

[00:08:08] **Abby Cabunoc Mayes:** I really love that, just open sourcing a tool that you can use multiple different ways, but also can help other researchers use multiple different ways, and they can focus on the science and not have to rebuild something over and over

[00:08:18] **Chris Jones:** yeah, exactly.

[00:08:19] **Arfon Smith:** In your domain model, then, for FlowerMD is each of those three scenarios now a recipe? Like, an extensible recipe? Is that what they would be?

[00:08:27] **Chris Jones:** Yeah, that's kind of the idea with the recipes. So the design of FlowerMD is we kind of created this base that any project might need. So any project might have to create molecules, any project might have to arrange these molecules in some box to create an initial configuration, and any project's going to have to run a simulation.

So we created these base classes. Where these things are kind of all separate, isolated parts of the package. But then how you put them all together is the recipe part of it, I guess. 

My project is the thermoplastic welding recipe that's in Flower right now. The previous project I mentioned it wouldn't necessarily be a recipe, but all the tools are there right now for them to be able to do the work that they had done already.

[00:09:14] **Arfon Smith:** Yeah, that makes sense. So who's your target audience for this software? Is it people designing materials? Like what's the sort of typical job titles of people who would, or research backgrounds of people who would be using your software?

[00:09:26] **Marjan Albooyeh:** So I think like any researcher could be undergrad, graduate students, or postdocs who are doing research on molecular dynamics, specifically on organic materials. Basically anyone who likes to see this evolution of particles in their material they can definitely benefit from FlowerMD.

And I think one of our goals was to build it in a way that it's kind of clear and easy to understand for those who are not necessarily very familiar with like programming languages or using like software packages. So because under the hood we are using like multiple different libraries and packages to kind of like do all of these processes from Initiating this structure to like assembling a box and like running the simulation. But each of those has its own learning curve.

But the goal of the Flower was to put all of these in one place with like clear instructions and documentation. So a researcher who just wants to get the code running and like actually running experiments rather than spending so much time on understanding each of these packages and learning how to work with each of them individually. They can just get to the part of running the experiments and analyzing the results rather than spending so much time on building the code, actually.

And I think our target audience also could be people who are passionate about doing reproducible research, meaning that they want to share their work with everyone, everybody else in the community, and make sure that everyone can also reproduce the exact same results that they had in their papers or in their work.

[00:11:01] **Arfon Smith:** Yeah, I think what I can hear you saying is, and this one of the messages I used to try and still try and promote for research software and investing in good research software, is if you do the work to understand those abstractions of the problem, you can actually do science faster and you can repeat it more easily. And, cost per repeat of doing the experiment drops through the floor once you've got a nice set of tooling. 

Better research through better software is one of those messages that I think lots of people who learn about what can be done if you invest in good software learn that value. But you kind of have to do the work to realize the value.

And then, I don't know, it's kind of a bit of a chicken and egg problem for some people, I think, but definitely sounds like an example of creating real value for a whole bunch of researchers.

[00:11:47] **Abby Cabunoc Mayes:** So it does sound like there's a lot of open source software in the field that you're leveraging, which is really, really great to see. Are there any alternatives to FlowerMD specifically, that people could be using, and what makes this different?

[00:12:00] **Chris Jones:** So I guess in response to all the open source software tools that are out there there's definitely a lot. I think there's a lot of people in this field that care about creating reproducible open source software. For example, there are two kind of packages that we leverage very heavily.

So one's called MoSDeF or the molecular simulation design framework. And this is a package or

a group of 

[00:12:22] **Arfon Smith:** brilliant name, by the way. Sorry, I was just like, that might be the best named software package ever. Sorry.

[00:12:28] **Abby Cabunoc Mayes:** Another backronym, but

[00:12:30] **Chris Jones:** Yep. So they created packages for building molecules arranging molecules in a system, applying your force field parameters to it. And then there's another package called HOOMD-blue, which is a simulation engine that runs on GPUs.

So, there's lots of packages out there that give you bits and pieces of what you need to do, but like Marjan was saying, it's really challenging to put them all together, create a single workflow that you can use to start doing science. So that's a big part of what Flower is.

We're not trying to recreate the tools that are already out there.

There are some alternatives that do a similar kind of thing. For example there's one called Radonpy where you kind of have the same steps of going from starting with a molecule and running a simulation.

They kind of focus more on calculating properties from their simulations. With Flower, we're trying to create recipes for more complex workflows. For example, welding two chunks of polymers together, this really requires running multiple simulations. Taking the output of one simulation to build another new system, use that as the input for the next simulation and similar with the surface wetting kind of recipe we have in there where it's multiple steps of build a system, run a simulation, build a system, run a simulation.

[00:13:45] **Arfon Smith:** Interesting. Yeah. It sounds like there's a pretty rich ecosystem out there, as you say, and you're sort of gluing all these different pieces together, which sounds really useful. Side note, I think your field has some of the best named software out there. So I'm just going to now go and like try and learn some more about that.

There's clearly a high bar for naming software packages in your area which I appreciate. I was wondering if I could ask, what are some of the challenges you faced when building Flower? Any problems you encountered that you didn't expect to?

[00:14:12] **Marjan Albooyeh:** I think the design phase of our project was probably the most challenging one. I remember we had to kind of like iterate over the design of our base modules a couple of times. And the reason for that was We kind of wanted to accommodate all of different projects that might come in the future.

Not only our projects because we were thinking about, okay, we can build this module for initiating the molecules in this way that works for our projects. But then we had to kind of come up with like an imaginary user who in the future might want to use this in a different way. Maybe they already have parts of their structure built.

But can they, use FlowerMD in the middle step of, like, getting the simulation running? So, yeah, we had to come up with these different scenarios, then, and how can our design kind of, like, accommodate that. And we also wanted to keep it simple, especially the API. We wanted to keep it as simple as possible so people can just look at the parameter names and they just understand what it does and it's clear enough for them, they don't have to go through the code and understand what each parameter does.

So it was a trade off of being flexible enough to serve different projects but at the same time be simple enough for people who might not have a strong background in like computer science or programming. So I think that was the challenging phase of our project. We spent quite a lot of time just designing the main modules without even coding, just like talking about it, but then we code it and then we say, oh no, this is not good enough, we should do it again.

Yeah, so after that phase, I think the rest of the challenges was making sure that we are following like best software development practices. We added unit tests, integration tests, making sure that all of our functionalities also work in bulk simulations, not just, like, the toy models that we were, like, working with.

Yeah, those are mostly the challenges that I think every software engineer might face during the production.

[00:16:18] **Arfon Smith:** Yeah, it sounds like you have a classic problem there, which is the balance between usability and sort of feature completeness. And finding those right abstractions is often a big part of the discovery process building tools.

[00:16:30] **Abby Cabunoc Mayes:** So how can people get started using your package?

[00:16:33] **Marjan Albooyeh:** So we made sure that our package is installable through conda. So if people are familiar with conda, they can just get our software from conda-forge and start working on it. We try to make it as seamless as possible. So you don't have to install a lot of requirements Just FlowerMD should be fine.

And we also added a couple of tutorials in form of Jupyter Notebooks to our repository, basically like going through the basic functionalities of FlowerMD line by line with some text description of how it works and what each of the classes in the FlowerMD package can do.

And the tutorials that we made, we ordered them in a way that starts with, like, basic functionalities so we don't scare people off and with the complexity, and then slowly adding more complex features and how they can use these building blocks that we introduced to start their own projects or run the simulations that they want.

And we also made sure that we have good documentations. We wrote Docker strings for all of our functions and everything is available in our repository. And we are very happy to answer any questions. If anybody wants to start using this project, they can just start an issue on GitHub and we would be happy to help them to get started.

[00:17:54] **Abby Cabunoc Mayes:** I love that. Yeah, it sounds like you put a lot of work into making it really easy for people to use this, so thank you.

[00:17:59] **Arfon Smith:** Yeah, I was actually just looking at the JOSS review, and it looks like you, your review was in, like, two months from submission to being accepted, which is very fast. Our average is actually about a hundred days but still, two months is quite great. And often those packages that go fast are the ones where people have got a really nice software package where they've basically done everything that we would already want you to do, so people just whiz through the review.

I was curious if you have anything to say about the JOSS experience? Did you know upfront you were thinking about submitting to JOSS, curious how you learned about the journal, why you submitted there, anything you'd like to say about that experience would be fun to hear about.

[00:18:39] **Chris Jones:** Yes, we decided to submit to JOSS because we wanted to write a paper where we talked about the problems that we were trying to solve and just focus on the features and the software. We weren't trying to publish results of these simulations or anything like that.

So we just wanted to get this, the software design out there and talk about our motivation for designing the software package and what problems it was solving.

So I think JOSS is a great place for that, where you can just focus on the software, not necessarily the tasks that it's designed to do and start talking about results and things like that. 

[00:19:11] **Marjan Albooyeh:** Yeah. And I think we kind of love the JOSS review process as well. It was kind of seamless and easy.

Everything was clear. Everything was happening through GitHub so we could actually communicate with our reviewers unlike other journals that you never have a channel to talk to reviewers and everything is like so formal. But in JOSS the great thing was we were able to we could actually talk to reviewers, they can tell us whether they were able to run the code without any problems, and then going through the next step of the review.

So that's, I think, what made the JOSS review process kind of easy for us, and I hope for the reviewers as well.

[00:19:52] **Arfon Smith:** Yeah. Our tagline is a developer friendly journal. So hopefully that resonated for you. It sounds like it. It was a good fit.

[00:19:59] **Marjan Albooyeh:** Yeah. 

[00:19:59] **Abby Cabunoc Mayes:** And what did you learn by going through the JOSS review process?

[00:20:03] **Marjan Albooyeh:** Yeah, the JOSS review process was quite easy for us. We, because we knew that the reviewers are going to run our code, so we had to make sure we have tutorials and a running examples before we submit. So that was the requirements that we put for ourselves and it was a good way to test our software with the reviewers who never worked on this field necessarily.

And the interesting thing that happened during the review process was by the time of the submission we only had one recipe on FlowerMD, and that was the, the polymer welding example. But in the paper, we mentioned that FlowerMD could be used for another processes, like surface wetting, where you, like, actually put, a droplet on the surface, and you see how it expands.

And one of the reviewers suggested that, oh, it would be nice to have this in your package, as you mentioned in the paper. And we were like, maybe we should try it. And because of the design choices that we made, we were able to build this surface vetting module during the review process, relatively fast, it just took us like a couple of days with testing and everything.

And we were able to merge it before the review process finishes. And I think that was a good example of this sort of like review process that the reviewer asked us something and we said, okay, let's do it. And we did it. And they were able to see the results before accepting.

[00:21:30] **Arfon Smith:** Super cool.

[00:21:30] **Abby Cabunoc Mayes:** That's amazing.

[00:21:31] **Arfon Smith:** Nice story. So how can others join in and contribute to this package? Is it writing new recipes extending core functionality? What kind of contributions are you looking for Flower?

[00:21:42] **Chris Jones:** I think either one of those would be great. I think the main thing right now is just if there are new researchers or experienced researchers out there that might be starting a new project the best way to help is just to try to come use FlowerMD and see if it works for your use case. If there are any issues you run into, open an issue on the GitHub page.

But yeah, specifically, FlowerMD is far from what we envisioned as a finished package. Cause like the name suggests it's a library of recipes and right now we only have two. So yeah, if someone has some project, I would definitely encourage them to at least maybe at first just come give Flower a try, see if you can leverage kind of the design mod and modules that we have in there in these base classes that we use and see if you can design your workflow from there.

And then, if it works out okay, then make a PR to contribute your workflow to the library.

[00:22:33] **Abby Cabunoc Mayes:** And just a real quick follow up, what skills does someone need to know to create a recipe, or what languages would they have to know?

[00:22:39] **Chris Jones:** So Flower is completely written in Python. The simulation engine we use HOOMD-blue is written in C++ and runs on GPUs and has a very nice Python API. That's one of the reasons we decided to use it as the engine in our package. So you don't have to know C++ or CUDA or anything like that.

It's just purely Python. And we think we designed the base classes in a way that it does not really require any like advanced coding skills to start writing a recipe and make a PR for one. 

[00:23:09] **Marjan Albooyeh:** Yeah, and we would be happy to help through the process if someone wants to contribute, they can open the PR, and we're definitely going to review it and give them feedback or help them with building the code.

[00:23:20] **Abby Cabunoc Mayes:** That's great. So what's the future of Flower? What's next?

[00:23:24] **Marjan Albooyeh:** So the future for FlowerMD, I think, as Chris mentioned, it would be really nice to see other researchers using it and start adding new functionalities to it or adding their own recipes. That's how, I guess, the Flower blooms. So, yeah, I think that would be the best use case for FlowerMD in the future.

And the other thing is, I think we both love to see it as a platform that people who are working on similar projects can use and share their results. So it would be easier to get the same results on FlowerMD getting like reproducible results. So we are hoping to gather a little community of researchers who are working in this field with FlowerMD.

[00:24:08] **Arfon Smith:** Yeah, it does seem like there's a great opportunity to build community around this software, especially the way that you've designed it for that extensibility. So that's really nice. And I wish you good luck with that. And so, just to wrap us up, like, how can people find you both online? What's the best way to keep up with your work?

[00:24:25] **Chris Jones:** So for me it'd probably be GitHub. I'm not active on Twitter or anything like that. So yeah, my GitHub username is @chrisjonesBSU. I'm sure the link for flower will be in the show notes. It's the cmelab/FlowerMD on GitHub. Yeah, so, people can feel free to open issues on there if they wanna discuss it or reach out to me via email or something like that.

[00:24:45] **Marjan Albooyeh:** Yeah, I think they can check out the. Flower MD GitHub page. We are releasing new versions every couple of weeks or a few months. I think that's the best way to keep up with the package.

And you can also follow my work through my GitHub page. Yeah, it's my first name and my last name. And you can also check out other projects in the CME lab that we are working on. We have a couple of other cool packages for the similar use cases that people can check out.

[00:25:12] **Arfon Smith:** Awesome. That sounds easy. And I'm sure people will do that. So thank you so much for your time today. It's been really fun to meet you both and learn about the work you're doing here. And I just wanted to say thanks for taking time to be part of the JOSSCast and telling us about FlowerMD.

[00:25:28] **Chris Jones:** Yeah, of course. Thanks for having us. Thank you.


[00:25:32] **Abby Cabunoc Mayes:** Thank you so much for listening to Open Source for Researchers. We showcase open-source software built by researchers for researchers. You can hear more by subscribing in your favorite podcast app. 

The Journal of Open Source Software is a community-run journal relying on volunteer effort. If you'd like to support JOSS, please consider making a small donation to support running costs at numfocus.org/donate-to-joss that's N U M F O C U S .org/donate-to-joss. 

Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mays, edited by Abby and music CC-BY Boxcat Games. 



[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/cs8NqkzgTeU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>