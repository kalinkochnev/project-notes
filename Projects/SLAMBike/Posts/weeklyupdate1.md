---
title: "Physics and controls research"
journey_tags: []
img: ""
draft: false
date: 2023-06-05T00:00:00-00:00 
last-modified: 2023-06-05T00:00:00-00:00 
summary: "Attempting to find a handhold to latch on"
type: "log"
---
Summer has officially started and, after a nice and relaxing vacation away from everything, I've been hard at work this past week for SLAM Bike. 

Last log I found several papers describing self driving bicycle designs. Sadly, those papers are not the most helpful resource for beginners, so I decided to take a step back and work from first principles. 

Whenever I start an ambitious project, there is always this initial chaotic frenzy of google searching where I'm pin-balling from one thing to the next, navigating the sea of chrome tabs. One moment I'm googling how bicycles work and the next I'm watching a video on Lagrangian mechanics. I'm looking for any kind of connection to things I already and peeling back the layers of confusion one at a time.

Learning is a lot like rock climbing, especially when you're learning something completely out of your comfort zone. It is like trying to climb a rock wall with few handholds. You have no idea of how to start. The only plan of attack is to climb in any way you can. Try any grip you can, position your body differently and in unorthodox ways, and most importantly, observe how others climb and see what you find appealing. Pin-balling to disparate positions is sometimes frustrating, but an important part of the process. Pin-balling is the better alternative to a case of analysis paralysis. 

There's little penalty to trying and failing in rock climbing, which is why it naturally brings out in people the best tools of problem solving: try again and again, experiment playfully, take plenty of breaks to prevent injury and exhaustion, work on "projects" (difficult climbs)  

## Progress
This is the first project that I have been extensively documenting the things I learn along the way. [Obsidian.md](https://obsidian.md/) is a big reason why I feel much more comfortable taking down notes. I can quickly get my point across in an organized way and refer to it later. The friction in doing so is significantly reduced.

I was debating on how to structure my logs for this project. Since this is something I am working on almost daily, I have been gathering little logs of progress. I don't want to hide the technical details of what I'm working on since that was kind of the whole point of having these logs. Learning in public! At the same time, I think having some form of meta analysis along the way is really important to see if I'm on track.

I allowed myself to spend most of this week pin-balling. And I am really glad I did. I felt like I gave myself time to flounder and collect myself. Now I have a solid idea of what needs to be done with the project and I know my next milestone for the next week or two.

This is in sharp contrast to the AMBER project where it felt like there was no time to learn and only time to execute. Time pressure can be motivating if you at least possess some of the skills necessary to complete your project. But when you are completely clueless, having a looming deadline is terrifying and forces you to worry about what's immediately important instead of what is actually good for the team. I digress.

It became pretty clear that I need some kind of way to test any kind of stability controls systems I develop. That is at the core of the project, how to stabilize the bicycle. Conveniently, this is a common controls systems problem, which someone on reddit has described as a "right of passage". Hearing that is a relief and also makes me happy. I know for sure I'm learning something useful and something that people will appreciate. 

At the conclusion of this week, I have almost completed [my CAD model](https://cad.onshape.com/documents/76a36bb1a69c3961d3fa9e94/w/1beebbe69216e8c3c34f1033/e/1334723eac8817b342eac3bf) of a reaction wheel inverted pendulum. I have a few components I need to purchase like screws, wires, machined axles, and a wood plank. Other than that, everything else is 3D printable. Since I'm away from home this week, I should probably order everything as soon as I can to have everything ready to assemble when I get back.

![](/journey/stabilizingbike/images/InvertedPendulumModel.png)

I have an ODrive motor controller on hand so I have to setup that whole thing. It has been a while since I've used it and I am not looking forward to reading documentation and getting dumb errors again. What I am looking forward to is actually getting this reaction wheel inverted pendulum to work. That will be a glorious day. If it turns out that my pendulum is giving me too much grief, I may purchase a pre-built one if those exist.

Additionally, I have found [this invaluable book](https://link.springer.com/book/10.1007/978-3-031-01827-5) on controlling a reaction wheel inverted pendulum. It is an entire analysis from beginning to end meant to teach people control systems. I also stumbled upon a couple of other really cool resources which I may check out at a later time:

- [Data Driven Science and Engineering](http://databookuw.com/databook.pdf): Machine Learning, Dynamical Systems, and Controls. Online lectures [here](https://youtu.be/WObG2LoSEwQ)
- [Inverted pendulum tutorial series](https://www.youtube.com/watch?v=7eIE23vJcI4) - assembly, design, and coding
- [Non-linear control and modeling of inverted pendulum series](https://www.youtube.com/watch?v=zNhUie9f1go)
- [Advanced Physics by Nick Lucid](https://www.scienceasylum.com/projects.php#book) (minimum of $5 but well worth it)

I am a huge sucker for math visualizations. I found this pretty obscure YouTube channel called [Physics Unsimplified](https://www.youtube.com/@PhysicsUnsimplified) that has a very unique explanation of the counter-intuitive effects of gyroscopic motion ([video here](https://www.youtube.com/watch?v=YiQVna7UTiQ)). 
