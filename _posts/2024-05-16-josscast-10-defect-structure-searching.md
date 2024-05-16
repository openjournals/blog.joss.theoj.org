---
layout: post
date: 2024-05-16 00:00
title:  "JOSSCast #10: Defect Structure Searching – Irea Mosquera-Lois and Seán Kavanagh on ShakeNBreak"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Defect-Structure-Searching--Irea-Mosquera-Lois-and-Sen-Kavanagh-on-ShakeNBreak-e2jnaqn" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)

Irea Mosquera-Lois and Seán Kavanagh join Arfon and Abby to discuss releasing software based on [important research observations](https://doi.org/10.1016/j.matt.2021.06.003), earning a PhD, and building ShakeNBreak, a defect structure searching method that better identifies low-energy structures.

Irea is a PhD Student at Imperial College London. Seán is an Environmental Fellow at Harvard University.

You can follow Irea on GitHub [@ireaml](https://github.com/ireaml) and X [@ireaml](https://twitter.com/ireaml). You can follow Seán on GitHub [@kavanase](https://github.com/kavanase), X [@Kavanagh_Sean_](https://twitter.com/Kavanagh_Sean_), and at [seankavanagh.com](http://seankavanagh.com/).

### Episode Highlights:

- **[00:03:02]** What is a viva? And earning a PhD
- **[00:05:41]** Defects in Materials and Their Impact
- **[00:07:20]** Understanding ShakeNBreak
- **[00:09:32]** Integration with Computational Tools
- **[00:12:46]** Benefits of Open Source Contribution
- **[00:17:20]** Discovering the Defect Configurational Issue
- **[00:20:23]** Peer Review and Publishing Software
- **[00:22:41]** Contribute to ShakeNBreak

### Links:

- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.04817](https://joss.theoj.org/papers/10.21105/joss.04817)
- ShakeNBreak repository: [https://github.com/SMTG-Bham/ShakeNBreak](https://github.com/SMTG-Bham/ShakeNBreak)
- Mosquera-Lois, I. & Kavanagh, S. R.; Walsh, A.; Scanlon, D. O.[ Identifying the Ground State Structures of Defects in Solids](https://www.nature.com/articles/s41524-023-00973-1), npj Comput Mater 9, 25, 2023
- Irea on ([GitHub](https://github.com/ireaml), [Twitter/X](https://twitter.com/ireaml))
- Seán on ([GitHub](https://github.com/kavanase), [Twitter/X](https://twitter.com/Kavanagh_Sean_), website: [seankavanagh.com](http://seankavanagh.com/))
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))
- [Donate to JOSS](https://numfocus.org/donate-to-joss)

### Transcript:

[00:00:05] **Abby Cabunoc Mayes:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by and for researchers. My name is Abby.

[00:00:11] **Arfon Smith:** And I'm Arfon.

[00:00:12] **Abby Cabunoc Mayes:** And we're your hosts. Every other week, we interview an author published in the Journal of Open Source Software or JOSS.

This is episode 10. We made it to the double digits.

[00:00:20] **Arfon Smith:** That's very exciting.

[00:00:21] **Abby Cabunoc Mayes:** Yeah, today we had a chat with Irea Mosquera and Seán Kavanagh about their paper ShakeNBreak: Navigating the Defect Configurational Landscape. Irea is a PhD student at Imperial College London and Seán just became an environmental fellow at Harvard University.

[00:00:36] **Arfon Smith:** So second podcast about defects. Defects are important though. We talked about this software that helps, I guess, pre sort of seed computational chemistry calculations, so it sort of sets up the configurations. Sounds like it's pretty important for helping actually truly explore the sort of properties of these materials, and then some nice tooling to help extract and manipulate the results that come out from the experimental runs.

[expand] 

Sounds like a really nice piece of software. Also, excellent name, which I only fluffed once, I think I only heard myself fluff

[00:01:11] **Abby Cabunoc Mayes:** Shake and

[00:01:12] **Arfon Smith:** Shake and bake, ShakeNBreak. Maybe I got it wrong a couple of times. I only heard myself say it wrong once. What about you? Did you find this one interesting?

[00:01:20] **Abby Cabunoc Mayes:** Yeah, no, I found it really interesting. And I think knowing that this group had done research to find how general this problem of finding these low energy defects was, and then they created this potential solution with ShakeNBreak to help with that. So it was a nice pairing of releasing reusable open source software together with an actual research output.

[00:01:41] **Arfon Smith:** Yeah. A good origin story. Good backstory. We talked about vivas.

[00:01:45] **Abby Cabunoc Mayes:** We did.

[00:01:45] **Arfon Smith:** We talked about the process of earning a PhD. And how that can be scary. And some of us have scar tissue for that still. 

So, are we going to do more defects after this or do you think we've had enough for now? Do you have any thoughts on that?

[00:01:57] **Abby Cabunoc Mayes:** All defects, all the time! This will become a defect podcast.

[00:02:01] **Arfon Smith:** 24 7. Yes. Yes. Actually, this is how it happens. I mean if somebody's interested in sponsoring us to be a defects only podcast, I'd at least entertain that idea. Seems unlikely at this stage, but

[00:02:14] **Abby Cabunoc Mayes:** Who knows.

Well, let's play the interview.

[00:02:17] **Arfon Smith:** let's do it.

[00:02:17] **Abby Cabunoc Mayes:** Irea and Seán, really great to meet you. Welcome to the podcast.

[00:02:20] **Seán Kavanagh:** thanks for having us.

[00:02:21] **Irea Mosquera-Lois:** Yeah, thank you.

[00:02:22] **Abby Cabunoc Mayes:** Yeah, glad to have you here. Do you want to tell us a little bit about yourself? 

[00:02:25] **Irea Mosquera-Lois:** Yeah, um, I'm a PhD student at Imperial College in London, in the group of Aron Walsh, and we mainly work on modeling defects. 

[00:02:34] **Seán Kavanagh:** So I'm an environmental fellow at Harvard now. So I just finished my PhD, which was split between two research groups in London. So one in the same group as Irea in Imperial College, and then also with Professor David Scanlon in UCL, also in London. And again, working on similar applications.

So, defects in energy materials is the main focus.

[00:02:55] **Abby Cabunoc Mayes:** Nice. Well, congratulations on finishing the PhD. That's a big milestone.

[00:02:59] **Seán Kavanagh:** very much. Exactly, yeah, four years. 

[00:03:02] **Abby Cabunoc Mayes:** Yeah. 

[00:03:02] **Arfon Smith:** Do you feel like you earned it? I don't know. Certainly in the UK, there's a viva and I feel like at the end of that, you feel like you earned it or I certainly did . Do you have that? 

[00:03:11] **Seán Kavanagh:** Yeah, I think so. I think in some ways it's a bit anticlimactic is what people always say about like the particularly the viva because I mean, for me, the main thing was submitting the thesis, which is like months ahead where you've actually done the work of writing because that's the worst part.

I think then you're done with it and then like the viva and all that is just kind of formalities afterwards. So I think the main celebration was like months ago rather than like just recently. But yeah,

[00:03:35] **Abby Cabunoc Mayes:** Wait, what, what is this word that

[00:03:37] **Seán Kavanagh:** Oh,

the viva, yeah,

[00:03:39] **Abby Cabunoc Mayes:** never heard 

[00:03:40] **Seán Kavanagh:** yeah. this is also something I'm starting to learn now in Harvard here with, yeah, because the whole system is very different here. So we call it the viva, which is like the defense, the thesis defense where you have to like go up and yeah. 

But then the system is so different because in the UK it's usually behind closed doors and so it's just a couple of hours of questions with your examiners who've read your thesis before whereas here I think it depends on the department but here it seems to be that you present this big long presentation to the public and then there's a few questions from examiners and that's it whereas yeah so the whole kind of way it's done is a bit different as well.

[00:04:14] **Abby Cabunoc Mayes:** Thank you for that.

[00:04:15] **Arfon Smith:** You generally know how serious your viva is going to be by whether the external assessor has booked a return train ride home already.

[00:04:24] **Seán Kavanagh:** yeah,

[00:04:25] **Arfon Smith:** because if they haven't then you might have problems because it could be like five hours or something.

So there's all these horror stories, two to three hours of intense questioning, often at a whiteboard. 

[00:04:35] **Seán Kavanagh:** Yeah,

[00:04:36] **Arfon Smith:** Yeah, I don't know. It's a rite of passage, I think. Irea, your viva be like that at UCL? I guess it would be, right? Is that, oh, sorry, are you at Imperial or UCL? I've forgotten.

[00:04:45] **Irea Mosquera-Lois:** years, yep.

[00:04:50] **Arfon Smith:** my worst enemy, to my worst enemies, honestly. Anyway, back to defects. This is our second conversation about defects of late. I was wondering if you could give us just a quick recap on. What they are, why they matter, what may be the particular interest that you both have in this subject area and also, by the way, awesome software name ShakeNBreak. uh, I'm always happy to see software with a pun name, so, most welcome here.

[00:05:15] **Irea Mosquera-Lois:** I guess we're interested in defects because they control the properties of most functional materials. So whether this is for solar cells or batteries or thermoelectrics, so most clean energy applications that you can think of, defects are quite important. So yeah, that's why we were interested in modeling them and trying to predict how they affect the properties and maybe, yeah, a material could be good for certain applications depends a lot on which defects are present there.

[00:05:41] **Abby Cabunoc Mayes:** Yeah, and we heard a great summary from Jimmy Shen episode 7, so if anyone listening hasn't heard that, you can jump back there and hear a little bit more about defects. He goes into the electrons, he went back to high school science for us.

[00:05:53] **Seán Kavanagh:** Nice. Yeah, building it up from first principles.

[00:05:56] **Arfon Smith:** right. And so, so is there a particular subset of materials that ShakeNBreak focuses on that are of particular interest to your individual research interests?

[00:06:04] **Irea Mosquera-Lois:** Yeah, we work on solid materials, like crystals, kind of, yeah, crystalline, so with high order, so similar to salt, if you have sodium and chloride, kind of order. But it could also even work in materials that are a bit more disordered. But yeah, generally it would be order Crystal the main application.

[00:06:24] **Seán Kavanagh:** To add on to that, usually solids is like a quite a wide range of applications, so not just I guess we think of semiconductors and insulators, but across the whole spectrum from low band gap semiconductors that we might use for solar cells up to, yeah, insulators that are used in like ceramic materials, even like cladding materials and nuclear reactors, things like that.

So yeah, I guess it's a relatively general application space.

[00:06:48] **Irea Mosquera-Lois:** From what I understand ShakeNBreak is specifically to help with these low energy structures. Can you explain a little bit more about that and like why you built ShakeNBreak?

[00:06:57] **Seán Kavanagh:** Yeah, it was a problem that has kind of been noticed in this field of research, but had been only kind of seen in a few select cases or maybe a little bit brushed under the rug. And essentially, when we're modeling defects in these materials, of course, we need to know what the actual atomic structure or the geometry of the atoms around that defect site are to then actually be able to model it and predict its energy and other sort of behavior.

But the standard way that we do that with our quantum mechanical modeling methods, so specifically DFT,

It depends on what initial structure you give your model, because it'll take that initial structure and try to relax and find the lowest energy arrangements that it can, starting from that initial position, that initial kind of path on this energy surface, but that could end up giving you what we call a local minimum on your potential energy surface rather than the global minimum.

And so you can end up getting stuck in these kind of, what we call like high energy basins rather than dropping down to the lowest energy position on this potential energy surface. And so ShakeNBreak was a method that we tried to develop to try and counteract this behavior. It's essentially like a global optimization approach to try and ensure that we're actually identifying the lowest energy possible defect structure, which is the one we actually expect to occur in reality in most cases.

[00:08:20] **Abby Cabunoc Mayes:** I actually really appreciate your hands visual. When I was reading, I didn't quite get that. 

[00:08:24] **Seán Kavanagh:** yeah. 

[00:08:25] **Arfon Smith:** I was going to say, you could use the board behind you if you want. I'd take a lecture on this right now. So DFT is Density Functional Theory, I think, which is a computational chemistry method. What is shake and bake? Shake and bake. ShakeNBreak. Sign of a good pun when you accidentally use the,

[00:08:42] **Seán Kavanagh:** Yeah.

[00:08:42] **Arfon Smith:** Yeah, yeah, yeah, it slipped. Not for the first time, I'm sure. Does ShakeNBreak actually drive the calculations? Or is that an implementation detail for the user? Like, what package they might use to actually, run the computational chemistry calculations.

What's the sort of broader stack of software that's, that's involved here?

[00:08:59] **Irea Mosquera-Lois:** yeah, so ShakeNBreak is kind of a bit general, so it would just generate kind of the atomic arrangements or the geometries that Seán was talking about.

And the user could decide what kind of software they want to use for the actual kind of quantum mechanical calculation. Or even, it doesn't have to be quantum mechanical, it could also be used in other methods. So, yeah, that's up to the user. Like, we provide compatibility with kind of the main or wider softwares, like the ones that have a bigger user base.

But, yeah, kind of easy to use with another one.

[00:09:32] **Arfon Smith:** So this is more like a tool for helping set up the precursor steps before the calculation,

[00:09:39] **Irea Mosquera-Lois:** Yeah, exactly.

[00:09:40] **Arfon Smith:** Cool, okay. 

[00:09:41] **Abby Cabunoc Mayes:** Just to make sure I understand. So it's a tool to set up these calculations, but then it's also addressing a piece that's often overlooked in current de facto calculations. How does, am I understanding that correctly? 

[00:09:53] **Seán Kavanagh:** So yeah. Yeah, exactly. So it's, as Irea said, it's setting up these initial structures, so trying to generate a range of potential reasonable initial structures to start these defect calculations. So it's how it's, I guess, changing the approaches instead of just doing one defect calculation or like relaxation calculation, we'd call it in like the de facto or the standard approach.

It's now that we're taking a range of possible defect structures, that's output by ShakeNBreak, doing the same type of calculation, but now with these range of possible structures, and then ShakeNBreak also does this, the parsing and analysis side of it, where it takes the final structures and energies from those calculations and analyzes them essentially to see which one actually ended up being the lowest energy and then taking that forward for the rest of our calculations.

So I guess it's like that sort of workflow, but not changing the specific quantum mechanical or otherwise like machine learning, potentially energy calculation in a sense.

[00:10:50] **Abby Cabunoc Mayes:** Okay, yeah, that was really helpful. Thank you.

[00:10:52] **Seán Kavanagh:** Yeah,

[00:10:52] **Arfon Smith:** So, what would people be using before ShakeNBreak? Like, are there other popular alternatives that you sort of found deficient in some way, or you didn't like, or, you know, is there other alternatives that people might use here?

[00:11:04] **Irea Mosquera-Lois:** Yeah there are a couple. There's one, I think it's called Lineman, or something like that. It kind of addresses the same problem, like trying to find the most stable geometry for a given defect, but it's quite expensive. Like, you would need a lot of calculations to find it.

And it wasn't maybe as user friendly as we wanted our tool to be. So that's what kind of pushed us to build this tool to make it kind of more efficient and applicable to kind of problems where you want to model a lot of defects in your material.

[00:11:37] **Abby Cabunoc Mayes:** Thanks.

[00:11:37] **Seán Kavanagh:** Mhm. Mm

[00:11:38] **Arfon Smith:** when I was doing things related to computational chemistry, there were no open source tools for doing even the calculations.

People would typically use tools like Gaussian or QChem. I'm curious if that's changed in the nearly 20 years since I completed my PhD. Are there good open source tools for even doing these calculations these days, once you've made those configurations with ShakeNBreak?

[00:11:59] **Irea Mosquera-Lois:** So, yeah, I feel like there are a few, like, there are several kind of first principle codes that you could use, kind of Quantum Espresso or CP2K in their open source.

[00:12:11] **Seán Kavanagh:** FHI-aims as well 

I 

[00:12:12] **Irea Mosquera-Lois:** yeah, yeah, right, is yeah. 

Also, some others that kind of do classical or machine learning kind of approaches. So I think there's quite a good variety and like people making great efforts for these codes to be open source and reduce the barrier for other researchers with less resources to perform 

[00:12:30] **Arfon Smith:** Nice.

Yeah, that's great. That's great to hear.

[00:12:32] **Abby Cabunoc Mayes:** So this paper was actually nominated by one of the editors again and she was mentioning how, yeah, this group has done a great job of publishing software together with the work, which we really do appreciate.

What encourages you to keep doing this when it's an often thankless job in academia? 

[00:12:46] **Seán Kavanagh:** Yeah that's a good question and something I guess we talk about, I think about quite a bit. So as you mentioned first the group particularly David's group, at UCL, try and yeah, and Aaron's group actually, I guess, with other software as well, like PyTASER we'll try and, yeah, make our codes open access and relatively user friendly as well, so that people can actually easily pick it up and use it in their research.

But yeah, what I'm encouraged to do when it's often a thankless job. That's a good question. I might have to think about that for a second. Yeah, I guess, I mean, part of it is like almost community service that you want your code to be usable and like to help push the forefront of research forward.

If we actually want people to be adopting these more advanced approaches to research you know, the code itself needs to be usable. Because if someone sees some random code online that has like 10 different installation steps and involves you downloading and compiling something in Fortran and downloading this thing and whatever, it's going to put people off.

At the same time, you get some visibility and exposure out of it too. So while it is in many ways a thankless job, you still have your name attached to the code. At least now with things like JOSS, you can actually publish the code and that count as a publication on your CV, whereas before that, you know, often wasn't even possible itself. So I guess that's what I'd say, but I don't know, Irea might have some other opinions on that.

[00:14:09] **Irea Mosquera-Lois:** Yeah, I think I would just add that we've benefited from great codes that were open source, so maybe like pymatgen or ASE that are kind of to manipulate structures. And that accelerates your work so much that you kind of want to contribute to that philosophy that I guess builds science. 

[00:14:25] **Seán Kavanagh:** Yeah, that's a very good point, yeah.

[00:14:28] **Arfon Smith:** Yeah, the I like these answers are really heartwarming in some sense, I think, you know, the motivations sound really, really good. I was reminded of the, I think, mission statement of the Software Sustainability Institute, software.ac.uk, which is better software, better research. I think, you know, Seán, what you're saying is, you know, sure you can share code that you use to conduct your one experiment, but actually a much more valuable contribution is a more generalized tool that allows others to follow and do, build on that work, right? And there's so much opportunity for the open source story to actually have value in research and academia.

It's actually a really strong fit, I think. 

[00:15:06] **Seán Kavanagh:** yeah I really agree with that I mean I think as Irea said, these tools like pymatgen and ASE were the same sort of philosophy of being, you know, quite readily usable and general as well. And then the fact that it's open source, you can see all the underlying code.

And then if you want to tackle a specific problem in your code, a lot of time you can get inspiration by seeing how it's done there. And then, you can kind of go about implementing similar approaches. And yeah, the fact that it does, as you say, kind of give this large, wide scale acceleration of research in the fields, as everyone can build on each other.

[00:15:37] **Abby Cabunoc Mayes:** One thing that I find really interesting about this paper if I understand correctly, it was your group that like discovered the issue with the low energy structures in the first place. So then being able to, no, yes, I don't, okay, okay,

[00:15:50] **Seán Kavanagh:** But I guess it was, yeah, it was kind of a big project on trying to see how general this behavior was. So it was myself and Irea worked in this project where essentially it would just been from noticing this behavior in one or two select cases, both in my research and also in the literature.

So there'd been this behavior had like bit was noted before, but I'd just been in one or two select rare cases because essentially it's the sort of thing that you don't see unless you go looking for it. So it had only been noticed one or two times before, mostly like serendipitously. So by accident it was kind of a semi famous in the field one for Joel Varley, who's someone who actually works with Jimmy Shen at LLNL where it was from trying to do calculations of the migration of defects.

But then suddenly he found that on this migration path, actually, there was a lower energy structure. So what he thought was the original defect structure actually wasn't. It was the transition stage between the lower energy defect structures. So it was kind of mainly from the, you know, occurrences like that people realize, oh, actually this can be an issue.

And so, yeah, I guess we tried to do a more general study of, Is this just a rare case in select materials or actually does this often happen in general across these different materials? Which I guess is, yeah, what the study that myself and Irea worked on and we found was quite a general behavior and then try to implement this method, ShakeNBreak, to go alongside that with actually trying to tackle it in general.

[00:17:20] **Abby Cabunoc Mayes:** Yeah, okay so you discovered how general it was?

You discovered how general it was and then released ShakeNBreak just to help with that in the field, which I think is really admirable.

[00:17:29] **Seán Kavanagh:** Yeah,

[00:17:30] **Arfon Smith:** Where does news happen in your field? So like, when somebody was like, found that there was low energy state, was that a paper, a pre print, where people were like, Oh my god, look at this pre print!

Or is there like, a big Slack or like, Discord that everyone's on? Or was it Twitter or whatever? Like, where, is that exciting? Or were people like, yeah, whatever. Like, was that big news? It seems like big news.

[00:17:53] **Seán Kavanagh:** I guess it depends yeah, what the forum for it is and again, it's like big news, but big news in the field, which can be

at 

[00:18:00] **Arfon Smith:** it's still big 

[00:18:01] **Seán Kavanagh:** field as well. So It's yeah, yeah, yeah, exactly. But I guess for that one for me, it was like, conferences are actually quite a big thing.

For this, so like, yeah, academic conferences and particularly ones that are kind of semi focused. So there's obviously a lot of like big conferences where there's thousands of people, but some of this was actually at one of these, what I call them, Gordon Research Conferences, so a GRC. We have a kind of relatively specific field, so in this case it was like a defects and semiconductors conference, and there were maybe like a hundred people there, a hundred people across the world who work in this field, and so at some of them, it's quite nice because then it's all the talking points in the discussion, so both like actually in talks, but also like at lunch and at dinner, when you're sitting around the table with other people and talking about these ideas, and so I guess, yeah, for that specific one I mentioned was kind of, yeah, like a conference like that, where it was mostly talk about talk.

[00:18:55] **Arfon Smith:** All defects all the time.

[00:18:57] **Seán Kavanagh:** yeah, exactly. For, for a week, 24 7 defects and some football at lunch, but mostly defects.

[00:19:03] **Arfon Smith:** Probably talking about defects, still, a little bit on the side, yeah, yeah, good.

[00:19:07] **Seán Kavanagh:** Yeah. Yeah.

[00:19:08] **Arfon Smith:** It's okay, that's the point of research, right? You get super specialist and, well, it's not the point, but as consequence of research, you end up quite narrow and what seemed like can feel like huge news.

I still have a colleague who I worked in my PhD area. I studied this thing called the diffuse interstellar bands. They are some little things that you see in space. They're little spectroscopic absorption signatures, and there's hundreds of them. And none of them have been assigned in about 150 years. We don't know what they are.

We don't know what the molecular carriers are. And yet, 20 years later, I occasionally email a friend of mine and say, do we have any assignments yet? And he's like, no. I'm like, okay, but it's gonna be big news when there are some, you know, it's just one of, it could, perhaps, it could be some interesting materials, presumably.

Anyway there you go. Don't study the diffuse interstellar bands, just in case anyone was wondering. It's not a good career. 

Let's see Irea, I was wondering if you could sort of comment on the sort of state of peer review and software in your field, like, did anything about the JOSS experience, did you think that was good?

I'm not fishing for compliments, I promise, but I was curious, like, if you found that a useful experience, is there anything, especially as it sounds like you both published software, like how do you feel like academia does generally in terms of sort of reviewing and understanding that work, that type of contribution?

Do you have any thoughts on that?

[00:20:23] **Irea Mosquera-Lois:** I thought JOSS was great, like, first, the fact that it's open, and yes, that anyone can see it, then that it was quite fast, at least for us, and that the reviewers were quite kind of involved, like, looking at the source code, looking at the tutorials and going through them. So, yeah, I don't know, I guess JOSS was way better than the other experiences I had.

[00:20:43] **Arfon Smith:** Pretty good. What about yourself Seán? Do you have any thoughts on sort of publishing software more generally? Is that a thing you think is sort of understood in your respective fields?

[00:20:51] **Seán Kavanagh:** Yeah. I mean, I think I'd echo what Irea said first anyway, that the JOSS experience I think in general is quite nice and we've been involved in a couple of papers that have been published in JOSS and actually both myself and Irea are on one paper that's currently under review in JOSS as well.

So again, all open source. But yeah, in general, I think people there give quite useful feedback on the software. In some other publications that can be more just kind of some cursory feedback on like the paper that you've written to describe the software, but actually in JOSS people make it quite a good effort to actually download it, use it, you know, see, give feedback on actually the user experience as well, which I think is can be quite important for these tools.

And I think in general, it's nice that there's now are these like avenues for publishing research software as well. I think I mentioned that a bit earlier, but before JOSS, there was one or two journals like I guess, Computer Physics, Communications, but there wasn't so much of an easy avenue or obvious opportunity for researchers to publish software, which makes it even more of a thankless job, I guess.

Because yeah, if you spend months kind of developing this code that you want people to use and benefiting the community, but then there's nothing that really goes on your CV because of that, but then that can make it quite tough, obviously, in academia, particularly to get a job. So it's nice that JOSS kind of provides this avenue where you get a publication out of it and something that's citable when people are using your code.

And so you can show that, yeah having some of those metrics as well.

[00:22:20] **Arfon Smith:** Well I'm glad that resonates. Sounds like it was a great fit for you as a journal, so I'm glad that worked out.

[00:22:25] **Abby Cabunoc Mayes:** Yeah, 

[00:22:25] **Seán Kavanagh:** Yeah, absolutely.

[00:22:26] **Abby Cabunoc Mayes:** They submit another thing, so there must have been. 

[00:22:28] **Arfon Smith:** Amazing.

[00:22:30] **Seán Kavanagh:** we came

back. Yeah. Mm hmm.

[00:22:32] **Abby Cabunoc Mayes:** I did want to ask a bit more about ShakeNBreak. So if people listening want to check it out, how can they get started? Can they start contributing? Are you looking for contributions?

[00:22:41] **Irea Mosquera-Lois:** Yeah, I guess for using it there are a few tutorials that they could follow. And then for contributing, yeah, like always happy to have more collaborators. I think the easiest would be just either to contact Seán or me or in the GitHub, like, open an issue or something. But yeah, very happy to kind of have people contributing.

[00:23:02] **Seán Kavanagh:** Absolutely.

[00:23:03] **Abby Cabunoc Mayes:** And are you looking for any particular skills? Like, how much quantum chemistry do they have to know to be able to jump in?

[00:23:08] **Irea Mosquera-Lois:** wouldn't necessarily need to like it'll be more about, yeah, kind of Python and the general idea of manipulating kind of atomic structures, but I guess that can kind of learn easily. But yeah, I guess something that we were considering was. Kind of open to other methods, like right now, ShakeNBreak is a bit more focused to quantum mechanical calculations.

So, I guess, if people wanted to use it with classical, maybe, force field, that is kind of another method that you could use to calculate the energy. Like, yeah, it would be nice to kind of, automatize kind of how ShakeNBreak parses the output from those codes.

[00:23:43] **Arfon Smith:** Awesome well look, this has been really fun to talk to you about Shake and Break, not Shake and Bake I was curious if there are places where you would want people to follow your work online. Obviously there's this paper and this software but are there particular places that people can find your work that you would want us to mention here? 

[00:24:00] **Irea Mosquera-Lois:** and 

[00:24:01] **Seán Kavanagh:** both on Twitter, right? If that's still, yeah, gonna stay the way it is who knows? But yeah yeah, yeah, 

[00:24:09] **Arfon Smith:** state.

[00:24:11] **Seán Kavanagh:** yeah, academic Twitter, I think, is kind of in a, yeah, confused state at the moment, whether it's gonna stay or go. Yeah, yeah, but yeah, I guess there were both on Twitter, right?

I guess it's usually a handy place for academics to follow each other and see what we're doing, both papers and other, yeah, things like code development. Yeah, I guess isn't that one of the best ways to follow us, Irea? Yeah. Google Scholar, I guess, is what people use as well in general.

[00:24:35] **Irea Mosquera-Lois:** Yeah, I guess for code, so for GitHub we're also there.

[00:24:37] **Seán Kavanagh:** Yeah, of course. Yeah, exactly. Yeah. We can follow each other on GitHub.

[00:24:41] **Abby Cabunoc Mayes:** Nice. Yeah, and on Twitter it's @ireaml for both Twitter and GitHub, actually, Seán, you're @Kavanagh_Sean_ on Twitter, and then @kavanase on GitHub, and we'll put those in the show notes.

[00:24:53] **Seán Kavanagh:** Yeah.

[00:24:54] **Abby Cabunoc Mayes:** Wait, you didn't spell out Kavanagh, it's, look in the show notes, we'll have it correct there. 

[00:24:58] **Seán Kavanagh:** Yeah, yeah, it was from my, like, university username, so I just used that and then, yeah,

[00:25:03] **Abby Cabunoc Mayes:** Yeah, they always cut off the last few letters of

your last name and then, 

[00:25:08] **Seán Kavanagh:** my, yeah, my surname was a bit too long for them, so, yeah,

[00:25:11] **Abby Cabunoc Mayes:** so K A V A N A S E. 

[00:25:14] **Seán Kavanagh:** yeah, that's the one.

[00:25:15] **Arfon Smith:** Someday I might understand how Microsoft's handles work. Have you ever heard that, Abby? weird. It's how they give you your email address.

[00:25:23] **Abby Cabunoc Mayes:** yeah, I don't know.

[00:25:24] **Arfon Smith:** It's your last name, and there's as many characters as they need to use to make it unique. So I'm A. Smith, but obviously there's an A. Smith, and there's also an A. R. Smith, so I get arf. Arf Smith.

We don't need to put that podcast. That seems very boring now. Anyway 

[00:25:40] **Abby Cabunoc Mayes:** It's cause I didn't have that problem. 

[00:25:44] **Arfon Smith:** Yeah, what's 

[00:25:44] **Abby Cabunoc Mayes:** Smith, it's ACabunoc, cause I don't have, I don't have your Smith. Everyone has the last name.

[00:25:50] **Seán Kavanagh:** it's a bit more unique.

Yeah, 

Smith is very 

common. 

[00:25:55] **Arfon Smith:** It's true. Anyway Irea Seán, thank you so much for your time today. It's been really fun to meet you both and learn about your software and thanks for being a part of JOSScast.

[00:26:03] **Irea Mosquera-Lois:** Yeah thank you so much 

[00:26:04] **Seán Kavanagh:** No problem. Thanks for having us. 

[00:26:05] **Abby Cabunoc Mayes:** Thank you so much for listening to Open Source for Researchers. We showcase open-source software built by and for researchers, you can hear more by subscribing in your favorite podcast app. 

The Journal of Open Source Software is a community-run journal relying on volunteer effort. If you'd like to support JOSS, please consider making a small donation towards running costs at numfocus.org/donate-to-joss. That's N U M F O C U S.org/donate-to-J O S S. 

Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes. Edited by Abby and music CC-BY Boxcat Games. 


[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/gERICASc0Sw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>