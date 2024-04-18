---
layout: post
date: 2024-04-18 00:00
title:  "JOSSCast #8: Deep Learning for 3D Protein Structure Predictions – Giulia Crocioni on DeepRank2"
category:
- josscast
---

<iframe src="https://podcasters.spotify.com/pod/show/josscast/embed/episodes/Deep-Learning-for-3D-Protein-Structure-Predictions--Giulia-Crocioni-on-DeepRank2-e2if1vd" height="102px" width="400px" frameborder="0" scrolling="no"></iframe>

**Subscribe Now:** [Apple](https://podcasts.apple.com/ca/podcast/josscast-open-source-for-researchers/id1725931379), [Spotify](https://open.spotify.com/show/42YQ4O6sbz7ZDi8qbOiX5E), [YouTube](https://www.youtube.com/@JOSSCast), [RSS](https://anchor.fm/s/ef96e5fc/podcast/rss)

Giulia Crocioni joins Arfon and Abby to discuss DeepRank2, a deep learning framework for 3D protein structure predictions.

Giulia is a Research Software Engineer at the Netherlands eScience Center where she uses different machine learning techniques to develop and contribute to methodologies and applications to answer life sciences research questions.

You can follow Giulia on [LinkedIn](https://www.linkedin.com/in/giulia-crocioni/)

### Episode Highlights:

- **[00:02:16]** Giulia introduces herself and her work at the Netherlands eScience Centre in the Life Sciences section.
- **[00:04:09]** Introducing DeepRank2:  An open-source deep learning framework for data mining of protein-protein interfaces or single-residue variants.
- **[00:10:14]** Target audiences (researchers, developers) and applications (drug design, cancer vaccine development)
- **[00:13:48]** Ecosystem overview from complementary projects like AlphaFold, to training data sources, to using PyTorch.
- **[00:23:27]** Open Source & Contributions

### Links:

- JOSS paper: [https://joss.theoj.org/papers/10.21105/joss.05983](https://joss.theoj.org/papers/10.21105/joss.05983 )
- DeepRank2 repository: [https://github.com/DeepRank/deeprank2](https://github.com/DeepRank/deeprank2)
- Netherlands eScience Center: [https://www.esciencecenter.nl/](https://www.esciencecenter.nl/)
- Giulia on LinkedIn: [https://www.linkedin.com/in/giulia-crocioni/](https://www.linkedin.com/in/giulia-crocioni/)
- [The Journal of Open Source Software](https://joss.theoj.org/) ([Twitter/X](https://twitter.com/JOSS_TheOJ), [blog](https://blog.joss.theoj.org/))
- @arfon on ([fosstodon](https://fosstodon.org/@arfon), [Linkedin](https://www.linkedin.com/in/arfon/), [GitHub](https://github.com/arfon), [website](https://www.arfon.org/))
- @abbycabs on ([Twitter/X](https://twitter.com/abbycabs), [hachyderm](https://hachyderm.io/@abbycabs), [bsky](https://bsky.app/profile/abbycabs.bsky.social), [Linkedin](https://www.linkedin.com/in/abbycabs/), [GitHub](https://github.com/abbycabs), [website](https://abbycabs.github.io/))
- [Donate to JOSS](https://numfocus.org/donate-to-joss)

### Transcript:

[00:00:05] **Abby Cabunoc Mayes:** Welcome to Open Source for Researchers, a podcast showcasing open source software built by and for researchers. My name's Abby,

[00:00:11] **Arfon Smith:** My name's Arfon.

[00:00:12] **Abby Cabunoc Mayes:** and we're your hosts. So every other week, we interview an author published in the Journal of Open Source Software, or JOSS.

This is episode 8, and today we're chatting with Giulia Crocioni about their paper, DeepRank2, Mining 3D Protein Structures with Geometric Deep Learning. I really enjoyed this conversation because Structural Bioinformatics was actually my favorite course in university, but I never did any of it professionally, and I was like, oh yeah, proteins, I remember how this works.

[expand]


[00:00:39] **Arfon Smith:** I also enjoyed it. I always forget what proteins are. I know they're very important, and so it's always good to have it like that. Reload it into your brain a bit. I always get kind of confused with structure versus active structure, and like, because there's all the sort of difference between, yes, there's the sequence of molecules and atoms, but then actually how their shape turns out to be way, way important, right, for Drug design and biological function and stuff, so it's cool.

This is like one of those software packages where clearly there's just a ton of real world value in this software. Speaking as an astronomer, that can't always be said. 

[00:01:16] **Abby Cabunoc Mayes:** It was also nice to hear more about the the eScience Center. We have a repeat guest from the institution, which is doing amazing work.

[00:01:23] **Arfon Smith:** Look, I'm just going to say, if we are still doing this podcast in a year, we should do an on site recording at the Netherlands eScience Center. 

[00:01:31] **Abby Cabunoc Mayes:** We'll just walk down the halls.

[00:01:32] **Arfon Smith:** Just going door to door with a mic.

Yeah, they do great work.

[00:01:37] **Arfon Smith:** There's lots happening there. A thing I learned today was that they do a competitive process for applying for research software engineering time. Which, on reflection, makes a ton of sense. These are very specialized skilled individuals who can help you with your research problems.

And so why wouldn't you make that a competitive process to ask for their time? They're clearly doing lots of interesting work there. 

[00:01:58] **Abby Cabunoc Mayes:** Yeah, well, let's play the interview.

[00:02:00] **Arfon Smith:** Yeah, let's get going. 

[00:02:01] **Abby Cabunoc Mayes:** Welcome to the podcast, Giulia. We're so glad to have you here.

[00:02:04] **Arfon Smith:** Yeah,

[00:02:04] **Giulia Crocioni:** Thanks, I'm so glad to be here.

[00:02:05] **Abby Cabunoc Mayes:** I know we've had one other person from Netherlands eScience Center, so we're definitely a big fan of where you're at. But I guess that's a bit of a spoiler for your intro, but do you want to say a few words about yourself and where you're calling from?

[00:02:16] **Giulia Crocioni:** Yeah, sure. So, I'm Giulia Crocioni. I am originally Italian. Now I live in Amsterdam, in the Netherlands. And I work at the Netherlands eScience Centre in the Life Sciences section. My background is in biomedical engineering and data science. And now in the Life Sciences section, I help researchers to develop software, especially in genomics and life sciences, more general domain.

[00:02:40] **Arfon Smith:** I have a question straight off the bat, which is how many research software engineers are there at the eScience Center? There seems to be

[00:02:47] **Giulia Crocioni:** Around 80,

[00:02:48] **Arfon Smith:** Oh, wow. Okay. That's

[00:02:50] **Giulia Crocioni:** Yeah, we grew quite a lot in the last couple of years. And myself, I started in 2022. So, I was in one of those big rounds. 

[00:03:01] **Arfon Smith:** So does it feel like a real proper team? Do you have an identity as a research software engineer or are you very local to the particular research problems you're working on?

[00:03:10] **Giulia Crocioni:** Yeah, so we do have teams, so we have different sections. I am in the Life Sciences section. So everything that is bio related goes there, project wise. And then within the section, we have also different teams. I'm in a team called Team Flow. We go with the flow and we do big data and health related projects and also machine learning related projects in the domain of the Life Sciences. We work really close to each other. We do not participate in all the projects of the team, but usually we work in two, three people at the same time for each project.

[00:03:47] **Arfon Smith:** Nice. Nice. It sounds like a great place to work. 

[00:03:49] **Giulia Crocioni:** It is, it definitely is, yes.

[00:03:52] **Arfon Smith:** Cool. So we're here to talk about DeepRank2 and so I guess maybe first question, was there a DeepRank 1? Is this the second version of this

[00:03:59] **Giulia Crocioni:** Yeah, there were many. 

[00:04:02] **Arfon Smith:** Oh okay, well maybe there's a deep rank zero as well.

So tell us about the software, what it does why you started the project, what kind of problems does it solve?

[00:04:09] **Giulia Crocioni:** So first, I think it's good also to give a bit of context about how we work at these projects. So basically, our organization is a national center that awards research projects based on calls for proposals. And what the awarding projects win is hours of work from the research software engineers of the organization.

And DeepRank2, is part of a very big project awarded in the call of 2021. This call was awarded to Li Xue, which is an assistant professor in the Department of Medical Biosciences at Radboud University Medical Center in Nijmegen, always in the Netherlands. And this package is actually an improved, unified version of other three packages.

That were two out of three of them were always developed within another of our internal calls. The main point about this package was that we noticed starting from our own stuff developed by us, that usually the software solutions around for these kind of problems, were highly specialized and especially lacked the flexibility.

Also in the previous call case, in which two packages called one DeepRank and the other one DeepRank GNN were developed they were sort of similar to each other, tackling the similar research questions, but from slightly different points of view. So, being more specific, the very first DeepRank package was developed for implementing convolutional neural networks, and trained them on these molecular structural data represented as grids.

Then there was a second version of it, called DeepRank GNN, that was basically the same thing, but using graphs as data representation, and then graph neural networks to train on this kind of data. 

Then there was also a third version developed, not by us, but by one of the postdocs of the lab at the RadboudUMC. And she was focusing on pathogenic variants in protein protein complexes using convolutional neural networks again. But this was a slightly different representation of the same data.

And so we had the three versions that sure were doing different things, but not so far from each other. And they were having slightly different APIs, so you couldn't just plug and play the same code to the different packages. Some documentation was lacking, some tutorials were lacking as well. 

And so we unified everything in this enhanced version. And now this one is able to do all of these things.

[00:06:42] **Abby Cabunoc Mayes:** Oh, that's great

[00:06:43] **Arfon Smith:** it sounds like a perfect sort of aggregation of lots of different

[00:06:46] **Giulia Crocioni:** Yes,

[00:06:47] **Arfon Smith:** Independent software projects packaged into a generalized library, which sounds super useful.

You said something right at the start that was super interesting I just have to ask about. You said people apply for software engineer time? Did I hear that right? So researchers apply for research software engineering capacity to be applied to their domain. Is that right?

[00:07:06] **Giulia Crocioni:** Correct. Yes, and these people are Dutch researchers in different stages of career. But yeah, but there are some requirements from this point of view.

[00:07:15] **Arfon Smith:** I just really like that model. I like it for a bunch of reasons. It really reinforces the value of the time of those individuals. But it also is like a computing and research computing grant in some ways, right? Like people are used to applying for super computing time, but what about applying for research or for engineering?

Anyway, that was a side note. 

[00:07:34] **Abby Cabunoc Mayes:** I remember talking to Nico about how he often collaborates with these different organizations around the Netherlands. I assumed that you just found these collaborators, but having them apply for time, that makes a lot of sense.

Anyway, for the original DeepRank and the DeepRank GNN, I know those are different implementations for doing the analysis. Is there a difference for the end user who's actually using the software? Does one do something better than the other? 

[00:07:55] **Giulia Crocioni:** It really depends on the problem. Yeah, in absolute terms it's difficult to say if one architecture is going to work better than another one, Or a type of data representation is going to work better than another one. 

Of course, there are some general things that we can say, like that graphs are definitely a more compact and efficient data structure than grids, for example. And they represent the same amount of information in much less space and also in a much more compact structure itself, which is a graph structure.

But still, then it really depends on the problem. So you really need to just try and see with your data set, with your neural network architecture, and with your type of target as well, what works best.

[00:08:39] **Arfon Smith:** So you can use a graph to represent a structure, I can think how that would be, or you could use some kind of Cartesian grid or something. Those are both just valid ways of representing structures. But the sort of underlying technology or the network so a neural network optimized for graph structures it's just then you get to choose different types of algorithms for traversing those structures. Is that sort of the right way to think about it?

[00:09:05] **Giulia Crocioni:** Yes, and also to give you a bit of more context. So how it works is that first we create the graphs. So the package internally first, when you plug in some data, it creates the graph representation of the data, and then if the user asks for it, it maps the graphs to grids, because these graphs also contain the information about a spatial position of residues or amino acids, and so everything can be just mapped straight away to a three dimensional grid.

And then according to this, we have different classes of datasets that a user can define. So the user can define either a graph dataset based on graphs representation, or a grid dataset based on grids representation. And according to which one the user chooses then it's also possible to use either convolutional neural networks, that are the ones to be used with three dimensional grids, or graph neural networks, the ones to be used with graph representation.

So, basically, the networks are different, so the layers are gonna be different. And we use PyTorch for all these options.

[00:10:12] **Arfon Smith:** Okay. Very good. Yeah.

[00:10:14] **Abby Cabunoc Mayes:** Yeah. Yeah, that was helpful. That's helpful just to understand the span of uses that this can have. So with that in mind, who is your target audience for the software?

[00:10:22] **Giulia Crocioni:** Yeah, so the target audience is very broad. So, in general, any researcher that needs to run experiments based on neural networks and based on this kind of structural molecular data of course, that doesn't want to spend too much time in data processing, which is a very tedious phase, usually, because also just figuring out how to map these data, which features to generate, how to use them, and yeah, that's already a big chunk of the pipeline.

And then maybe the users can be interested in using their own machine learning pipeline, so maybe they have their own TensorFlow Neural Networks, or they don't want to implement that as well, and so they can just use our PyTorch pre implemented pipeline. But anyway, they can be both researchers that are also programmers, but just do not want to spend time on this part because they are maybe interested in trying out some more fancy kind of neural networks, for example, so they are not interested in the data processing part so much.

Also people that are not experienced at all with programming. So that's also why we provide a very extensive documentation and tutorials part, because indeed this software is also taught for people that do not have much experience with programming at that low level.

[00:11:40] **Abby Cabunoc Mayes:** Okay. Yeah, that makes sense. And I know in the paper you mentioned things like drug design, immunotherapy. Is that also on the research side, what your target audiences is? 

[00:11:47] **Giulia Crocioni:** Yes, yes, because maybe researchers identified a class of proteins that are really of interest, but then they want to select a subset of these proteins. And so to have a predictor that runs predictions with high accuracy on such complexes can be something very, very useful for drug design, for example. Or an application that we actually developed using this package is about cancer vaccines.

So in developing certain types of cancer vaccines, it's really important to understand if certain types of proteins that are called MHC proteins, I'm not digging into that too much now, but certain kind of surface proteins, if they are able to bind with peptides that are within the cell, then they are able to expose these peptides on the surface of the cell. And if the cell is a tumor cell, then the immunogenic system is able to activate and to kill the cell.

So it's very important to select these peptides well. And how to do that? Well, you can train a neural network on thousands or even millions of data that tells you which peptides are good candidates by predicting which ones have a good binding affinity with these proteins. So that's what we did as a use application for the software,

[00:13:04] **Abby Cabunoc Mayes:** Nice. Yeah, and I haven't heard much about cancer vaccines, so that's an interesting application for this. Yeah, thanks.

[00:13:09] **Giulia Crocioni:** definitely.

[00:13:09] **Arfon Smith:** A bit of a sort of sideways question, which is just to help sort of calibrate where we are in the sort of technology space here. So I've read about things like AlphaFold and protein folding challenges. And actually, even before that, like the Foldit challenge, where the citizen scientists were involved in trying to through a game, like help fold fold large molecules, proteins in a browser and it sort of gamified that.

I was just curious if you could sort of calibrate me a bit on how does this work relate to some other work that goes around that happens around protein structures, protein foldering. Which part of the sort of problem are we working on here with this?

[00:13:48] **Giulia Crocioni:** Sure. So what alpha fold and in particular the last version of it, which is alpha fold two. What it does is that it takes as input sequences of amino acids, so of these basic building blocks of proteins, and then it outputs. the coordinates in space that these amino acids are gonna have when the protein is folded, so when it's in its active state.

Because if you have the sequence of a protein, actually you don't know, one of the most important information about it, which is structuring the space. Because the way in which proteins fold determine a lot their properties, what they can do and what they can achieve, what they cannot. So it's really, really important to know.

So AlphaFold takes as input the sequence and outputs a file containing both the sequence, but it ends with information about the Cartesian coordinates of each residue or amino acid, however we want to call it. And then what we do instead is that we take this information, so this file already reached with information about the space.

So we have two types of information as input. We have the sequence of amino acids and atoms plus the deposition in space of these building blocks. And then starting from there, with domain knowledge and with the computational part of the data processing of the package, we enhance the information adding all kinds of physicochemical features, so the charge of polarity of the residue, the electrostatic field, the van der Waals potential, all sorts of things.

And this is what is used in our pipeline to train our networks. So we are sort of, after the, the AlphaFold 2 phase, let's say.

[00:15:37] **Arfon Smith:** Okay, that's useful to know. And actually, related to that, what would be your sort of source material that you would train on? Is it lots of experimental data? How do these networks get trained ? I'm aware of techniques like X ray crystallography, and you can get structures from there. What are the sort of source materials that have made your trained networks actually useful to academics?

[00:15:59] **Giulia Crocioni:** Yeah, so it can be all sorts of materials, so it can be the material derived from the crystallographic experiments. Nowadays they are publishing more and more data sets containing these kind of experiments results. Those are very useful. And then there are also more synthetic data, so generated by software like AlphaFold 2, but not only.

There are also many other software that do similar things, maybe tackling specific structures. AlphaFold aims to be more general and working with everything but then there are many, many similar software that are just narrower in this sense. So it can be both experimental data or synthetic data, in this sense, that are based on, some way, on some physical modeling.

And yeah, which one is better? Again, it really depends on the specific data we are talking about. Cons of experimental data is that they can be labelled wrong. So you need to do a data cleaning phase very often. You need to be aware that there may be mistakes in how experimentalists classified things or the techniques that were used, maybe they're old data.

But then on the other end, the ones that are right, you're super sure that are correct and fully represent the chemistry and physics that is behind the structure. On the other hand, synthetic data, they aim at reaching a very high accuracy from this point of view. But again, it depends on the tool, on which kind of model you rely on inside.

[00:17:31] **Abby Cabunoc Mayes:** Yeah, and I know data wrangling is always a huge deal. Especially genomic data, just trying to clean it all up, so I understand that pain of training data. 

And I know that you've mentioned PyTorch a couple times. Can you tell me why you decided to use PyTorch? And how that's been going?

[00:17:47] **Giulia Crocioni:** So, PyTorch is one of the biggest Python platforms for developing the deep learning based algorithms. We went for that one because it's very well documented, it has many tutorials, and many people are using it, so many people know about it. So it's both easier for developers to dig deeper into it, but also for future users or future developers to keep going and build up on that.

So this is also something that as the Netherlands Science Centre, we really like to do in general to not reinvent the wheel. We always try to evaluate which are the open source softwares available because it's always better to build on and, again, to not reinvent the wheel or to not start from scratch because other very smart people very likely have already thought about things and likely they have already developed them well.

[00:18:41] **Arfon Smith:** Yeah, for sure. It always makes sense to use something off the shelf if you can, I think, especially for core dependencies. And PyTorch seems to be wildly popular these days and I think rightly so. I was going to ask a slightly different question related to the sort of infrastructure aspects of the project.

What's the cost of training neural networks here that you're working with? Is this an expensive operation? Is there particular hardware that people have to use? And so sort of training and then also, you know, inference and running the network. Could you say a little bit about what sort of hardware resources people would typically need to make use of this software?

[00:19:18] **Giulia Crocioni:** Sure. So the training is definitely more expensive than the inference time. So the inference time, if you have a machine that allows you to just run a model you are done. And we are not talking about large language models that could occupy terabytes of space. So we're talking about much smaller models here.

So the inference part is definitely less a bottleneck than the training part. On the other end, the training part, again, it really depends on how many data you're training on. Usually you need at least the order of thousands, at least. A million, the order of millions is a good order for this kind of research questions usually.

And for that, it's really advisable to have a very powerful hardware. So for example, here we are using the Dutch supercomputer. It's called Snellius, and for the experiment that we run with DeepRank2 for showcasing it we use only one GPU but the package in general supports parallelization both CPU and GPU level.

So, yeah, the package can definitely, as PyTorch, indeed, can definitely handle parallelization. So, optimization of the training procedure, but also of the data processing. But it's more, yeah, on the users, and yeah, they should need to have something a bit more powerful than maybe your local machine.

[00:20:44] **Arfon Smith:** Yeah, makes sense.

[00:20:45] **Abby Cabunoc Mayes:** Yeah, and I guess related to that would users have to train a new neural network for each different type of target, or how often do you think a researcher would have to go through that process and, like, get a hold of a GPU or a cluster?

[00:20:58] **Giulia Crocioni:** Yeah, so, in general, in machine learning, when you change a target the weights of your networks very typically needs to change. So if you're using a network that has been trained on another target, and then you try to do inference on a new target it's very likely that it's not going to perform well, because the network has been optimized on that specific target that you used before.

So yes, in general, you do need to retrain networks on new targets. And yeah, depending on the problem, you may think about either classification or regression. So maybe you have continuous targets. So going back to the cancer vaccine example, you can have the binding affinity value, which is a continuous value of these molecules.

And this is a regression problem. Or you can think about, okay, I want to predict if these two molecules bind or not. So this is more a binary classification problem. And also according to these, in these two different examples that I mentioned, you're going to use also a different loss function for optimizing your network.

So you definitely need to, yeah, to train again if you change it. 

[00:22:02] **Arfon Smith:** thank you. That's useful to know and for people who want to use the package as well. I want to switch tracks a little bit and ask about open source software. This is JOSS is a journal that's about open source software. This is an open source package. Tell us a bit about your experience with open source software and maybe the reason for publishing this as open source software was in particular.

[00:22:22] **Giulia Crocioni:** So we think as organization, first of all, that open source software is the base for collaborative science. And collaborative science in turn is the base for a long term working science as well. So, yeah the JOSS journal in this sense really alliance with our principle and our vision as well.

And we also think that when you have an open source software you can encourage transparency, you can encourage reproducibility, trust, and then you can also involve the community more. These are just advantages because then even when I'm not going to be here anymore to maintain the package, if the package has been spread enough across the community, there's going to be other developers willing to maintain it.

And this is something that always helps. Keeps going and builds up.

[00:23:11] **Arfon Smith:** Yeah. No, I, that vision definitely strongly resonates certainly for me. I'm assuming for Abby too. I'm curious though, is there some kind of manifesto or something at the eScience Center that really embraces this? Is it written down, these ideals, or is it just sort of

[00:23:27] **Giulia Crocioni:** yeah, we do have, yeah, we do have a vision statement, a strategy statement on our website. Yeah,

[00:23:34] **Arfon Smith:** Oh, cool. Okay. 

[00:23:35] **Giulia Crocioni:** When we have to do design choices, for example, when we are at the beginning of a project and we need to pick packages, libraries, we have to do many choices.

We always prefer to go for open source existing software. And again, if something already exists that does something similar to what we need, it's always good to go there. Maybe they have a repository online, so maybe you can, even yourself, you can contribute to the package. You don't need to restart from scratch.

[00:24:05] **Arfon Smith:** Yeah. Nice. Very nice.

[00:24:07] **Abby Cabunoc Mayes:** And Giulia, had you done much open source before joining the eScience Center? 

[00:24:11] **Giulia Crocioni:** I did a bit during the university, but then I worked for an insurance company for a couple of years, and there of course nothing is open source, because yeah, that type of industry is a bit different.

[00:24:23] **Abby Cabunoc Mayes:** Yeah. So is that a big draw to joining the eScience Center?

[00:24:27] **Giulia Crocioni:** Yes, yes. And intertwined with the research and yeah, I really love the vision statement that we have and in general this concept about using and developing open source software in order to spread it more across the community and engage the community. It's really, really nice, and this is how science should be done, in my opinion, and unfortunately it's not always like that, for many reasons, of course, it's not an easy topic, but still, I believe that going towards this direction is the right one. 

[00:25:01] **Abby Cabunoc Mayes:** Yeah, and one of the reasons why I picked this paper for the JOSSCast was looking at your repo and just seeing how many contributors there were and just how collaborative you all seem to be working. So excited to see this being open for contributions. 

[00:25:14] **Arfon Smith:** This is a, obviously a really nice package and it was really fun to see it published in JOSS, so thank you for publishing with us. I guess I wanted to ask, what are the sorts of things that you're looking for in terms of new contributions? Are there obvious things that people could be doing to help improve, extend DeepRank, maybe prepare for DeepRank 3 if that's gonna happen someday, I don't know. What contributions do you especially want as a team?

[00:25:39] **Giulia Crocioni:** Yeah, so it will be amazing to have both structural biology more domain oriented people, but also programmers who are more machine learning slash deep learning oriented people. I think both can contribute a lot and also we would like to incentivate the mix of these communities that very often are very much separated between each other.

Yeah, and in general just open issues, open PRs. We also have a nice discussion tab on our repo and we always welcome new contributions. It can be that you tried the software and maybe you haven't figured out how to install it, or you run it and you incur into an issue an error, or you would like to see a feature implemented there.

So it can also be just new requests, and that we see how it fits with our timeline, or just a discussion. So again, whatever topic users can think is interesting, we are open to pick it up.

[00:26:39] **Arfon Smith:** Very nice, yeah, lots of important work is, especially with a more mature piece of software when you've actually got people using it is just supporting people who are using it and answering questions, right? There's a lot of non code creation work. That's still essential for any big projects.

So cool. Okay. 

[00:26:56] **Abby Cabunoc Mayes:** Yeah, so where can we find you online and keep up to date on your work, both personally and with DeepRank2?

[00:27:01] **Giulia Crocioni:** Yeah, so for DeepRank2, definitely on GitHub, in our repository. So we have this huge DeepRank organization that also contains many other interesting repos including the archived older ones, and there you're going to find DeepRank2 repo. And then on LinkedIn, through the eScience Center channel, of course, they also post news about DeepRank2.

And yeah, me on LinkedIn or on Instagram, but that is less related to , to my software engineering work.

[00:27:30] **Abby Cabunoc Mayes:** Do you have pictures of stroopwafels? 

[00:27:32] **Giulia Crocioni:** Yeah 

[00:27:34] **Abby Cabunoc Mayes:** When Nico was here, I was like, I love Stroopwafels, but I've never been to Amsterdam. Anyways, 

[00:27:41] **Arfon Smith:** yeah, Americans seem to have a lot of them. I know you're Canadian. I know you're not American, Abby. But in North America, there are many Stroopwafels. A surprising number. 

Giulia, thank you so much for coming on the JOSSCast today and telling us about DeepRank2. It's been really fun to get to talk to you and learn about your work.

So thanks again.

[00:27:58] **Giulia Crocioni:** Thank you so much. It was amazing to be here. I loved it.

[00:28:01] **Abby Cabunoc Mayes:** Thanks, Giulia.

Thank you so much for listening to Open Source for Researchers. We showcase open-source software built by and for researchers, you can hear more by subscribing in your favorite podcast app. 

The Journal of Open Source Software is a community-run journal relying on volunteer effort. If you'd like to support JOSS, please consider making a small donation towards running costs at numfocus.org/donate-to-joss. That's N U M F O C U S.org/donate-to-J O S S. 

Open Source for Researchers is produced and hosted by Arfon Smith and me, Abby Cabunoc Mayes. Edited by Abby and music CC-BY Boxcat Games. 





[/expand]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/8tYL5J_KF0g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>