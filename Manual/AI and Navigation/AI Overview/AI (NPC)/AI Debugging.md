# AI Debugging

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798766
- Page ID: 29798766
- Breadcrumb: AI and Navigation > AI Overview > AI (NPC) > AI Debugging
- Parent: AI (NPC)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933199)

## Overview

When debugging AI behaviors, one of the most useful console variables is **ai_DebugDraw**.

Setting this cvar to **1** will result in debug information being drawn above the head of any active AI. In game mode, you can also press ** F11** to set** ai_DebugDraw** to 1 or zero.

You can use **ai_AgentStatsDist** to set the radius within which entity debug info will be drawn.

## Sections

[Sections](#sections)[Setup](#setup)[More AI Debug Draw](#more-ai-debug-draw)[Network AI Debug Draw](#network-ai-debug-draw)

### Setup

Generally, it will look like this:

There's a lot of information here, so here's how it is broken down:

A) REGENERATE COVER SURFACES - This means that the cover surfaces haven't been generated. If the game that you're working on supports cover surfaces, speak to a designer about this.

B) This is the name of the Entity - The name will be **green** for vehicle AI (i.e. the actual vehicle. The driver and passenger names will be in white).

C) Pipe User Group ID.

D) These are cover/combat state indicators. The conditions are true when they're lit up **red**, false if ** grey**:

Abbreviation | Description
--- | ---
**MC** | Moving to Cover
**M/IC** | Moving in Cover / In Cover
**CC** | Cover Compromised
**AL** | Is Alarmed

E) Current Behavior Name.

F) Current Target Name.

G) Current Target Perception:

Abbreviation | Description
--- | ---
**VIS** | Visual
**MEM** | Memory
**SND** | Sound
**AGG** | Aggressive
**THR** | Threatening
**INT** | Interesting

H) Current Goal Pipe Name.

I) Current Goal Op Name - If the goalop is active, it will be rendered **white**. If paused, it will be rendered ** grey.**

J) Stance name and Speed.

K) Aim information and Fire mode.

### More AI Debug Draw

More information on AI Debug Draw can be found [here](../../../Profiling%20%26%20Optimization/Profiling%20Overview/Debugging%20and%20Profiling%20Tools.md).

### Network AI Debug Draw

In multiplayer sessions, AI is updated on the server. If it's a dedicated server, there may be a need to transmit AI debug draw data to the client to display. This is controlled by the following CVars:

CVar | Description
--- | ---
**ai_NetworkDebug** | Disable (0) or enable (1) the transmission of AI debug draw data to the client. To display transmission summary (on the client's display), use **ai_NetworkDebug 2**
**ai_NetworkDebugBytesPerSecond** | Maximum transmission rate in bytes per second
**ai_NetworkDebugChannel** | Network channel which the server uses to send AI debug draw data
**ai_NetworkDebugClientHost** | Network address of the client
**ai_NetworkDebugMinDelay** | Delay between successive transmissions
**cl_serveraddr** | Server address that the client will try to connect to when the user types **connect**. Default is "localhost"
