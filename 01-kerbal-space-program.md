![[KSP-LogoFullRed1-2d2moq3.png]]

notes: I want to talk about Kerbal Space Program, but first...

---

# Orbital Mechanics

notes: We've gotta talk about orbital mechanics. Well, actually, we only need to talk about BASIC orbital mechanics.

---

~~Orbital Mechanics~~
# _Basic_ Orbital Mechanics

notes: Orbital mechanics talks about the (often unintuitive) physics of orbits, and how we can manipulate them for fun and profit. (Okay, mostly fun)

---

# Terminology

notes: I'm going to be using a lot of terms here, so here's a lightning-fast glossary of terms, okay? Ready? Go!

---

# Trajectories

<table>
<tr>
<td>Suborbital</td>
<td>Hey, is that the ground?</td>
</tr>
<tr>
<td>Orbital</td>
<td>You're moving fast enough to miss the ground when you fall.</td>
</tr>
<tr>
<td>Escape</td>
<td>Earth is silly, let's see what else is around.</td>
</tr>
</table>

notes: Trajectories talk about where you're going and where you've been!

---
# Apses

- Apoapsis - highest point
- Periapsis - lowest point

(c.f. Apogee, Apolune, Aphelion, etc)

notes: Apses are the highest and lowest points of your orbit! "Apo" is high "Peri" is low.

---
# Vectors

- Prograde / Retrograde
- Radial / Anti-Radial
- Normal / Anti-Normal

notes: Here are some ways to talk about what direction we're pointing when we're in space!

---
# Delta V

Tsiolkovsky rocket equation
$$
\Delta v = v_{e}\ln \frac{m_{0}}{m_{f}} = I_{sp}g_{0}\ln\frac{m_{0}}{m_{f}}
$$
notes: Delta V is...shoot, it's complicated. Man, if only I'd thought of some easy way to talk about Delta V! This is such a huge mistake I'm making that I didn't simplify this!

---
# Delta V

~~Tsiolkovsky rocket equation~~

$$
\xcancel{\Delta v = v_{e}\ln \frac{m_{0}}{m_{f}} = I_{sp}g_{0}\ln\frac{m_{0}}{m_{f}}}
$$

_How big is your gas tank_

notes: Ha, you all just got punk'd, I DO have a simple way to talk about Delta V. Delta V is how big your gas tank is (relative to how big your rocket is and how efficient your engine is. Whatever. It's potential change in velocity -- you're nerds, you get it)

---
# How do I...?

notes: "So, cool, yeah, space is awesome, but like how do I GET there?" Well the thing about space is that it's not very far away. Even on Earth we talk about space beginning at something called the "Karman" line which is 100km up. That's, like, _Salem_. In KSP it's even closer -- just 70km.

---
# The problem

notes: So if space isn't far away, why is it so hard to get there? Well -- have you ever tried to stand by the side of the highway and hop into a moving car? Space isn't far away -- it's FAST. Orbital velocity here on Earth is about 30 kph, which is 18 miles per hour.

Wait did I say per hour? I meant per second. It's 66,000 miles per hour.

---
# Up then over

notes: So we go up until we're free from most of the drag we get from the atmosphere, then we turn sideways until we're moving fast enough that when we fall back to Earth, we miss.

---
# Change our orbit

notes: Now that we can get to orbit, we need to know how to change our orbit to point us where we want to go. Remember those vectors from earlier? Let's look at what each vector Does to our circular orbit

---

<grid drag="30 80" drop="left">
Radial In / Radial Out
<video autoplay loop><source src="media/radial.mp4" type="video/mp4"></video>
</grid>
<grid drag="30 80" drop="center">
Normal / Anti-normal
<video autoplay loop><source src="media/normal.mp4" type="video/mp4"></video>
</grid>
<grid drag="30 80" drop="right">
Prograde / Retrograde
<video autoplay loop><source src="media/prograde.mp4" type="video/mp4"></video>
</grid>

notes: Radial can be useful for getting eccentric orbits back to something more circular and adjusting the timing when doing orbital rendezvous, but we're not really going to get into that here. Prograde and Normal are the two maneuvers we mostly care about. Normal adjusts our inclination about the point we begin our acceleration. Prograde makes our orbit bigger or smaller by stretching the oval from the opposite side of the planet.

---

# Observations

Your actions affect the opposite side of your orbit!

notes: This is the key realization for "conversational" orbital mechanics. If you want to go higher, don't burn up -- wait until the other side of your orbit and burn FORWARD.

---

# What do we do with it?

Go to the moon. Duh.

notes: So alright, now that we've made some observations about different maneuvers, what can we use it for? Well if I speed the footage up REALLY FAST I think I can probably make it to the moon.

---

<video autoplay><source src="media/minmus.mp4" type="video/mp4"></video>

notes: I'm going to narrate over some footage of me taking a rocket to one of Kerbal's sattelites, Minmus. You'll notice the initial ascent followed by a quick turn to the East (bonus points if you know why I turn East) to speed up near orbital velocity. Now I'm planning a maneuver near apoapsis to circularize the orbit a bit before planning another maneuver to extend my orbit all the way out to intersect with Minmus.

Once I've managed a close encounter with Minmus, I create another maneuver halfway out to trim the approach. The further out I make this maneuver the less Delta V it requires, but the more precise the burn must be. I end up setting a throttle limiter to 1% here to ensure precision.

Now I time warp forward until I'm captured by Minmus. Right now I'm still on an escape trajectory back towards Kerbin, so I plot a maneuver near the Periapsis to burn retrograde and slow me down so I don't go skipping away from the moon. Once I remember about the throttle limiter I set earlier I'm able to slow down enough to jettison my penultimate stage and plan a descent trajectory. I'm slowly bringing myself down here, but the reason I chose Minmus is because it's so small (and therefore its gravity is so weak) that I can land safely even without landing legs.

Now that we've touched down, it's time to do what every good astronaut does: plant a flag.

---

# Real world applications

Gemini 4 mission failed orbital rendezvous

Kids today can rendezvous in KSP within an hour or two of touching the game

notes: Gemini project engineer Andre Meyer later remarked, "There is a good explanation for what went wrong with rendezvous." The crew [...] "just didn't understand or reason out the orbital mechanics involved." KSP allows players -- sometimes just young kids -- to experiment with orbital mechanics, rocketry, and mission design in ways NASA engineers could only have dreamed of doing only a couple decades ago. I don't have to preach to a group of software engineers how being able to quickly and painlessly iterate on your designs leads to better results. "Revert to launch" is sure a lot better than scrubbing an orbital rendezvous mission after burning millions of dollars of rocket fuel.

---

![[ksp-difficulty.png]]

notes: Finally, I'd like to leave you with this difficulty curve that the community has created. Together, we hit the first three points, and it only goes up from here. If this interested you at all, or if you just wanna build planes, rovers, rockets, space stations, and see all your favorite toys blow up because you forgot to check your staging, give KSP a try!

---

## Questions?
![[kerbal-goodbye.jpg]]