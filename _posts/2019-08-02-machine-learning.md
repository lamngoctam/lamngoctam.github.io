---
layout: post
title: "How I Threw myself into Machine Learning"
tags: [machine learning]
excerpt_separator: <!--more-->
---

---
Just like with swimming, dancing, and many other things I have done, I decided that the best way for me to learn machine learning is to throw myself into it...

<!--more-->


![ML](/images/blog-ml.jpg){:height="80%" width="80%"}



## The Initial Impression

Just like with swimming, dancing, and many other things I have done, I decided that the best way for me to learn something new is to throw myself into it. And that's exactly what I did with Machine Learning (ML) and here is a brief summary of what has happened.

ML has been the buzz word for the past few decades and I wanted to understand for myself why that is, so I began by reading some articles on cool ML projects, including [this one](https://blog.floydhub.com/turning-design-mockups-into-code-with-deep-learning/) on neural networks generating website designs. To me, the idea of having machines doing sophisticated tasks and automating lots of processes that were impossible or inefficient to automate before was fascinating, but the more I dig into these algorithms behind the technologies, the more confused I got (this was with no formal education in ML). So I turned to courses to help me demystify such concepts.

For a couple of weeks during summer of 2018, I spent the two or three hours of free time I had per day outside of my summer camp TA job to learn ML basics from the one and only [Andrew Ng](https://en.wikipedia.org/wiki/Andrew_Ng). Andrew teaches a popular course called [Machine Learning](https://www.coursera.org/learn/machine-learning), through which he does such a great job of going through ML topics like gradient descent, unsupervised vs. supervised learning, neural networks, and much more. I learned how to build a neural network to recognize handwritten digits in Matlab and programmed gradient descent from scratch. Highly recommend checking this course out if you're new to the ML world. I got even more curious and decided to look into my school's [ML course](https://alliance.seas.upenn.edu/~cis520/wiki/) to learn more.

Because I couldn't fit ML into my schedule, I audited the course for a good two months until I got too busy and couldn't afford to go to class every other day. Many of the things I learned were also overlapping with Andrew's lessons, thus I had less incentive to attend classes because I couldn't take advantage of the projects given to enrolled students.


## The First Real Challenge

One day, I got an email from my school's career services that the school of medicine is looking for an ML developer for their research assistant role. I responded within 5 minutes and heard back the next day to organize an interview. Despite not having professional experience in the field, I was given the role. My project was to segment catheterization waves from patient's waveform scans.

Beside from the handwritten digit project, I rarely worked with visual data before this project. So here I am, trying to independently design a segmentation model. The logical thing to do then was referring to Google and search for any articles, paper, and documentation on segmentation and neural networks. I was not surprised by how many results came back, which made it difficult to filter through. In my post on the project, I have included a list of resources that I referenced, as well as more details on the actual model architecture, process of development, and results. 

I spent some time in Matlab trying to use their built in tools for machine learning, only to find it difficult to look for help when I needed because the Matlab ML developer community is pretty small and exclusive since it is not a free software. I migrated to Tensorflow - Keras then and life suddenly became easier. With more tutorials, documentation, and support from Keras users, I was able to get a U-Net model to semi-work (I wrote about how well it works in my project post) in a week. I even looked to AWS to reduce training time and refining techniques, all done within ⅓ of the time it took me to develop in Matlab (unsuccessfully). This is not to say that Matlab does not have great tools and models, it is just less used by casual developers like myself and thus harder to find answers to debugging questions.


## Conclusion

Do I think I'm an expert in ML now? Absolutely not. And I'm not sure if I will ever be at the rate of progress that the technology is growing. But I'm glad that I got to test the water for myself and not only be able to understand why ML is the next big thing, but also come up with my personal take on HOW it will be the next big thing. As a computer graphics major, I can come up with dozens of ways that ML can benefit the field, from refining renders to adding autocomplete to artist's tools to generating 3D worlds from existing data. I'm pretty thrilled to be able to live during this wave of technology and see where I can apply ML to my own work.