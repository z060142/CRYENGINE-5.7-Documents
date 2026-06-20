# CryAnimation Overview

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306437
- Page ID: 23306437
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > CryAnimation Overview
- Parent: CryAnimation

## Content

##
Overview

**
Towards More Interactivity:
**
 One of goals at Crytek is to push the boundaries of
**
interactive animations
**
. All animated scenes in the Crysis are rendered in real-time. It is not necessary any more to create cut-scenes in an offline tool and play them as a video. But real-time does not mean interactive. There is still a big difference.

In a game, Crytek usually has two types of animations:
**
linear
**
 and
**
interactive animations
**
:

-
Linear animation is the kind of animation seen in movies and cutscenes.

-
Interactive animation is needed in games for AI-behavior and for avatar-control.
There is a big difference between both of them and this difference is not really obvious for somebody who is playing the game; in both cases they can see characters moving across the screen. The key difference is the
**
decision making process
**
. Everything revolves around one single question:
*
"Who decides what that character on the screen is going to do next"
*

##
Linear Animations

In linear animation, the
**
decision-making process
**
 happens inside the head of the people who design the animation. During this process an animator has
*
direct control
*
 over every single keyframe. There is absolutely no problem with collisions-detection, physics and path-finding; characters only run into walls or collide with each other when the animator wants them to do it. There is also no problem with AI-behavior; the person who writes the storyboard decides how intelligent or stupid the characters are. If you want to show interactions between characters, then you can put several characters in mocap-suit and record their performance at the same time. It is ok if the sequence looks good from one single camera angle; that's what the audience will see on the screen later. All possible events in such a scene are fixed, so animators don't need to deal with complicated transitions and motion-combinations; they can bake everything in one single big fat motion-clip.

Because everything is fixed and predicable, it's possible to guarantee a consistent motion-quality. Animators can always go back and adjust little details in the scene, i.e add or delete keyframes, adjust the lighting, change the camera position, etc.

Therefore creating linear animation is currently not really a technical challenge in games. You still have to make sure that the rendering is not dropping the framerate and that the facial-animations and body-animations are in synch, but this is more a challenge for animators and render-gurus. The animation-technology for linear animation is much simpler then for interactive animations. All linear animations in the CryENGINE are created with
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048798](
Track View Editor
)
.

##
Interactive Animations

When you're creating interactive animation then you're automatically in a world full of problems: Animators and programmers have no direct control any more over the movement the characters are doing on the screen. It's not always obvious where and how the
**
decision making process
**
 happens. It's usually a complex combination of AI, player-input and sometimes contextual behavior.

Interactive animation is by definition responsive. In other words, it must look visibly different with each user's individual input and must be able to adapt automatically to the actions on the screen. The act of moving from linear to interactive animation is more than just a set of small tweaks or a change in complexity; it requires a totally different technology under the hood.

When doing interactive animation it is no longer possible for an animator to exactly plan and model the behavior of a character. Instead, animators and programmers develop a system that allows them to synthesize motion automatically and define rules for the AI-behavior.

One of the most crucial features you need to make animation more interactive is
**
automatic motion synthesis
**
. The system to synthesize the motion must be very flexible, since it is difficult to predict the sequence of actions that a character may take and each action can start at any time.

Imagine a character moving in a typical outdoor environment: you would need to specify the style, the speed, the direction of the locomotion and you would want to see a variation in the motions when running uphill or downhill, and leaning when running around corners. Depending on the circumstances in the game, it might also be necessary to interactively control emotional features such as happiness, anger, fear, and tiredness. You would want to see different motions when carrying objects of different sizes and weights, e.g. with a pistol in his hands a character can run faster than with a heavy rocket launcher. On top of that, you would want your character to perform different tasks at the same time, e.g. walking in direction X, looking in direction Y
*
(to track a flying bird with head and eyes)
*
 and aiming with the gun in direction Z
*
(at a moving object of course)
*
. Providing unique animations for every possible combination and degrees of freedom is almost impossible. The amount of data is incredibly large. It is obvious that you need a mechanism for motion modifications to keep the asset count as low as possible.

Developing such a system involves very close collaboration and a tight feedback loop between programmers, animators and designers. Problems with the behavior and the locomotion system
*
(either responsiveness or motion quality)
*
 are usually addressed from several sides.

Interactive animation can be divided into two categories:
**
Avatar-control
**
 and
**
AI-control
**
.

In both cases, animators and programmers have just
*
indirect control
*
 over the final behavior of the character, because the decision of what the character wants to do next happens somewhere else. Let's take a closer look at the situation in game environments.

