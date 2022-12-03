---
layout: post
title:  "HangingPlotter PRD"
date: 2022-12-03
tags: HangingPlotter PRDs
author: Matt
---

So you want to build a Hanging Plotter...

# What is it?

Before we jump in to any technical details, lets discuss what a hanging plotter is.

Most printers work by sweeping back and forth placing small dots of ink.
A pen plotter instead works by tracing paths around on a piece of paper.

There are two main kinds of pen plotter:

1. XY Plotter
   - Works by moving a pen along one beam and along another beam.
   - Control logic is rather straightforward: to move to position (x, y), the X-beam moves to x and the Y-beam to y.
   - Requires long rails the size of your desired paper size.
2. Hanging Plotter
   - Works by winding/unwinding spools of thread, letting the pen fall onto the page.
   - The control logic requires a little trig to determine how much the spools should be rotated.
   - Supporting a larger image only requires more string.
   - Construction is a little easier in my opinion -- just mount two motors and wire up the string.

Here are a few examples of hanging plotters, but there are many more across the web!

## References

### 1. PiPlotter

This is the project I made in high school. It won my school's Engineering Contest and my district for the U.S. House of
Representatives "House App Contest".

<iframe width="560" height="315" src="https://www.youtube.com/embed/OTyaAT0rUo4" title="'PiPlotter' by Matthew Merrill (CA-07)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="allowfullscreen "> </iframe>

### 2. IOIO Plotter by Ytai Ben-Tsvi

This project was a major source of inspiration for my design. I especially like the designs for his spools -- they are
very "yo-yo", referencing the name. If I remember correctly, in this project Ytai Ben-Tsvi uses a logic board that he
created called "IOIO" that interfaces with an Android device directly over USB. This is why the phone here is mounted
directly onto the plotter. 

In contrast, PiPlotter uses a raspberry pi that uses some networking code to allow objects to be sent by an android app.
In my view a Raspberry Pi-based approach this is more accessible for most students, but the construction of this is top
rate!

<iframe width="560" height="315" src="https://www.youtube.com/embed/5v_nz6qzoZ4" title="IOIO Plotter" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Key Requirements

1. Plotter consists of at least two stepper motors spinning spools controlling string lengths.
2. Plotter can translate a series of paper position instructions to spool rotations.
3. Plotter can hold a pen, and spool rotations move the pen around a piece of paper.
4. *Optional:* Plotter can use a servo to lift the pen off the paper.
5. *Optional:* Plotter can be programmed to create its own instructions:
 - shapes in random positions on a page
 - its impression of a picture
 - a mathematical formula

## Getting started

Start by creating a work breakdown.
I've created an example you can locate at the [Work Breakdown Template page](/breakdowns).

Consider all work you'll need to complete. First think of the tasks as high level "epics":

1. Electronics to spin stepper motors to precise positions 
2. Construction of the easel/paper/spools/string
3. Programming drawing by turning a series of paper locations into desired motor rotations

Then, think of three to ten tasks for each epic. Which tasks will be easier? Which will be harder?
Which will require the most time? Which can you do in a short amount of time?

Creating this work breakdown document will help you track your progress and understand how much work remains so you can
pace to avoid "crunch mode" as much as possible! It will also help communicate your progress to others if you need to
ask for help -- focusing on the specific aspects of the tasks that are unknown remain.
A well-understood question is already half-answered!

One tool that can be useful is simulating your plotter in software. This allows you to better understand the math, and
allows you to work on the programming logic independently of a completed construction. If the plotter is not behaving as
as you expect it should after you construct it, then you can reason that the problem must be in the motor-spinning code
or electronics wiring!

Here's an example of a quick simulation I made while I was waiting for my components to be delivered.

<iframe width="560" height="315" src="https://www.youtube.com/embed/tzbczSpsVZw" title="PiPlot Bezier Render" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>