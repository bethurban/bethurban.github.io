---
layout: post
title:      "What my CLI data gem project taught me"
date:       2018-02-24 00:07:49 +0000
permalink:  what_my_cli_data_gem_project_taught_me
---


I was eager to undertake my CLI data gem project – but also nervous. This would be my first time programming in Ruby without a predetermined objective or tests to guide me. But my approach to coding thus far has been: The more I do it, even if it doesn't click with me at first, the more comfortable I'll feel. And the better programmer I'll become. And so with that in mind, I jumped in.

My first step was to decide what my application would do. I wanted to work with information that interested me to keep me excited about the project. My wife and I are in the process of adopting a dog, and she suggested an app that gave users some sort of information on dog breeds.

**What my application would accomplish**

A quick examination of the [American Kennel Club's site](http://www.akc.org/) gave me an idea:

1. Users would be given a numbered list of all dog breed groups recognized by the AKC.

2. They could then choose which group they were interested in and receive a numbered list of all breeds in that group.
 
3. They could choose the breed they wanted more information on and be given a concise list of breed traits.
 
All of the information, from the groups to the breeds to the dogs' characteristics, would be scraped from the AKC's website.

**How I began**

I wanted to hit the ground running, so I first built my app using hard coding instead of scraping. I wanted all of the methods to work together in the CLI class before I started scraping. So I chose one breed to work with - the first breed on the AKC's site, the American water spaniel - and built out my methods using that dog's specifications.

As I hard-coded, I tried to be methodical. I built new methods as I realized what steps I needed to take to make the app work as intended. Every time I thought of a new functionality that was needed - even something as simple as saying goodbye to the user as he exited the program - I tried to build a new method to contain that function.

**Time to scrape**

Once everything was working smoothly, I started to move the methods in the CLI class into new classes named for their functions: Groups, Breeds, and Breed Details. I moved the appropriate methods to those classes and began to figure out how I could deliver the same information using scraping instead of hard coding, which would make each method so much more powerful and flexible.

**Lessons in scraping**

Going into this project, I was starting to feel a little more comfortable with scraping, but I hit a few roadblocks that really helped me. I had everything working using scraped information – or so I thought. I was testing my app and found that it broke when I chose a certain dog breed, the pug, which was odd.

I took a closer look at the pug's page on the AKC site and discovered that certain breeds had a different HTML structure on their pages, which meant my app broke when it tried to scrape their info.

At first, I built two different scraping mechanisms to handle both HTML structures that I was seeing. But as I tested my scraping code, I soon realized that if I moved a level up, I could actually scrape both HTML structures using the same code, which helped simplify my program.

**Why is that text indented?**

I felt almost done with my app, but one thing was nagging me – the strings put out into the CLI with breeds' information was indented, and I didn't know why. A closer examination of what I was scraping showed that some breeds' info came with `\n` with extra spacing, and others had `\n` along with `\t`.

A Google search quickly showed me what I was dealing with - the strings were being told to move to a new line and brought the extra spacing with them, or they were moving to a new line and tabbing over (or indenting) at the same time.

I fixed this to make all outputted text in the CLI align on the left using `delete!` and `strip` on the strings of breed information.

**A confidence builder**

While my app feels simple - it just returns snippets of information from one website - I also appreciate how I was able to access a large amount of information (the AKC has seven groups of dog breeds and 20-30 breeds of dogs in each group) and parse it for the user.

Building a program from scratch and navigating the hiccups along the way to produce a useful, streamlined app has given me a lot of confidence as I move forward in coding.


