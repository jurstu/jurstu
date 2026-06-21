---
date: 2026-06-21T17:21:27+02:00
# description: ""
# image: ""
lastmod: 2026-06-21
showTableOfContents: false
# tags: ["",]
title: "Robustness"
type: "post"
---


# Learning the solution

There are many example of tutorials in the general network, where somebody teaches someone about something. We often learn this way as coders, IT-guys or architects. This is often a scenario in which we **"learn quite fast"** since there is a simple and easy to follow path from point A to point B - say You wanted to detect skateboards on images:
- You find the tutorial,
- read it once or twice (or not even once)
- copy the code to Your project (or follow the tutorial 1:1 without Your own project)
- check if everything works properly

This has some obvious advantages and some not-so-obvious disatvantages. More often than not the code works and we're happy with the result, and even if we're not - it's super easy to fix it, since the general groundwork for solving the problem is generally layed out. **This path has low mental cost.** By that I mean, there isn't that much work, that went into searching for systemcalls, methods, procedures, how they work, how are they supposed to be used and connected through structures. There is reading and general cognitive work, but not much of it. This makes it **easy to use and hard to remember**, since there wasn't much struggle along the way. The harder something hits us in life, the longer we remember it (generally). This is why everyone is always searching google for "**how to center a div**" - searching it and copying the code required no mental effort in order to use it. If there was no ctrl+c+v the story could be different. 

This can be seen as as good or a bad thing, depending on how the tutorial/solution relates to Your everyday work. Maybe centering a div is something You do once in Your lifetime and rewriting:
``` css
.element {
  max-width: fit-content;
  margin-left: auto;
  margin-right: auto;
}
```
is just not worth it.. (Yes, I did copy and paste it). If you use it everyday - better learn it by heart. Rewriting however requires more mental effort, but ensures that the code has actually went (in some way) through Your brain and whether You want it or not and whether You understood it or not - it did go through.

If You think that's bad - think about what happens when You vibe code using agents :]

# Applying the solution

Aside from the fact that the solution may be remembered or not there is the aspect of applying the solution to Your specific problem. Detecting skateboards may be all You need but maybe the task is to check whether the skateboard is seen inside the skatepark and not outside. For this You still can use some kind of tutorial, but in the end we often have to connect both solutions - detecting the skateboards and checking their positions on the video frame. 

Because of this it's much better to rewrite simple things by hand. When You apply the solution yourself it's almost certain that you went through every line of it, every element, every action it does. Later in coders life it turns out that it's beggining to matter more and more - the solutions and experiences compound, giving way to new quality of their output. 

The solutions in tutorials are generic, they solve only the presented issue - they seldom ask the bigger edge-case questions and they almost never share the answers to them. If You code yourself the intersection of two solutions You should probably consider:
- what are the edge cases of both solutions
- how do those cases interact with eachother

Think like a hacker: how could I modify the input to this function in order to make it fail. What can I do, and how much can I screw with the inputs to make the calculation time go through the moon. What do I expect from this code and how can I make sure it's going to provide it.

# The robustness of the solution

![alt text](/robustness/image.png)

Using the tutorials is fun, but real work, having a job and doing something for money (professionally) requires some actual responsibility. The tutorials often skip over this, as they are a entry for a beginner. Nobody at this level really wants to know, that the detector will produce the bounding box for skateboards only 12.34% of the time there is any skateboard in the frame. They want to see anything work and honestly? That's what should happen - they should get hooked on that feeling - "Eureka, It's working" and stuff like that. This is unfortunate however for higher-level professionals. 

A similar problem revolves around Arduino and Raspberry Pi - both very interesting platforms - they offer a kind of problem however - searching for a high-end solution often makes google come back with beginner level solutions. This happens in 2 scenarios - the search is not phrased correctly, the solution actually exists only on entry level platform (Raspberry Pi CVBS output). In the second scenario it is really hard to find out (for obvious reasons). Let's come back to the main thread.. 


<!---
The solutions offered by companies often end at the demo stage - look at NPU model zoo for almost any ML/AI acceleration device - IMX8MP npu, Hailo8 - everything is great, until You want to do something outside their understanding - everything falls apart, you need support and 

-->

Robustness - we can't rely on 20%, 60% or even 80%, the detector has to work 95% of the times, since it can generate output once every 2-3s. Almost everywhere in engineering you have to compromise. Outside those detections we can track the objects without image (Kalmann tracking) or use additional video tracking (but then we use cpu/gpu/fpu/ALU/npu/apu/RWR/EWMS).


# The actual point, of using the solution

Detecting the skateboard is one part, and even though it may not seem so, it's the easy part. The hard part is using that detection. Think about it, all the tutorials, all the videos and demos - they all can show, how do we detect skateboards on video - and it's great, don't get me wrong. There is a problem however - this was never the endgame - showing the bounding box on the screen after the cpu (or whatever does the fucking calculations these days) has detected something is actually useless. Using that data later on is what makes it valuable. 

You see a skateboard? Great! Is it inside the skatepark? Maybe it's outside it's bounds? How do we know this? 

Without the next level (camera -> image enchancing -> skateboard detection) **all we have is a bounding box on the screen**. There is nothing more to it. We can inform security guy and make him check it out, but he can't be checking the camera feed everytime the skateboard is in the skatepark (valid). 

Let's use the position of the skateboard on the screen and make sure the center of it's box is inside the [skatebowl](https://outside-devon.imgix.net/uploads/Outside_Skate_Jam_2023_OwenTozer-9-SMALL.jpg?ar=&auto=compress&fit=crop&fm=avif&ixlib=php-3.1.0&q=80&w=1800&s=f81b754d0e1b74900a65e5ed398f36de)


Now, if we detect it's outside of bounds, we can inform someone, add the message to the logs, change lights on the skatepark, and so on..  We still haven't touched on what are the intentions of the human - how does he want to use the skateboard (there are models that do this for cars) - we merely know, where it is on the screen.



As you can **see**, there are still many things, that the human brain can do automagically, while we still have a long way to figure out how the machines could do all those things. That's probably also my current look on smarthomes - we can install 300 IoT connected lamps, but we still can't detect intent to turn any one of them properly with 100% accuracy, we rely on movement sensors to decide (which was already true in 1985).

This paragraph ^ also applies to using AI/Agents to code. 

The part which excites me, is there is a rise in camera-based position estimation work, which could lead way towards many fun projects, because these days not doing something professionally means I can't really give it my 100% and the opensource projects really rekindle my hopes. But there are a lot of projects that show it is possible to estimate 3D position of things in the general space. 