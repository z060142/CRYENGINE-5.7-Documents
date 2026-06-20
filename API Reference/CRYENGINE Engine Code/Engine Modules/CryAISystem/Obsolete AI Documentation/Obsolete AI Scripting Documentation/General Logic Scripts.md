# General Logic Scripts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306480
- Page ID: 23306480
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > General Logic Scripts
- Parent: Obsolete AI Scripting Documentation

## Content

##
Overview

Behaviors and characters are not the only types of scripts that exist in the AI portion of CryAISystem scripting. Since LUA is a very flexible scripting language, and one that offers instant access to any global objects and global functions, it is easy to abstract a lot of the common functionality in a separate LUA table and write that code only once but call it from all places where it is needed.

In CryAISystem, this strategy is used very often. While the actual implementation details can be changed at any time and by anyone, this part will provide a little insight on how the general logic scripts were implemented for CryAISystem, and it might give the user an idea of the scope of things that can be done in this way.

As a general guideline, anything that needs to be called by any behavior or script on more than one occasion – it is a good idea to isolate it into its own special table. Some of those general logic tables can be found in the Scripts/AI/Logic folder in your installation directory.

##
Idle Animation Manager

In a lot of places, during the execution of an idle behavior or any kind of job, the system needs to select one idle animation (head scratching, arm stretching etc) from some pool of existing animations. There are a certain amount of fine details when it comes down to how these animations are selected, how the system knows from which animations it can choose etc. This piece of script logic addresses all these issues.

There are a couple of functions that the Idle manager implements, and they basically have to do with populating a list of available animations and selecting one of them at semi-random. That means that while the selection of the animation to be returned is random, the system makes sure that all animations are shown before the same animation is seen again. However, the order in which the animations are shown is indeed random.

The function that selects the controlled random animation is the GetIdle function. It receives the name of the model for the specified enemy and then analyzes whether there are animations for this model. If there are, it selects them at random, and tags the ones that have been selected already. Every random selection is made from animations that have not been tagged. When there is no untagged animation left, the tags are cleared on all of them, and the process starts again with randomly selecting an animation. Please refer to the actual script for the implementation.

One remaining issue is how the idle manager discovers which animations are available for a particular model. This is half-automated. All the idle animations in all models have to adhere to a simple naming rule – they have to be named with the string
**
idle
**
 followed by a double digit number. The double digit number has to start at 00 and increase by one for every subsequent animation (animations named with non-consecutive numbers will not be discovered). Then the idle manager will try to enumerate all the animations starting with
**
idle00
**
 and go as long as the subsequent animations exist. Finally, it will create a table of available animations for every model.

The tables of available animations are created the first time some model requests an idle animation. If the animations are named correctly, the system will discover them all and make sure they are displayed sufficiently randomly. For more information on how this all works please consult the script code.

As discussed before, since the IdleManager becomes a global table in the LUA space, it can be accessed from any place in the code. Plus, it conveniently isolates all the operations discussed here so that any intervention in the selection method for animations or their discovery is transparent to its user.

##
Conversation Management

The complete logic that controls how conversations are performed in CryAISystem is written in the form of a few script tables. There is no C++ code related to the conversations. This makes it easier to maintain and completely rewrite. The following text explains how conversational logic works in CryAISystem.

Conversations in the game have to be first and foremost – scripted. There must be a conversation script that tells the system how many participants a certain conversation has, and the
**
flow
**
 of the conversation. Its best explained in an example, so we will look at one conversation from the few that can be found in the Scripts/AI/Packs/Conversations folder.

```

`
Participants = 2,
Script = {
  {
   Actor = 1,
   Duration = 1837,
   SoundData = {
    soundFile = "languages/missiontalk/training/training_generic_H_1.wav", Volume = 255,
    min = 10,
    max = 40,
    sound_unscalable = 0,
   },
  },
  {
   Actor = 2,
   Duration = 1420,
   SoundData = {
    soundFile = "languages/missiontalk/training/training_generic_H_2.wav", Volume = 255,
    min = 10,
    max = 40,
    sound_unscalable = 0,
    },
  },
  {
   Actor = 1,
   Duration = 1200,
   SoundData = {
    soundFile = "languages/missiontalk/training/training_generic_H_3.wav", Volume = 255,
    min = 10,
    max = 40,
    sound_unscalable = 0,
   },
  },
},

`

```

This really looks more complicated than it actually is. The table simply describes the lines that will be said in the conversation and the dynamics of the conversation. Each conversation needs to be defined in this way.

In order to know how many people need to join the conversation before it starts, the system needs to know the number of participants in the conversation. That is the first parameter of the conversation script. Most conversations have 2 participants, but the number can be bigger or smaller.

Following is the actual script, separated in lines – every conversation line has to have its own sub table. Every line has to define WHICH one of the actors will say it. This is the property Actor and it can be any number between 1 and the number of participants. This property enables the scripting of normal conversations in which the participants alternate in saying one line each (1,2,1,2, etc.), or monologues (1,1,1,1, etc.), or rather one-sided conversations (1,1,1,2,1,1,2,1,1,1,2, etc.).

Beside the Actor, every script line needs to define the time (in milliseconds) that has to pass until the next script line is executed. This parameter (Duration) gives another way to customize the conversation. If the time duration of one script line is the same or bigger than the time duration of the associated sound file, then the resulting conversation has a very civil dynamic (the next speaker waits until the previous finishes his sentence). But, if this time is shorter, then it is possible to script conversations in which one of the participants appears impatient. This will work naturally since the sounds will be played in 3D sound from the respective positions of the participants – something that cannot necessarily be done by baking-in the whole conversation in a single file.

The final property is the SoundData sub-table. This sub table defines al properties of the sound that needs to play when this line is executed – including the actual wav file, the volume, minimum and maximum distance at which the sound will be heard etc.

The lines are executed sequentially in top down.

When a certain number of conversations have been defined in this way, then it is possible to request a conversation with a specific name, or just a random conversation. Even though the games initially the focus was on having more random conversations, for story development and other reasons it was moved away from that principle. Now the conversations are selected based on their name.

When a conversation is requested, the conversation manager selects one appropriate conversation. It is possible to have multiple conversations under the same name – the system will just select one. When the conversation is selected, the entity (AI object, enemy) that requested the conversation has to invite other entities to join the conversation. He does this by sending a signal to the members of his own group. Whoever receives this signal then joins the conversation by calling the function Join on it. When the amount of joined entities becomes equal to the required participants, the conversation is started. IT IS ALWAYS THE ENTITY WHO ORIGINALLY REQUESTED THE CONVERSATION THAT STARTS WITH THE FIRST LINE.

After a line is selected and the associated sound file is played, the conversation sets a timer with the duration of the selected line. When this timer expires, an event is generated in the conversation that makes it call the function Continue on itself and thus continue the conversation.

When the last line of the conversation is finished, then the participants go back to whatever they were doing previously. The conversation is not repeated until someone else requests it.

To understand the finer details of how conversations are managed and how they are executed on runtime, the actual script logic files for the AI_ConvManager and the AI_Conversation can be found as LUA files under the same name in Scripts/AI/Logic.

##
Name Generator

The name generator is very simple, and it really can hardly be called a logic script. It just contains a big list of names that were inserted into a table, and a simple function that retrieves the next available name when someone requests it.

To make this possible, an index pointing to the next available name is bumped every time a new name is requested. If the end of the table is reached, it wraps to the beginning.
