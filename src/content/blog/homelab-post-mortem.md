---
title: 'Homelab Post-Mortem'
description: 'My home server died'
pubDate: 'Dec 16 2023'
heroImage: '/blog-placeholder-4.jpg'
---

On my main page, I listed that I had a home server running Linux Mint that I used for file storage and a few services that allowed me to enjoy my media library over 
the network on any of my devices. Unfortunately, about a week ago, that server died. Well, not the whole thing, just the important bit. I'll get there in a second. At 
this point, I've come to terms with all of what was lost, and I'm planning to do it all over again, but bigger, better, and properly. If there's one thing I love, 
it's learning about tech and this project has been in the back of my mind for years now. 

Firstly, if you know what a homelab is, great! You're one of us or you've been hanging around us enough to know what we're talking about. 
If you don't, great! Welcome to the grand rabbit hole of "I'll find a way".

A homelab is a term used to describe the practice of and community around building, upgrading, and maintaining a home server sandbox environment for tinkering and 
experimenting with emerging technologies and/or hosting more tame ones. Some do it out of necessity &mdash; certain services and/or content are unavailable in their 
region, are prohibitively expensive, or are restricted to the point where they're not worth using. Others do it for understanding &mdash; rather than break something 
even in work's dev environment, they can test a similar thing at home and when it blows up, it can be wiped clean and tried again without consequence. Others still 
do it because it's fun &mdash; while you have to be a certain kind of person to get enjoyment out of tweaking and maintaining configuration files among a ton of 
other files (on an OS or other program that you're likely not familiar with), the end result can be very rewarding when you turn on the service, see all of your 
media and projects populate, and everything works exactly as you read it would. I'm a mixture of the three, but there are a ton more reasons people do this stuff. 

## Who?

My server was (is?) an Alienware Alpha R2: a Steam Machine made by Valve to create a video game console-like target for developers and publishing studios to start 
pushing their games and applications into a Linux direction. I originally picked it up because it was cheap and I wanted to see if it was suitable for me to bring 
some of my games into the living room to play with my family via remote play. The specs were roughly as follows: 


- Intel i5-6500T
- NVIDIA GTX 960M
- 8 GB DDR4(?) RAM, soldered
- Wifi + BT
- 500GB 2.5" HDD
- Steam OS 3.X, based on Debian

**I/O:**
- 1 HDMI Out
- 1 HDMI In - passthrough
- 4(?) USB 2.0 ports
- 1 1G Ethernet
- Power


Long story short, Steam OS wasn't great, but I'd read up on the machines prior to purchase and knew that I could install Windows on it and get better performance, 
but I already had a desktop and laptop for that. So, I threw Linux Mint on it to see how well it could work as a desktop. Not surprisingly, it worked well enough. 
Mind you, this was around 2017, the bulk of what most people needed to do was access the internet and work with files on the internet. That meant that doing all 
of your basic school work was possible on your phone, but was still easier on a desktop with a full keyboard. So, web browsing, using Google Docs or Office 365 
worked more than fine, and the local programs for photo editing, word processing, and video and music consumption were all flawless. (If you have an old desktop 
or laptop sitting around collecting dust, I would recommend you try it, it's lack of surprises is the most surprising.)

## What?

As time went on, the machine became more and more useful for small things. When my GPU in my main computer died, I was able to use it as a spare and do everything 
on it mostly fine. It didn't handle games very well, but it handled the ones I cared about well enough to not be an issue. My main computer's CPU (still) doesn't 
feature on-board graphics, so no video out from it until I got the card back. As I saw my laptop usage decreasing, I started to transfer all the files I wanted to 
keep from it to this new machine. When I went to uni, I was able to use it to do my Java homework over the network because I ran into an issue with competing Java 
versions on my main machine that I didn't have time to work through at the time. After my GPU came back, I wanted to continue to listen to music while I did 
homework, so I set up a media server. As a bonus, I was able to connect to the server using anything that supported universal plug-and-play (UPnP), which was great
for smart TVs and casting devices. 

I then discovered [Docker](https://www.youtube.com/watch?v=Gjnup-PuquQ), which I learned was a great way to set up applications and environments that work flawlessly
almost every time because dependencies are installed within the container at setup time. This allowed me to experiment with things like MariaDB (SQL), MongoDB 
(which I'm still trying to understand), and try out other media servers without them clashing with my existing one. 

As I collected more files &mdash; books, photo dumps from old phones, school work files &mdash; I began to get into the habit of immediately sending a copy of whatever
I had to the server, usually by FTP or SSH. It was very nice to buy books and videos from Humble Bundle and stream them over to my phone or tablet whenever I wanted 
them for reference or to learn. 

## The Mortem

Last week, I went to feed cats and noticed that my server was off. These things normally happen when someone needs to plug something in and wiggles a power cable 
or when the power blinks in the middle of the night. I hit the power button and went about my business as normal. When I came back to monitor the cats (ask 
about it), I noticed the machine was off again. Strange, but maybe something is telling it to turn off. A failed update step or something. I turned it on again and 
waited. Under the fan noise, I heard a faint beeping: groups of 3 beeps and a pause. After about 15 seconds or so, the machine turned off. Not good. 
For the age of the machine, I thought it was likely the hard drive, as it was several years old and on for a lot of that time. The drive in it was a laptop 
hard drive that wasn't even new when it went in. 

I dismantled the machine, removed the drive, and put it in an enclosure. I grabbed another machine and plugged the drive in. Same beep pattern, but it was something 
in the drive. The drive didn't display when plugged in as most drives normally do and while the enclosure interface was listed in `lsusb`, I couldn't find any 
evidence of the drive. Dead. 

Because I used a desktop OS and didn't have any other signs of drive failure, I didn't check S.M.A.R.T. data on the drive, which could have warned me about any issues 
with it. Also, because this machine was designed as a desktop or living room box, it only had space for a single drive. While I'd been planning (air quotes optional) 
on building a system with redundancy, I didn't have the resources to do so, *especially* this past year. 

## Lessons Learned

The 3-2-1 data policy is real and would save me a lot of headache, but I knew I wasn't particularly setup to handle a failure like this. In order to keep 3 copies of 
my data on 2 separate media, I would not only need the drive space, but also another machine that could handle everything I was throwing at it. As far as homelabs go, 
it wasn't particularly a lot, but here I am without a server. Additionally, in order to keep 1 copy off-site, I would either need to build a replica machine to keep 
at a friend's house or use a cloud storage solution like BackBlaze or AWS to hold that data for me as well. While the drive is dead, I'm not sure I lost a ton of 
data, because everything I'd stored on the server came from other local sources. I still have the laptop, SD cards, phones, and flash drives (that all still work, 
I checked!) that made up all of the server's media library. I may have lost some photos that were in Nextcloud, but that was due to a setup blunder I unknowingly 
made that restricted the allowed IP of the server to only be one address.

## Rebuilding

While I don't know what I could have done aside from having more disposable income to build a better solution and having nerdier friends to do all of this with me. 
I'd love to meet someone else doing something like this to find out what solutions they use and how much they cost, but until then, it's just me and the ol' internet.
I'm continuing to research what I may be able to build that would at least allow me to keep multiple copies of my data and protect from drive failures. So far, this 
is what I have. 

[**TrueNAS**](https://www.truenas.com/) is a storage-first solution for servers of all sizes and is free for non-commercial use. In my research, if you're looking 
to store files to be served over the network, this is what you use. I tried to set it up on another machine a long time ago, but ran into the issue of needing a 
wired network. Because of where I was in the house and the size of the machine, running cable or moving the machine weren't options. Since moving, I now have a 
place I could put a small enough server where it can have wired access to the network. TrueNAS also supports virtualization, so I can run services from it as well.

**Bigger and better drives** are a must. I managed to put a lot into 500GB, but time is only going to require more space and more drives. As far as doing it better, 
I want to shoot for drives made to be used in a NAS applicance. I have seen some SSDs, but I haven't seen enough of them to be okay with trying them out. 

**Space for the drives** because you can't have one without the other. It's easy to get a full-sized tower and throw everything you need into it, but I have space 
restraints. This thing needs to be able to sit in a media console, be fairly unassuming, and be reasonably quiet. No 1U server chassis with PSU fans that could 
blast the thing into low orbit, no 6U Behemoth with 85 drive bays that's going to need to register it's own zip code. These restraints put me in a little bit of a 
pickle, because the best options I've seen so far mean sourcing other parts that I don't already have on hand or don't allow for using things I do have. 

- [AUDHEID](https://www.amazon.com/dp/B0BXD8QSQK), whoever they are, makes this neat little 8-bay chassis that isn't ugly and leaves plenty of room for future 
upgrades. Something like this would be my preferred route just to have some future resiliance against data loss and hope for using newer drives as they become 
cheaper and more available.
- [Jonsbo](https://www.amazon.com/dp/B09WZLHCZG) makes the N1 and N2, two chassis designed to do the same thing in sightly different form-factors. While they both 
support less drives than the AUDHEID, I don't think it's too much of a hit. And it's cheaper. 

**Hardware** is always the hardest part of doing something like this because 1) consumer hardware is powerful enough to run this on just about anything released 
since Windows 8.1 and 2) especially as a homelab project and product, the best hardware is the hardware you already have. As such, the most responsible thing I 
could do is reuse my current hardware when I'm ready to upgrade to newer things. Given the chassis options, this would allow me to reuse the CPU (AMD Ryzen 5 3600), 
RAM (16 GB of DDR4), and basic storage (1 TB mSATA SSD, boot drive), but I would still need to get a motherboard and PSU. Given how old my hardware is, the 
motherboard should be cost effective, at least. 


### Software and Services

As far as services go, I mostly just want to be able to stream my media over the network, but I would love to get more into some development tools, even if it's 
just for myself. 

- **Portainer** was one of the first things I used to manage my Docker containers that I'll certainly be installing again, though I do want to try using Docker with 
just the command line. 
- **Navidrome** is for streaming music via a website or to mobile devices with supported apps. Because there's no dedicated Navidrome app, most of the solutions I've 
found run into API limits when searching for songs or playlists. 
- **Jellyfin** is a version of the UPnP solution I used before, Emby, but without the pushes of a commercial product. If UPnP is supported, it'll do great, as I prefer
to use something like VLC on mobile devices or XBMC/Kodi for larger screens where I can. 
- **MS SQL Server** was something I never thought you could host without a Windows server, but [here we are.](https://hub.docker.com/_/microsoft-mssql-server) While I
don't have an explicit need for a SQL server (SQLite works fine for most of my personal projects), it's nice to have something familiar where I can look at 
`INFORMATION_SCHEMA` as I please. 
- **Nextcloud** is what I set up on bare metal the first time I tried it. While it wasn't perfect, it was good enough for holding and interacting with files, 
especially pictures. My mistake the first time was during configuration, I set the listening IP of the service to the machine's IP at the time instead of 
leaving it as the default which would allow it to work on all addresses. When I tried to go through the setup instructions again, I couldn't find the 
configuration file I used to change that value. At the time, it was fine because the server had a static IP and that address reserved in the router, but next time, 
I think putting it in a container is the way to go. 
- **VS Code Remote Server** - I'm not sure if this one has a container, but being able to develop for a language on anything that supports a web browser and 
a keyboard has saved me a lot of trouble more than once. As I use VS Code already, it would be nice to be able to develop for homework or hobbywork purposes again. 
- **SurrealDB** is a database solution that attempts to save us from databases by being all of them at once. It's still very much in early days and not production
ready last I checked, but having a database that is a traditional RDBMS like SQL, a document database like Mongo, a key-value store like Redis, and a graph database 
all at once sounds like fun. At this point, I would never tell anyone to use it for more serious work, but it's out there.

---

I'm open to any questions about my experience with a home server and rebuilding one. I would also greatly enjoy speaking with someone who also has a homelab, 
as there's always another way to do all of this. 