---
layout: post
title: "Hey Siri, see you in the summer!"
author: "Abhi"
categories: news
permalink: /:categories/:name
tags: [cmu, news]
image: apple.gif
---

---
Dear Internet,

Four days ago I accepted the offer to intern with the Siri Team at Apple. I shared this news on LinkedIn and have since then been overwhelmed by the wishes I have received. Many also posed queries about the interview process and the preparation required to crack it.

In this post, I will share my experience along with the tips I have to prepare for such an interview.

---

### Note: This is not a masterclass

Before we start, let's go over some basic considerations,
* I interviewed for the **AIML Intern** position which is different from other roles (such as SDE) and therefore, this post might not reflect how the process looks for other roles.
* Even within AI/ML, my research field is primarily focused on NLP and therefore, it is possible that the rounds look different for other fields.
* Finally, each interviewer has a unique interviewing style and experiences/rounds may widely differ for the same role. Therefore, read my experience as only an _experience_ and not a masterclass!

---

### Phase one: Pre-interview
I applied for the role early in October with a referral from a senior. I directly messaged him on LinkedIn and asked if he could refer me for the role. I heard back from a recruiter in the following month of November asking for my availability to schedule the interviews.

I was told that _usually_, there are two rounds of virtual interviews but the team can have more if required.

---

### Phase two: Interviews

#### 1. Live-coding
The first round was a live-coding round where I was asked to solve a coding problem on [coderpad.io](https://coderpad.io) (one of my favourite live-coding platforms!) It was an array problem that I think would probably fall into `medium` category on [leetcode](https://leetcode.com). The interviewer was very interactive and swiftly answered all my clarification questions. After I solved the problem, he asked me the time complexity of the code. After solving the question, we were left with ~15 minutes (out of the allotted one hour) when the interviewer told me to get ready for the second question. My heart skipped a beat – there's one more? There wasn't. He was joking (_*sigh*_). We both laughed and he asked me if I had any questions for him. I asked a few questions and the interview ended.

The next day I heard back from the recruiter – I had made it to the next round!

<!-- #### Round one: Coding -->

#### Reflections from Round 1:
* Anecdotally, interviews for ML roles are not known to have difficult coding problems. Search for the most frequent company-specific lists online (I like Reddit for this!) and practice them properly before other problems.
* While coding, use a debugger (_pdb_ or the good ol' _print_) if you are allowed to use one. For e.g., you can import pdb and also run your code on _coderpad.io_. Utilize it!
* Interviewer is your friend – ask them clarification questions before you start coding. If you get stuck, don't hesitate to ask for hints.

#### 2. Research-calibre
The second round was totally research-based and involved open-ended modelling and design questions. In the words of the interviewer, the purpose of this round was _"to understand my thought process while approaching a problem."_

In the beginning, he asked me to choose one area of ML or NLP that I was most confident about. He then asked me to give an overview of what I knew were the past and current state-of-the-art approaches/models in that area. Such a question could be as detailed as you want it to be. For e.g., a brief survey of seq2seq models could start from vanilla RNNs, touch upon LSTMs, attention-based RNNs and go up to the current transformers-based models such as BART and T5. This was followed by a few classic questions that I have now learnt to expect in every NLP interview – _what issues of RNNs do transformers solve?_ _What are some of the issues with vanilla transformers?_

After gauging my breadth of knowledge in the area, the interviewer designed an open-ended problem based on the approaches I had mentioned before. For e.g., _how can we add additional contextual information to a summarization model?_ We then discussed possible solutions to the problem for the rest of the interview (~35 mins.)

I heard back from the recuiter the same day in the evening. He asked for my availability in the week – I was to expect some _"good news."_

Good news: I got in!

#### Reflections from Round 2:
* This type of an interview is not a _viva-voce_ but a discussion, therefore, interact with the interviewer. Besides your domain expertise, they also want to gauge your collaborative skills and whether you can work in a team. Try to work out the solution *together*.
* Try to connect your ideas to your past projects. If you think of an approach X that could be used to solve a problem Y, perhaps you could mention one of your projects where you tried something similar to X, and it led to some improvements. This can demonstrate your prior experience, as well as, your ability to re-use your or someone else's work – it is redundant to reinvent the wheel!
* Know in depth the architecture and common issues associated with the models you have used in the past. For e.g., if you have used _transformers_, know the computational complexity of self-attention and how it increases quadratically with sequence-length.
* Prepare a high-level summary of other similar models. This is not super-important but really helps in these design questions. For e.g., if you have used transformers, you might want to know a little about Transformers-XL and how it differs from the vanilla implementation.

---

Have any comments or questions about this blog? Drop me an [email](mailto:abhesrivastava@gmail.com)!