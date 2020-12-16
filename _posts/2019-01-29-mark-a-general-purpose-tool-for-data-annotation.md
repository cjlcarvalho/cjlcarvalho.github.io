---
title: "marK – Starting the Development of a General Purpose Tool for Data Annotation"
date: "2019-01-29"
coverImage: "screenshot_20190129_010323.png"
---

In the end of October, I have decided to make a simple tool to help me with some annotation procedures in two projects that I am involved into. These projects are related to Computer Vision and Artificial Intelligence applications. So I decided to evolve this idea, aiming to make this simple tool become a more complex application. It is called **marK** and will help people in the process of data annotation, specially with large datasets and multiple types of data such as images and texts.

Well, for those who don't know nothing about AI, specially when the topic is Machine Learning, there are two main different learning processes: supervised learning and unsupervised learning. The first one is a task where your algorithm learns a function by mapping an input to some output based on some examples of correct input-output pairs. The second is just the opposite of it, where your algorithm will learn by itself as it identifies some common parameters in all the received input.

The idea behind **marK** is to help people with the process of supervised learning. In this learning process, you need to collect a group of examples to make your algorithm learn some task. These examples are united in a dataset and they normally have a collection of raw input data and the expected outputs, which are identified by labels or some other patterns. Data annotation tools are responsible for helping people to create these labels or outputs.

We can work with different types of data as this learning technique can be applied to different contexts and situations. Not only for the Computer Vision area, but as well for the Natural Language Processing and Pattern Recognition areas. Actually most of the data annotation tools offer support to only a specific data type and have a lot of issues that complicates the life of those who are willing to construct a dataset for their algorithms and studies. Most of them are proprietary, by the way.

I have already started the development of **marK**. It is being developed in Qt and actually offers support to the annotation of images with different types of output such as JSON, XML and pixel maps. You can annotate a single image or a group of images from a directory. More classes can be added as you annotate your entities with the possibility of choosing highlight colors. It is kind of sketchy right now because I need to improve some issues with some widgets and the GUI. You can see it working in the GIF below:

\[caption id="attachment\_902" align="aligncenter" width="600"\]![ezgif.com-video-to-gif](images/ezgif.com-video-to-gif.gif) _Ignore the QAnnotator name (I was think about calling it like this before decided to call it as marK) and the bad annotation around the Will Smith face. xD_\[/caption\]

This will be an important tool for those who are interested in this area, specially because it will be a free software to solve the problems that I have mentioned before. I hope to release this project as soon as I can get more time to work on it. Feel free to build the code and try to test it. You can also contribute to the issues that I have included on [its current repository on Github](https://github.com/cjlcarvalho/marK) and implement some new features.
