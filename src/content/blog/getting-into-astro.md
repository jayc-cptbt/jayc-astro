---
title: 'Getting into Astro'
description: 'A first look at Astro'
pubDate: 'Nov 10 2023'
heroImage: '/blog-placeholder-3.jpg'
---

This site has been one of my goals for a long time, but I suffered from decision paralysis. If you
look into the world of web development right now, you'll find an overwhelming amount of choices to make
for just about everything.

I've developed personal and hobbyist sites before when I was in grade school, either for projects to make
a website look like a website for a PowerPoint presentation or just to have one. Geocities and Freewebs were
the places to go and do that and they provided fairly nice tools at the time to take your website from being
a blank white page with text to what could be something people would actually want to visit and maybe keep
up with. This page is just to air my thought process on deciding to go with Astro and talk about what it's like
to use.

## What's Astro?

Astro is presented as a static site generator that makes it quick and easy to get a website up and running.
I previously thought it was just a JavaScript library that could turn Markdown into HTML, which is valuable
on its own for people who _just_ want to get things going, but it's also a great option for people who know
how to do their styling and want to focus on the content. For example, this very blog post is written in
Markdown. If you understand the formatting, the result is exactly what you would expect.

As I'm getting more into the documentation for Astro, which I'm going to see if I can get a local copy of,
I keep seeing references to things like React and Vue components, which is a neat feature and may be a great
way to add functionality better handled in other frameworks. I'll try those out at some point soon, but
today is not that day.

## Why Astro?

As a techy person, I consume a lot of internet content and a small chunk of that is development related.
The first time I heard about Astro was in Fireship's [Astro in 100 Seconds](#) video, which was a spark
to me. After seeing all the complexities of React and Angular, I quickly learned they were overkill for
what I wanted to build. I could use vanilla HTML and CSS, sure, but that would also mean having to
template out pages for posts like this so that they all come out the same. Again, it's a little tougher
to focus on the content rather than the code.

Secondly, I came across a write-up about using Astro to build a static site and why it was a good idea.
While I haven't read the entire article, the author reinforced my belief that a website doesn't need to
be a single page application nor does it need to immediately feature the levels of interactivity that
sites made with React provide. (I'm realizing I'm dunking on React a lot, it's not intentional!) So,
building something that's going to be faster by design and doesn't throw the kitchen sink at you
sounded pretty good to me.

Third, I knew it allowed for flexibility in generating pages and components, which is great for me.
For example, if a page needs a form, I can write in HTML or use an Astro page to do that. If a
component idea comes to me in JSX/TSX, I can use that. If I just need to write a blog post, I can
use Markdown. It's fantastic. Astro pages also allow you to combine HTML and Markdown and call
your JSX/TSX components fairly easily in one source file.

## So far, so good.

In getting this site set up the way I've wanted so far, it's been pretty nice. While not as
straightforward as using raw HTML, it's easy enough and allows for very nice organization of
files and paths. I've kept with the layout of the demo site and changed the colors because I
currently don't have another general theme in mind, though it won't stop me from looking in the
future. You'll notice that my [résumé page](#) looks very different from the rest of the site
because it was made from scratch by me independently of this site. However, I'm mostly happy
with the way it looks.

I'm by no means an Astro (or any other framework) expert, so please take this post with a
grain of salt. If you're interested in getting started with Astro, you can check out
[astro.build](http://astro.build) for how to get started on your local machine or
[StackBlitz](http://stackblitz.com) to get started in the cloud. Neither of them are sponsors,
they're just what I used to get started. (Though, if they wanted to sponsor me, I wouldn't
mind. 😊)
