# Programming New Procedural Clips and Procedural Contexts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308468
- Page ID: 23308468
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Programming New Procedural Clips and Procedural Contexts
- Parent: Mannequin Technical Topics

## Content

##
Overview

Procedural Clips, as explained in
[the article on them](../Mannequin%20Concepts/Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)
, are clips that can be placed in fragments and allow to execute custom code in synch with the rest of the fragment.

We have Procedural Clips that range all the way from playing a sound, controlling joints on a character, to procedurally aligning an entity to a location specified by the game. The current types are listed in
[this article](../Mannequin%20Concepts/Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)
.

The main interface functions that a procedural clip offers are OnEnter(blendTime, duration, params) Update(timePassed) and OnExit(blendTime).

The following diagram shows when the events are triggered in relation to the lifetime of a Procedural Clip.

```

`
   +-----+--------------------------+
   |    /|                          |\
   |   / |                          | \
   |  /  |                          |  \
   | /   |                          |   \
   |/    |                          |    \
   +-----+--------------------------+-----+
   [             Update             ]
   ^                                ^
OnEnter                           OnExit

`

```

Handling blend in or out times is the responsibility of the implementation of the Procedural Clip.

Note that after a clip receives the OnExit callback it will stop receiving any Update callbacks, even if the blendTime parameter passed to OnExit is not zero.

The following is an example of a class that implements an empty Procedural Clip.

```

`
// In ProceduralClipEmpty.cpp:
struct SProceduralClipEmptyParams
  : public IProceduralParams
{
  virtual void Serialize(Serialization::IArchive& ar)
  {
    ar(exampleParam, "exampleParam", "Example Parameter");
  }

  float exampleParam;
};

class CProceduralClipEmpty
  : public TProceduralClip<SProceduralClipEmptyParams>
{
public:
  virtual void OnEnter(float blendTime, float duration, const SProceduralClipEmptyParams& params) {}

  virtual void OnExit(float blendTime) {}

  virtual void Update(float timePassed) {}
};
REGISTER_PROCEDURAL_CLIP(CProceduralClipEmpty, "Empty");
`

```

CRYENGINE 3.6

##
Procedural Context

(not to be confused with
[scope context](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)
)

Procedural Clips have a limited lifetime. By themselves they have no way to handle what to do when blending out, since after the OnExit callback they are not getting updated anymore. They also have no straightforward way to know what other Procedural Clips might be doing in other layers and resolve any conflicts between them if they should want to, or work together with other Procedural Clips to combine what they do.

If there's no underlying system on the entity that can take care of this interactions, that's where Procedural Contexts come in handy. They provide a system the lifetime of which is tied to the ActionController and that Procedural Clips can easily communicate with.

To create a Procedural Context and ProceduralClips that can refer to that Procedural Context see the following code snippet:

```

`
// In ProceduralContextExample.h:
class CProceduralContextExample
: public IProceduralContext
{
public:
  PROCEDURAL_CONTEXT(CProceduralContextExample, "ProceduralContextExample", 0xbd3b8e9b263b4768, 0x8e5444b453233fb7);

  // IProceduralContext
  virtual void Initialise(IEntity& entity, IActionController& actionController);
  virtual void Update(float timePassedSeconds);
  // \~IProceduralContext
};

...
// In ProceduralContextExample.cpp:
CRYREGISTER_CLASS(CProceduralContextExample);

void CProceduralContextExample::Initialise(IEntity& entity, IActionController& actionController)
{
  IProceduralContext::Initialise(entity, actionController);
  ...
}

void CProceduralContextExample::Update(float timePassedSeconds)
{
  ...
}

...
// In ProceduralClipWithContextExample.cpp:
class CProceduralClipWithProceduralContext
: public TProceduralContextualClip<SProceduralParams, CProceduralContextExample>
{
public:
  virtual void OnEnter(float blendTime, float duration, const SProceduralParams& params){
    // The Procedural Context can be accessed through the m_context member
  }

  virtual void OnExit(float blendTime) {}

  virtual void Update(float timePassed) {}
};
REGISTER_PROCEDURAL_CLIP(CProceduralClipWithProceduralContext, "ProceduralClipWithContext");

`

```