**
Avatar control:
**
 For avatar characters the
**
decision-making process
**
 happens inside the head of the person who is controlling the avatar on the screen. The player determines the movement direction and speed and all other actions of his avatar, and the locomotion system is taking the user input and translating it on the fly based into skeleton movements
*
(using procedural and data-driven methods)
*
. For avatar control high responsiveness is the key feature and the motion quality might be limited by the game rules. This means that many established Walt Disney rules for nice looking animations might be in direct conflict with the responsiveness you need for certain types of gameplay.

The quality of the animations depends to a large part on the skills and on the decision of the player who is controlling the character; because he is the one who makes the decision what his avatar will do next. Motion planning based on predictions is not really possible because the actions of the player are unpredictable. Complex emotional control is not possible
*
(and probably not needed)
*
. It's only possible on a raw level, e.g. soft punch vs aggressive punch. But it might be possible to let the player control the locomotion of his avatar, and to let the game code control the emotional behavior of the avatar by blending in "additive animations" based on the in-game situation.

In all these scenes we're controlling the character with a gamepad. The character here is using animation assets made by animators.

**
AI-Control
**
: For AI-characters the
**
decision-making process
**
 happens entirely inside the computer. The dev-team designs the system to generate behavior. The computer program acts as an intermediary between the creators and the audience. But for the program to perform this task, it is necessary for the behavioral decisions and parameters to be specified explicitly. A clear definition of the rules of movements that the characters should undertake is very important. Interactive animation for AI characters is much harder to realize than animations of avatars, but at the same time it offers some (not always obvious) opportunities to improve the motion quality. High responsiveness is still the No.1 goal, but because everything happens inside the computer it is possible under certain circumstances to
**
predict
**
 the actions of the character. If the AI System knows what the NPC wants to do next, then it is possible to incorporate this knowledge into the
**
motion planning
**
 and this can help a great deal to improve the motion quality. Good motion planning might allow it to apply the classical animation rules to interactive animation. AI-Control can have a somewhat higher motion quality then avatar characters, at the cost of having more complex technology under the hood.

The only problem is that AI is always reacting to the player, and there is no way on earth to predict the actions of the player; so the player is the only source of uncertainty in such a prediction system.

The list of non-predicable situations in a game could be endless. Because you can't predict the things that happen on the screen, it's almost impossible to create the right assets for each in-game situation and this in turn makes it impossible to guarantee a consistent motion quality. For an animator who is working on interactive animation it can be a big problem to have no direct control over the final animation, and it is never really clear when the work is complete. This is one of the reasons why linear animation in movies and cut-scenes usually look so much better and why there is so much trouble with interactive animations.

CryENGINE tackles the problem with interactive animation in multiple levels:

On the 'lower level' (CryAnimation library) the engine provides support for animation clips, parameterized animation and procedural modification of poses. The animations can be sequenced together, layered on top of each other in a 'layered transition queue'.

On the 'higher level' (CryAction library) the CryMannequin system helps to manage the complexity: it will manage animation variations, transitions in between animations, animations that are built up out of many others, sequencing procedural code, the link to game code, and so on.

##
Scripted Animations

Because linear animations is easy, and interactive animation is so much harder many games are trying to "blur the line" between cutscenes and in-game actions by using interactive scripted sequences.

In this case characters are acting on a predefined path. The quality for this kind of motion can be very high. Because this is not fully interactive, animators have more control over the entire sequence. It is basically manually designed motion planning. These are perfectly reasonable cheats to overcome hard-to-solve animation problems. It might be even possible to script the entire AI sequence to allow you to fake near cut-scene quality. This can even feel very interactive and looks absolutely cinematic, but actually it is more the illusion of interactivity.

There are many scenes in Crysis where Crytek made use of scripted animations. In the "Sphere cutscene" you can see the Hunter walking uphill and downhill and stepping over obstacles. This is a scripted sequence where the assets were made for walking on flat ground. Crytek used CCD-IK to adapt the legs to the uneven terrain. In the "Fleet cutscene" with the Hunter on the carrier deck, the player can move around, while the Hunter is fighting the VTOL's and other NPC's.

Both scenes look and feel highly interactive, but they are not: the Hunter doesn't respond to the player and the player cannot fight the Hunter. The entire scene is fully linear and scripted; it's basically just animated background graphics. These sequences were created in
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048798](
Track View Editor
)
. Some of them are using the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048897](
Flow Graph Editor
)
. When the cut-scene is over, the Hunter turns into an AI-controlled interactive character.
