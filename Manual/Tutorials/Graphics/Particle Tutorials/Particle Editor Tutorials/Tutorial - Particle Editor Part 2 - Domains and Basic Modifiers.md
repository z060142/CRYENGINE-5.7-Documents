# Tutorial - Particle Editor Part 2 - Domains and Basic Modifiers

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/65437724
- Page ID: 65437724
- Breadcrumb: Tutorials > Graphics > Particle Tutorials > Particle Editor Tutorials > Tutorial - Particle Editor Part 2 - Domains and Basic Modifiers
- Parent: Particle Editor Tutorials

## Content

This is part two in our particle effects tutorial series. Today we're going to focus on two concepts:
[Modifiers](../../../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/Modifiers.md)
and
[Domains](../../../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/Modifiers.md#Modifiers-domain)
.

This tutorial builds on the concepts that we went over in
[part one](Tutorial%20-%20Particle%20Editor%20Part%201%20-%20Introduction%20to%20Particle%20Effects.md)
 of this tutorial series, so do make sure that you’re already familiar with what was covered there.

##
Introduction to Modifiers

You’ve already been introduced to Modifiers in part one: the
**
Curve
**
 Modifier (
[17:03](https://youtu.be/LjgEE2QF-6c?t=1023)
) and the
**
Random
**
 Modifier (
[18:26](https://youtu.be/LjgEE2QF-6c?t=1106)
), but in this tutorial, we'll dig much deeper into them as well as the domains on which they depend.

You can start with creating a simplified version of the smoke particle we made last time, as explained in Part 1:

-
Create your new particle

-
Right-click and add the advanced → smoke template

-
Set
**
Spawn:Rate → Amount
**
 to
**
3
**
 particles per second,

-
Set
**
Motion:Physics → Gravity Scale
**
 to
**
-.5
**
 so the particles float upward,

-
And set
**
Life:Time → Life Time
**
  to
**
6
**
 seconds,

-
Lastly, make the particles a bit bigger by setting
**
Field:Size → Value
**
to
**
2
**
.
Click on the
![Image](https://www.cryengine.com/docs/static/attachments/65438274)
 dropdown button to the right of
**
Field:Size → Value
**
. Here you can find all Modifiers whose main functionality is basically to modify the values of the feature to which they’re attached. Simple enough, but in fact this can get very complicated.

![Image](https://www.cryengine.com/docs/static/attachments/65438275)

*
Modifiers
*

##
The Random Modifier

Now it's time to explore Modifiers. The first Modifier we're going to add is the one we used last time, which is simply the
**
Random
**
Modifier. If you drag the
**
Random → Amount
**
 slider, you’ll see that we can vary this between
**
0
**
 and
**
2
**
... but what does the value 2 actually represent and how is it used?

This number essentially produces a range of random values, which is always from
**
1 minus Amount
**
to
**
1
**
. In other words, what you’re setting indirectly through
**
Random → Amount
**
 is actually the basis of the
*
minimum
*
 random value, but the maximum value is always
**
1
**
.

At a
**
Random
**
 value of
**
1
**
, you’ll get randomized numbers between
**
0
**
, which is
**
1 - 1
**
, and
**
1
**
. Those numbers are then multiplied times the value that you’re modifying,
**
Field:Size → Value
**
 in this case, or whatever Modifier you’ve selected. And if you watch the particles spawning, indeed you can see their sizes ranging from a pinpoint up to their original size, but never bigger, because the maximum
**
Random
**
 value is
**
1
**
, and that’s multiplied by the original size.

It’s worth pointing out that this maximum
**
Random
**
 value of
**
1
**
 means you can’t make numbers any bigger, only smaller, so your original number should be the largest value you ever want to see.

##
Negative Random Values

Next, if you do the math, you’ll quickly see that if you set
**
Random → Amount
**
 to a value larger than
**
1
**
, your minimum values will start going into negative values, because it always subtracts this value from 1. To demonstrate that, we need to modify something other than
**
Field:Size
**
, because “negative size” isn't feasible.

Instead of modifying this Component that you've been building, let’s say you want to keep it as it is so if you change your mind later you don’t have to undo a zillion changes, you can make a copy of the entire Component by right-clicking on an area right beneath the Component’s title bar and choosing
**
Copy
**
, then clicking on a blank area in the Effect Graph and choosing paste, or pressing
**
Ctrl + V
**
.

Now we have two Components that do exactly the same thing. So, to make our life easy, we're going to name each Component by double-clicking on the titles. We will call the first one
*
random size
*
. And since we don’t want to see it for now, let's also disable one of the components by clicking the
![Image](https://www.cryengine.com/docs/static/attachments/65438276)
 button.

Disabling a Component is not quite the same thing as merely hiding it via the
![Image](https://www.cryengine.com/docs/static/attachments/65438277)
 button. A hidden Component would still be processed by the Engine, and could affect other components if they’re linked together; you just wouldn’t see it making any particles itself.

For more information, please see the
[Particle Editor](../../../../Editor%20Tools/Particle%20Editor.md)
 page.

We now need to make our particles spawn randomly to either side of the actual position of the particle emitter entity. For that, we need a
[Location:Offset](../../../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/Location.md#Location-offset)
Feature.
**
Location:Offset
**
 is a very useful way to modify the position of where particles appear.

In the image below is a ten meter ruler with the particle emitter placed in the middle of it. This will make it easier for you to see exactly what's happening:

![Image](https://www.cryengine.com/docs/static/attachments/65438278)

*
Location:Offset → X = 5, Scale = 1
*

-
Disable the
**
Random
**
 Modifier in
**
Field:Size
**

-
Set
**
Location:Offset
**
 to
**
5
**
 on the
**
X
**
 axis.
This is actually the maximum distance away from the emitter where we want particles to spawn, but we also want them to appear randomly
*
between
*
 the emitter position and five meters on the
**
X
**
 axis. So we will need the
**
Random
**
 Modifier.

However, you’ll notice that we can’t add Modifiers to the
**
Offset
**
 property fields, probably because they exist in three dimensions, but we can add Modifiers to its
**
Scale
**
property.

-
Go ahead and add a
**
Random
**
 modifier to it,

-
And set
**
Random → Amount
**
to
**
1
**
,
You’ll see that the particles spawn at a random distance between the particle emitter’s position, which is a distance of
**
0
**
, and up to five meters away from it in the positive
**
X
**
 direction. Again, a
**
Random → Amount
**
 of
**
1
**
 generates random values between
**
0
**
 and
**
1
**
 and multiplies them by the original offset value of
**
5
**
, so we get offset values from
**
0
**
 to
**
5
**
.

But if you want to offset to
*
both
*
 sides of the emitter’s position, in other words, from minus five to five meters, you can make use of the negative Random multipliers. So, if you set
**
Random → Amount
**
to
**
 2
**
,  you'll get a multiplier from
**
-1
**
, (in other words, 1-2), to
**
1
**
. Those values are multiplied by the original offset of
**
5
**
, giving you a range from minus five to five meters.

##
Multiple Location:Offset Features

What if we also wanted to randomize the offset on the
**
Y
**
 axis, but with a different range of values, like plus or minus ten meters?

We can’t do it with the
*
same
*
**
Location:Offset
**
 feature, but there’s a simple trick: we can add as many features as we like, so;

-
Add another
**
Location:Offset
**
 feature to the Component and set the
**
Y
**
 value to
**
10
**
,

-
Add a
**
Random
**
 Modifier to its
**
Scale
**
 property,

-
Set the
**
Random → Amount
**
 to
**
2
**
 to get the
**
-1
**
 to
**
1
**
 multiplier.
![Image](https://www.cryengine.com/docs/static/attachments/65438279)

*
Multiple Location:Offset features. X = 5, Y = 10
*

If you turn the
**
Spawn:Rate
**
 up, you can observe exactly where the spawning is happening and that the particles kind of fill out their spawn area and stop floating away. When a 20 meter ruler is placed along the
**
Y
**
 axis, you can see the particles spawning exactly within this five by ten meter rectangle.

In fact, if you explore the
**
Location
**
features, you’ll find out that you can spawn particles in the shape of geometric primitives, including circles, spheres, boxes, omnidirectionally, and even using a CGF mesh component that’s attached to the same entity as your particle emitter.

##
Location:Box

So in the case of our five by ten meter plane, a quicker way to do this would be to just use
**
Location
**
:
**
Box
**
 and set its axis fields to
**
5
**
,
**
10
**
 and
**
0
**
, from left to right:

![Image](https://www.cryengine.com/docs/static/attachments/65438280)

*
Location:Box → X = 5, Y = 10, Z = 0
*

This kind of control allows you to spawn particles with complete control over their placement, like making it look like a window frame is on fire. As we’ll see, you can even distribute particles along a spline path.

We’ll check out these other location features later on.

##
Domains

Now we need to talk about
[Domains](../../../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/Modifiers.md#Modifiers-domain)
.

![Image](https://www.cryengine.com/docs/static/attachments/65438281)

*
Domains
*

You were already introduced to Domains in the first tutorial in this series. Let’s look back at the
**
Random
**
 Modifier by adding it to the
**
Field:Size
**
 Feature again. This is one of the most simple modifiers, because it just has one parameter called
**
Amount
**
.

But now let’s compare this Random Modifier to another one that we also used in part 1: the
**
Curve
**
 Modifier: disable the
**
Random
**
 Modifier and add a
**
Curve
**
 Modifier to the same
**
Field:Size
**
 Feature's
**
Amount
**
property. You’ll notice that while the Random Modifier simply appears as one item in the list of all available Modifiers, when you choose a Curve, an extra dropdown menu of
**
Domains
**
pops up next to it listing ten possible choices, starting with
**
Age
**
. A Domain simply provides the input values that your modifier is altering.

We’ve chosen a
**
Curve
**
 Modifier because it gives you a nice visual representation of the Domain values, represented by the horizontal axis of the Curve Editor, but Curves can be used to modify other Domains as well.

For example, the default
**
Age
**
 Domain is the lifetime of the particle represented on a normalized scale from
**
0
**
 on the left side of the grey box to
**
1
**
 on the far right side.

![Image](https://www.cryengine.com/docs/static/attachments/65438282)

*
Domain Scale = 1, Domain Bias = 0
*

Let’s make this curve a bit more interesting by letting the particles spawn at 100% of their original
**
Field:Size
**
 and then shrinking them down to about 15% of their original size by the end of their
**
Age
**
. We've also made the curve a straight line by setting the tangents on these keyframe points to linear (outgoing tangent on the first point and incoming tangent on the second).

For more information on the Particle Editor's Curve Editor, please see the
[Particle Editor](../../../../Editor%20Tools/Particle%20Editor.md)
 page.
Now the particles simply shrink as they age.
**
Age
**
 is the Domain that specifies the range over which
**
Field:Size
**
 is being modified. It is of course a time-based Domain, but as you’ll see, there are plenty of Domains that have absolutely nothing to do with time.

##
Domain Scale and Domain Bias

We’re not simply stuck with these Domain values; we can also tweak them with the
**
Domain Scale
**
and
**
Domain Bias
**
properties. Mathematically, these are very simple:
**
Domain Scale
**
 is multiplied by the current Domain value, and
**
Domain Bias
**
 is added to it.

If we look at this as a math formula, the final result equals
**
Domain Value
**
 *
**
Domain Scale
**
 +
**
Domain Bias
**
. Remember that multiplication always takes precedence over addition when you calculate the result. And that result is where we land on the horizontal axis when we’re looking at a Domain with a Curve Modifier.

##
Setting Domain Scale < 1

So let’s experiment with these values a bit. Leave
**
Domain Bias
**
 at
**
0
**
 for now so it has no effect, and set
**
Domain Scale
**
 to
**
0.5
**
. That’s getting multiplied times an
**
Age
**
 of
**
0
**
 when a particle is spawned, giving us
**
0
**
, and once again multiplied by our ending keyframe, which is
**
1
**
.
**
1
**
 times
**
0.5
**
 gives us
**
0.5
**
, so that means that this keyframe gets shifted over to
**
0.5
**
 on this horizontal axis. And as you can see, at that point on the curve,
**
Field:Size
**
 has only shrunk to about 60%, which is exactly what we see our particles doing.

![Image](https://www.cryengine.com/docs/static/attachments/65438283)

*
Domain Scale = 0.5, Domain Bias = 0
*

What’s tricky is that you need to think carefully about what values a particular Domain is going to give you to make sense of the result.
**
Age
**
 is always normalized from
**
0
**
 to
**
1
**
, but other Domains will produce entirely different values, like speed in meters per second, or camera view angle in degrees, etcetera.

While we’re looking at curves, it's also worth pointing out that our Domain is represented on the graph by the lighter grey box. That grey box represents the only part of the Domain in which we can modify values by setting keyframes. But if you use your scroll wheel to zoom out on the graph, you’ll notice that it continues past this grey domain area.

-
If you get lost in the graph  just click on the graph property, in our case
**
Curve
**
, in the Properties panel to automatically zoom to the Domain range.

-
If you grab a keyframe like this first one, you’ll see that you
**
can
**
drag it above or below the grey Domain area. For example, I could drag it up to
**
3
**
, which means the particles will start at
**
300%
**
 of the original field size. You can do the same with any keyframe. Remember that these numbers on the vertical axis are just multiplied by the value we’re modifying.

##
Setting Domain Scale > 1

Back in
**
Domain Scale
**
, we can actually put a huge range of values here, to plus or minus
**
999,999
**
. Just remember that any values less than
**
0
**
 or greater than
**
1
**
 are completely outside of the grey domain area.

Now set
**
Domain Scale
**
 to
**
2
**
, and watch what happens to the particles: they still shrink all the way down to the final keyframe value 50% of the way through their Age, but then they just stay that way.

![Image](https://www.cryengine.com/docs/static/attachments/65438284)

*
Domain Scale = 2, Domain Bias = 1
*

If you look closely, you’ll see that they reach that final keyframe value exactly halfway through their lifetime. This it not mysterious; it’s just simple math: the
**
Domain Scale
**
 of
**
2
**
 has been multiplied by the starting Domain value of
**
0
**
 and the final value of
**
1
**
. That extends our Domain all the way over to
**
2
**
. Whatever our last keyframe value is, that value is just held for the rest of the domain, its second half in this case, which is why you see the particles shrinking in half their lifetime and then just lingering there.

##
Domain Bias

In addition to setting Domain Scale, you can also add an
**
offset
**
 to the horizontal axis using
**
Domain Bias
**
. Again, the Domain Bias value is just added to the original Domain values. For example, set
**
Domain Scale
**
 back to
**
1
**
 and set
**
Domain Bias
**
 to
**
0.5
**
, and now the Domain begins at
**
50%
**
 of the way through this curve when the particles have already shrunk about halfway.

![Image](https://www.cryengine.com/docs/static/attachments/65438285)

*
Domain Scale = 1, Domain Bias = 0.5
*

If we set it to
**
-0.5
**
 and zoom out a bit on the graph, you can see that
**
Field:Size
**
 is holding the first keyframe’s value throughout the part of the Age to the left of the keyframe, and then only gets halfway through the decreasing curve before it loops back and start over.

The Curve Editor makes it easy to visualize these Domains, but with other kinds of Modifiers, we don’t have any kind of visual, so you need to know what’s going on and be able to visualize it in your head. We encourage you to play around with a wide range of settings and analyze what’s happening until you’re clear about why.

##
The Linear Modifier

There’s just one more basic modifier that we would like to demonstrate in this tutorial, and that’s
**
Linear
**
. To set this up, we're going to modify the particle slightly:

-
Reverse the direction of the
**
Uniform Wind
**
 to
**
40
**
 to push the particles upward,

-
Reverse the slope of the
**
Field:Size
**
 curve so the particles
**
grow
**
 over their lifetime.
So we’re back to the basis of something like a smoke effect. You should also set the tangents on these Curve points to be linear, so in the end, what we’ve plotted is a straight line that simply uses
**
Age
**
, which is a number between
**
0
**
 and
**
1
**
, as a multiplier for
**
Field:Size.
**
 In other words, the particles spawn at zero size and grow linearly to the original
**
Field:Size
**
 value.

Even though there’s nothing wrong with this approach, given the need to optimize performance at every step of game development, it’s worth asking what do you think is a more expensive formula to calculate: a straight line between two points, or a multi-keyframe spline curve? Even if the curve
*
happens
*
 to be a straight line at the moment, it’s still calculating using a formula that’s
*
capable
*
 of handling a spline curve with many keyframes, and that is definitely more expensive than a straight line between two points.

Since we’ve just plotted a one-to-one relationship between
**
Field:Size
**
 and
**
Age
**
, there is a more efficient way to do this, and that’s where the
**
Linear
**
Modifier comes in.

-
Replace the
**
Curve
**
 Modifier with a
**
Linear
**
 Modifier,

-
Leave
**
Age
**
 as the Domain.
![Image](https://www.cryengine.com/docs/static/attachments/65438286)

All Linear does is simply passing on the values from the Domain, which you can then modify further with
**
Domain Scale
**
 and
**
Domain Bias
**
. So if you compare these two methods, you’ll see that
**
Linear
**
 gives me exactly the same results but at a much cheaper cost.

##
Using Multiple Modifiers

You can and will assign many Modifiers to a Feature, even the same type of multiplier at least more than once. Each of them is simply multiplied by the others, so the order doesn’t make any difference.

##
Summary

That’s it for part two
in our particle effects tutorial series.

##
Video Tutorial

You can also follow this tutorial series in video form on our YouTube channel.

[Embed: https://www.youtube.com/watch?v=h8FV9n7xnz8]
[Introduction to Modifiers](#introduction-to-modifiers)
[The Random Modifier](#the-random-modifier)
[Domains](#domains)
[Domain Scale and Domain Bias](#domain-scale-and-domain-bias)
[The Linear Modifier](#the-linear-modifier)
[Using Multiple Modifiers](#using-multiple-modifiers)
[Summary](#summary)
[Video Tutorial](#video-tutorial)
