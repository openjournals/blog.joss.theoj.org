---
layout: post
date: 2024-05-02 00:00 -0400
title:  "JOSSCast #9: Reproducibility in Neuroscience – Mats van Es on FieldTrip reproducescript"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Reproducibility-in-Neuroscience--Mats-van-Es-on-FieldTrip-reproducescript-e2isb03" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)

Mats van Es joins Arfon and Abby to discuss reproducible science and the functionality he added to FieldTrip, a MATLAB software toolbox for analyzing brain imaging data.

Mats is a cognitive neuroscientist at the University of Oxford.

You can follow Mats on Twitter/X [@mats_van_es](https://twitter.com/mats_van_es).

### Episode Highlights:

- *[00:03:11]* Introduction to FieldTrip and reproducescript
- *[00:06:30]* Config-Driven Science & Reproducibility
- *[00:11:42]* Using MATLAB in Open Source Software
- *[00:21:02]* The State of Open Source Software in Neuroscience
- *[00:21:53]* Publishing in JOSS
- *[00:23:35]* Future Directions and Contributions

### Links:

- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05566](https://joss.theoj.org/papers/10.21105/joss.05566) 
- FieldTrip repository: [https://github.com/fieldtrip/fieldtrip](https://github.com/fieldtrip/fieldtrip) 
- OHBA Software Library  or OSL [https://github.com/OHBA-analysis/osl](https://github.com/OHBA-analysis/osl) 
- OSL Dynamics [https://github.com/OHBA-analysis/osl-dynamics](https://github.com/OHBA-analysis/osl-dynamics) 
- Mats on Twitter/X @mats_van_es [https://twitter.com/mats_van_es](https://twitter.com/mats_van_es)
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))
- [Donate to JOSS](https://numfocus.org/donate-to-joss)

### Transcript:

[00:00:05] **Arfon Smith:** Welcome to Open Source Researchers, a podcast showcasing open source software built by and for researchers. My name is Arfon.

[00:00:12] **Abby Cabunoc Mayes:** And I'm Abby, sorry I forgot that part

[00:00:14] **Arfon Smith:** Very good. And we're your hosts. Is it coffee or tea you've got in there?

[00:00:18] **Abby Cabunoc Mayes:** This is water. Yeah.

[00:00:20] **Arfon Smith:** Okay, 

[00:00:21] **Abby Cabunoc Mayes:** Boring. 

Yeah. 

[00:00:22] **Arfon Smith:** of tea. Every other week we interview an author published in the Journal of Open Source Software.

This is episode nine, and today we chatted with Mats van Es about his paper, Reducing the Efforts to Create Reproducible Analysis Code with FieldTrip. And Mats is a cognitive neuroscientist at the University of Oxford. 

[00:00:40] **Abby Cabunoc Mayes:** I really enjoyed this focus on reproducible science and just hearing why it's important in neuroscience, and it is important for all of science, how he was tackling that through reproducescript, and how he saw this as a model for other researchers to see best practices for reproducibility.

[expand]

[00:00:56] **Arfon Smith:** Yeah, I agree. Reproducibility I agree is incredibly important. I'll share that one thing that kind of bugs me about reproducibility sometimes is reproducibility for reproducibility's sake. I think there should be a purpose to working reproducible, reproducibly. There we go. Came out eventually.

And so that reproducibility can be, of course, being able to redo your work again share more easily, be more transparent when you publish. But I think cause he's grown up as a researcher that's had to learn to code to do their work, I got this really strong sense from him that he understood the problems that people really have as a neuroscientist using these tools and has built the tools that he needs to work more effectively, which is really cool. It's a really good way of building useful tools. If you solve your own problem first. 

[00:01:48] **Abby Cabunoc Mayes:** I also liked hearing a bit about FieldTrip and just having such a widely used piece of software among neuroscientists. It was cool just to hear more about it.

[00:01:56] **Arfon Smith:** Yeah, for sure. FieldTrip sounds like an incredible community. But it also sounds like he's trying to write a Python version. So probably might have him back on in a few years time when we are still podcasting.

[00:02:07] **Abby Cabunoc Mayes:** Yeah, yeah, of course.

[00:02:10] **Arfon Smith:** It was interesting to have a MATLAB submission. So we talked a little bit about that and proprietary runtimes and open source software. But yeah, I thought it was it was a very interesting conversation.

[00:02:19] **Abby Cabunoc Mayes:** Cool. Yeah, let's play it.

[00:02:21] **Arfon Smith:** Let's go!

Welcome to the podcast, Mats.

[00:02:23] **Mats van Es:** Thank you very much and thanks for inviting me.

[00:02:25] **Arfon Smith:** Of course. So Mats, you're a cognitive neuroscientist at the University of Oxford, I think. Is that right?

[00:02:30] **Mats van Es:** That's correct. Yes. I did an undergrad in biophysics and then a master's and PhD in cognitive neuroscience. And I've been I've been a postdoc in Oxford for about three and a half years now.

[00:02:42] **Arfon Smith:** Very nice. And how is Oxford today? Is it spring springing or has it gone cold again like it is up here?

[00:02:47] **Mats van Es:** I wish it was spring. No, it's quite cold and wet. Exactly what you expect from England.

[00:02:55] **Arfon Smith:** Fair enough. Yes, I agree. Well, there

[00:02:57] **Abby Cabunoc Mayes:** Same here in Toronto.

Very slushy.

[00:03:01] **Arfon Smith:** It's raining and cold in Scotland as well, so there we go. Anyway so yeah, well thanks for coming on. So tell us about FieldTrip and the project. Tell us about what this project does and why you started it.

[00:03:11] **Mats van Es:** So FieldTrip is a MATLAB software toolbox for the analysis of Magnetoencephalography data and electroencephalography data. So this is like brain imaging data. And it has been around since about 2011. And it's basically a collection of functions for analyzing your neuroimaging data. Initially it started as basically just some colleagues at the Donders Institute in the Netherlands sharing scripts for analyzing data that at the time was quite new.

And people were kind of figuring out how to analyze these data because they're quite complex. And it's, it can be quite difficult to kind of, tear structure out of this data. So that's how it started. And then at some point they developed a toolbox out of it for other people to use outside of the local institute.

And this has been a great success. I believe the main paper has been cited over 4, 000 times and is being used in hundreds or maybe even thousands of labs in the world. And yeah, it really helps a lot of people to analyze that data. 

What we try to do is actually an addition into this toolbox called reproducescript. Because we noticed that a lot of users of FieldTrip, they create their own scripts out of specific FieldTrip functions. And these scripts, they can become quite complex. Typically cognitive neuroscientists are not trained in programming. So there's a lot of variability and a lot of complexity in a lot of these scripts.

And we noticed just at the institute that a lot of the code that our colleagues and maybe ourselves were writing was really hard to reproduce. And I had played around a little bit with MATLAB function called diary, which basically saves all the commands that you write into the command window.

And that was basically the beginning of reproducescript. . So this is basically an addition that you add to your script. When you're using FieldTrip, and it's only a few lines of code, but when you add that, then basically FieldTrip creates a very generic analysis script out of everything that you're doing.

With the intermediate data. And that means that in the end, after you've done your analysis that might be coming from quite complex scripts, you also have a script and intermediate data that you can upload or share with colleagues. And they can just basically run your entire analysis pipeline with one click on the button. 

[00:05:50] **Arfon Smith:** This sounds almost like a sort of a debug log of the analysis run. Is that the right way to think about it? I mean, maybe debug's not quite the right thing, but it's like a verbose sort of version of every step that was taken with the FieldTrip toolbox and sort of capturing state at each point in the analysis.

Is that how to think about it?

[00:06:11] **Mats van Es:** Yeah, that's correct. I think a lot of people when they write scripts and functions themselves, everything ends up in different MATLAB scripts. And so there's all these complex dependencies at the end, and we try to get rid of all those dependencies, so you just have like one big script that does everything.

So it's, makes everything very serial.

[00:06:30] **Abby Cabunoc Mayes:** Yeah, I think one of the big reasons why this paper stuck out to me when I was looking through the recently published stuff was first, that FieldTrip was so popular and widely used. Then second, how you're really focusing on reproducibility and just making it easier for other scientists to reproduce that.

So if I understand correctly the researcher would just write a config file with all the different steps, and then reproducescript would create this script in a standard format so that other people can just easily use it. Is that, is that

[00:06:59] **Mats van Es:** Yeah, yeah, that's correct. And this configuration file that people write, usually you would write one configuration for one specific analysis step. So you might think of data cleaning as one analysis step, and maybe spectral analysis is one analysis step. So you have different configuration structures for every function. And all of these together are then, by reproducescript, put into one big script.

[00:07:29] **Arfon Smith:** It sounds like a really cool project and reproducibility, I think is something that's near and dear to many people's hearts, even for just yourself you know, making it easier to redo your own work can often be a real challenge, right? You go back to look at something you did a year ago and you're like, yep, I don't know how that worked. So this is good.

I was curious to learn a bit more about this. I think you said, did you say diary function in MATLAB? So it's like some kind of history kind of thing. Is that true? Is that I've never heard of that. I'm curious to learn a bit more about, I guess, how much you're just reusing what the language supports already and how much work you had to do with the reproducescript functionality. How much you're just leveraging this sort of capability that language has versus like writing lots of code yourself.

Could you say a bit about that?

[00:08:15] **Mats van Es:** Yeah, I think most of it is actually code that we've written. It's only, I think, that the MATLAB inherent diary function was the inspiration for this. Because the MATLAB diary only captures everything you put in the command window. But reproducescript captures everything that is happening in functions, even if they don't have any outputs to the command window.

So, FieldTrip makes use of a set of functions called the preamble and the postamble. And these are used at the beginning of each script and at the end of each script. Or sorry, FieldTrip function. And this is basically keeping track of all the data bookkeeping versions and making sure everything runs smoothly.

And this is then also where the reproducescript functionality happens.

[00:09:03] **Abby Cabunoc Mayes:** Well yeah, thanks for that. I haven't touched MATLAB in 20 years, I realized. I was just thinking back. It's like, oh, I didn't even know about this diary function. But I'd love to hear a bit more about reproducibility and why this matters so much for neuroscience.

[00:09:16] **Mats van Es:** Open Science is great, and sharing scripts is great, but if it's only that, then sometimes there's still a lot missing right? For example, the case not trained at writing code, which is still the case for me. And as you said before, sometimes I'm also like angry with my previous self for not documenting my scripts better.

And in the past, maybe five years or so It has become obvious that in large parts of psychology, but also large parts of neuroimaging and neuroscience, there is a lack of reproducibility. Of course, we all know that the incentives for publishing exciting results are not always in line with doing solid science.

And yeah, so we wanted to improve this reproducibility and make it easier for people to make their analysis reproducible. More and more funders now are requiring you to upload code and data when you publish a paper. But often either people upload their code and it might not work, or they're very nervous about sharing that code because it looks a bit ugly or they will only send it to someone when they request it, and then still, it might be really hard to actually get that code to work.

So that's why we envisioned a functionality that was really easy to use, and if people are already using FieldTrip, it doesn't require any more training besides maybe doing a five minute tutorial. 

[00:10:51] **Arfon Smith:** Yeah, I think the reproducibility, I mean, I think it's called a crisis in many areas. And I think people will probably be aware of that.

I think it's a really important problem for all areas of research to be aware of, and I think some areas probably have to work harder than others on addressing that.

I think good software practice is one of the tactics that we should strongly favor. Good software and open source software is a good way of thinking about how to at least solve some of that problem. What's it like working on open source software in a proprietary language like MATLAB?

Does that cause you any problems day to day? I was curious. Also, I think there's a language called Octave as well, which is like an open source version. I was curious if this runs on Octave or whether user has to have a MATLAB license to use FieldTrip and also to use, therefore, I guess, reproducescript.

[00:11:42] **Mats van Es:** Yeah, as far as I know you can use FieldTrip with Octave but personally, I've never done so because I've always had MATLAB license. The reason why we use MATLAB is mostly historic. I think Python wasn't really as big as it is now like 10, 15 years ago. And there are some benefits with a licensed software like MATLAB, as in it gives you a large set of base functions that are already there. 

It's relatively robust. But it is a bit tricky if you don't have a license. That is true. Every year there's a a FieldTrip toolkit organized at the Dundas Institute. So people are also actively trained in using the software and using the analyses. And every year there are a few people that say that at their home university, they don't have a MATLAB license, what to do now? So yeah, in that respect, it can be a bit annoying. And it would be great if we can kind of go away from that model.

[00:12:43] **Arfon Smith:** Cool. Okay. Thanks.

[00:12:44] **Abby Cabunoc Mayes:** I didn't even know about Octave, so this is enlightening

[00:12:46] **Arfon Smith:** There you go. Yeah, we get this side note on JOSS. We decided very early as the journal that we would accept submissions where the runtime was proprietary because we said the software is still open source. The runtime might not be and that's okay. I think we say something like &quot;We would prefer people use open source languages, but it's not a requirement.&quot;

[00:13:07] **Abby Cabunoc Mayes:** That's interesting. Yeah, back to reproducescript. Have you used this to look at any research problems at all, or know of any other groups that have used it?

[00:13:15] **Mats van Es:** Actually, no, so far not.

[00:13:18] **Abby Cabunoc Mayes:** Brand new!

[00:13:19] **Mats van Es:** Yeah, brand new. As in, it's been out for a while, but we haven't really advertised it as much. I wrote this basically at the end of my time at the Donders Institute, and then when I moved on, I actually made a switch to Python, which is a bit of a pity because I think there is real use in reproducescript.

The audience that we have in mind is mostly the FieldTrip user that is not very proficient in writing code and in what I would say, maybe code hygiene. I'd like to see myself as someone who's like slightly above that. So, I haven't been doing any new projects using FieldTrip in a while. And that's part of the reason why I haven't used it myself. 

But I think for especially a beginner in FieldTrip, it can be very helpful. And also outside of The FieldTrip end user, we kind of wanted to publish this work to showcase a strategy that you could use in any research fields.

But this is all specific to the FieldTrip tool toolbox. But hopefully it will get people to think a bit more about how can we. improve the reproducibility of our own analysis and our own software. 

[00:14:30] **Abby Cabunoc Mayes:** Hopefully this podcast can maybe get the word out and get a few more users of reproducescript. 

[00:14:35] **Arfon Smith:** Absolutely.

[00:14:36] **Mats van Es:** great, yeah. 

[00:14:37] **Arfon Smith:** So I think you were sort of hinting at this Mats in your last answer, but like, how do you think about config driven work? You said something about this is something that can help people who are maybe less technically competent or experienced. You know, there's sort of things that we do as software engineers that just come naturally to us, you know, maybe like use version control or think about how to structure our work.

But there's lots of people who just trying to do science, right? They're just trying to get their work done. And so do you feel like config driven science --I don't know if you like that phrase, but let's go with it for now. Like, config driven research is a really important tactic for people to do their work.

Is that like an opinion that you hold and that you want to push more on?

[00:15:21] **Mats van Es:** Yeah, I think so. I think a config is quite simple. It's a simple concept, but very broadly useful. It helps, especially, for example, a config is really easy when you're still making functions or writing functions and then they change.

And you can hide all that complexity in the one function that deals with the config. Alright, so there's only one kind of layer of complexity there. I think that's really useful. And it can also be a very kind of concise way of capturing everything that you want to do. So it's, yeah, usually I guess a config is also easier to share with colleagues and peers than just a list of verbally saying what you did.

[00:16:09] **Arfon Smith:** Yeah, for sure.

[00:16:10] **Abby Cabunoc Mayes:** Right, that makes sense. And are there any other strategies that you're adopting to improve transparency and reproducibility of your science?

[00:16:17] **Mats van Es:** Yeah, so now here in Oxford, I'm working on a software toolbox that is very similar to FieldTrip, but it's in Python. It's building on top of a toolbox called MNE-Python, which is widely used. But for our purposes, so I'm part of a methods lab. And we always like to do things our own way, and if MNE-Python doesn't have them, then we decide we have to write them ourselves.

And so that's why we're writing a software package called OHBA Software Library or OSL. We also have a config structure that we try to keep as concise as possible. So it's basically maybe 25 lines of code. that captures an entire pipeline and I think that gives you a good overview of what you've done so you can really, you don't even have to scroll through it. You can just show the config and it will clearly show you every step you've done. That also helps in sharing. 

Another thing is not really software related, but it's more looking at analysis and the way we do science because more and more in neuroscience and neuroimaging we're making use of data driven techniques coming from machine learning. And in my own research, I try to find structure in these complex data. So, for example, I'm trying to find temporal structure in when specialized brain networks activate.

But if you're using a data driven technique, then a critic could, can always say, well, you've just fitted a model to your data, and it will always give you an output. We know that what you're showing us is actually, something real and something physiological. So, in a paper that I'm trying to publish now, I've applied the same methods to five independent data sets and show that all the results replicate over all of those data sets.

And that's another way to kind of think about how can I really show that the science that I do and the results that I show reproduce and are robust.

[00:18:26] **Abby Cabunoc Mayes:** Oh, that's super interesting. Yeah, if you can share the links, especially to the software, the Python software you were mentioning earlier, we'll be sure to include that in the show notes. People can check it out if

[00:18:35] **Mats van Es:** Ah, brilliant.

[00:18:36] **Abby Cabunoc Mayes:** a neuroscientist jumping to Python.

[00:18:38] **Arfon Smith:** Yeah. Very good. So I have a sort of bit of a meta question about just you and your experience. Like, how did you get into open source software? Could you say a little bit about what the sort of origin story of you contributing open source 

[00:18:53] **Mats van Es:** Yeah, so I did my PhD, my master's and my PhD at the Donders Institute, where FieldTrip Toolbox was initially written. And the people who trained me during my PhD, including my PhD supervisor, are the main developers of the FieldTrip Toolbox. So it was kind of very naturally ingrained in me that this was important.

And yeah. So this project was also part of my PhD where I was also kind of expected to contribute to the development of the FieldTrip Toolbox. But it also, in a way, came a bit more natural by sometimes asking people, &quot;Oh, can I have your code to try this on my data?&quot; And then it's very frustrating to actually make that code work if it doesn't immediately.

Often there's just so many dependencies, both on different toolboxes that you might have locally installed and on complex scripts and directory structures that it's just so hard sometimes to, yeah, use somebody else's code. So that really kind of empirically gave me the observation, well, it's really important that we make sure that we can do this easily.

And I think I'm quite a good person to try and kind of develop these methods because I myself am not formally trained to do any programming. And I work with people that have less experience in programming and with people that are formally trained in programming. And it's kind of good to sit there in between and understand the challenges of everybody who doesn't have a doctorate in computer science.

[00:20:26] **Arfon Smith:** Yeah. No, that makes a ton of sense. I think you can see the challenges that your peers would face because you've come up not through a software engineering track. That makes sense. I had a sort of little bit of a follow up on that as well , and this is probably a very hard question to answer. 

But relative to other research areas, what's the state of open source software in neuroscience? Is it well developed? Is it still sort of weird and new? It sounds like your supervisors for your PhD were like, you will do this because we're doing it. So that was easy. But are they unusual? Like what's the sort of state of open source software in your discipline?

[00:21:02] **Mats van Es:** It's getting better, but there's definitely room for improvement. So I think the closer you are to people actively developing open source software, the more likely you are to share your own code and your own data. But generally speaking, there's still a lot of papers that say, If you want my code or my data, you have to email this email address. which 

[00:21:26] **Arfon Smith:** Code available on request.

[00:21:28] **Mats van Es:** Exactly exactly.

But it's definitely moving in a good direction. There's nowadays also more people that are switching to Python which I think also helps in making everything more transparent. So yeah, we have a long way to go, but we're on the right track. I think.

[00:21:48] **Arfon Smith:** Nice. That's great to hear. 

[00:21:49] **Abby Cabunoc Mayes:** That's great. Yeah, just to switch gears a little bit, why did you decide to publish in JOSS?

[00:21:53] **Mats van Es:** So I guess part of it was curiosity. It's a very different model of publishing your work compared to a traditional paper. Where here the GitHub repository is the first priority really. So that's one. And then also it seemed like quite a natural fit, because as I started talking about reproducescript, open science and reproducibility are very closely interlinked.

So we thought that JOSS would be a really good platform to talk about reproducibility.

[00:22:26] **Arfon Smith:** Did it go okay? I actually don't remember the review. I know the paper took a while to go through a review, so sorry about that. Hopefully that was okay. Did the review go okay from your perspective?

[00:22:36] **Mats van Es:** Yeah, I mean, there were some challenges. So one of the challenges was that when I started working on reproducescript, I was new to git and GitHub which meant that my local git was a big mess and in the end, rather than pushing all my commits to the FieldTrip Toolbox myself, I still basically copied and pasted codes and gave it to my supervisors and then they put it in the FieldTrip toolbox.

And in the end, when we tried to publish this in JOSS, initially there was a question of whether I had done anything at all, because I was completely absent from the GitHub repo. So yeah, that was a bit frustrating, but it all worked out in the end.

[00:23:22] **Arfon Smith:** Very good. Yeah, I can imagine somebody will have spotted that, so we do look at the commit history to see if you're publishing something that you should reasonably be able to publish.

[00:23:30] **Abby Cabunoc Mayes:** Yeah, so, how can people contribute to reproducescript? What kind of skills do they need to help you out?

[00:23:35] **Mats van Es:** I think even if they don't have any programming skills but they have ideas of how to improve it or they may be using FieldTrip and they have tried reproducescript, opening a issue in GitHub or sending an email to the FieldTrip mailing list is always a good idea to share your thoughts or to send a piece of code that you think might improve it.

So either GitHub or through the FieldTrip mailing list.

[00:24:01] **Abby Cabunoc Mayes:** Nice.

[00:24:02] **Arfon Smith:** Good.

[00:24:03] **Abby Cabunoc Mayes:** I know you mentioned some of the other projects you're working on, but is there any other open source software you're currently working on?

[00:24:08] **Mats van Es:** Yeah, yes. So, at the lab in OHBA in Oxford, we're also building software for analyzing electrophysiology data. One is similar to FieldTrip but based in Python. It's called OSL. And this can be found on GitHub on the OHBA, that's O H B A Analysis page. And then there's one called OSL Dynamics, which is about generative modeling of brain data, which can also be found at the same GitHub page. 

[00:24:39] **Abby Cabunoc Mayes:** Just to close this off, how can others find you online, and, oh, will you be presenting this work anywhere? Perhaps?

[00:24:47] **Mats van Es:** Yes, yes I will. So, online, I guess Twitter is the easiest. That's mats, M A T S, underscore, van, underscore, E S. And I will, presenting this work specifically at the Biomag Conference in Sydney, Australia at the end of August and I will also go to the conference of the Cognitive Neuroscience Society in Toronto next month in April.

[00:25:14] **Abby Cabunoc Mayes:** Hey, say hi when you're here! 

[00:25:16] **Mats van Es:** Will do! 

[00:25:16] **Abby Cabunoc Mayes:** That'll be fun.

[00:25:17] **Arfon Smith:** Cool. Hey, yeah. Okay. So Mats, thank you so much for coming on the podcast today to tell us about your software. This sounds like a really cool project. I love its origin story. It sounds like you're doing a bunch of really interesting and exciting work. And thanks for sharing your time with us today.

[00:25:33] **Mats van Es:** It was my pleasure.

[00:25:34] **Abby Cabunoc Mayes:** Thank you so much for listening to Open Source for Researchers. We showcase open-source software built by and for researchers, you can hear more by subscribing in your favorite podcast app. 

The Journal of Open Source Software is a community-run journal relying on volunteer effort. If you'd like to support JOSS, please consider making a small donation towards running costs at numfocus.org/donate-to-joss. That's N U M F O C U S.org/donate-to-J O S S. 

Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes. Edited by Abby and music CC-BY Boxcat Games. 


[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/DP-EJsYbNV0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>