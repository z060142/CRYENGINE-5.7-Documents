# Entity Setup From Scratch

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308465
- Page ID: 23308465
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Entity Setup From Scratch
- Parent: Mannequin Technical Topics

## Content

##
Overview

The purpose of this article is to provide a deeper understanding of how the different components of CryMannequin fit together and how to use them.

Since examples can be an accessible way to build up towards that goal, we'll describe how to make use of CryMannequin to control the animation state of an entity from scratch.

##
Core Mannequin Classes

The following is a diagram with an overview of the main components that are involved in CryMannequin. It aims to illustrate the key classes and their relationships. It is not a complete UML diagram of all classes, but more of a useful companion for this article where all of them are used in practice. It is not necessary to fully understand all the concepts at this point, since this article aims to present them as they are used.

![Image](https://www.cryengine.com/docs/static/attachments/23998363)

##
Mannequin Setup

Our first goal will be to be able to animate a character that has two logical animation states, Idle and Movement.

##
Designing the Scope Structure

The first thing we will do is decide how we will divide our character into a series of logical parts. We will be able to control each logical part of a character directly, that is, change their animation state.

For each of these logical parts we create what is called a
*
[Scope](../Mannequin%20Concepts/Mannequin%20Scopes.md)
*
. Scopes are where fragments are started on.

In our simple example we don't need much complexity yet. We will have a single entity with one character instance and we will change between an Idle and Movement logical animation state. For the moment we don't want to be able to control separately what is playing on the upper body of the character. We have enough control if we can decide what plays on the full body of the character. Therefore a single scope will suffice for now. We will call it FullBody.

![Image](https://www.cryengine.com/docs/static/attachments/23998376)

Scopes are mapped to an entity, a character instance and an
[animation database](../Mannequin%20Files/Animation%20Database%20(ADB).md)
 through a
*
[Scope Context](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)
*
. We will create this mapping through code during the entity setup by referring to it by name (MainCharacter). These properties of a Scope Context can change during run-time, so it is possible to swap the entity, character instance or animation database we are playing animations on at any time (we made use of this when swapping weapons in Crysis3 for example).

![Image](https://www.cryengine.com/docs/static/attachments/23998373)

We can always add more scopes later on, when we need more complicated setups or to obtain a more fine grained control over a character. For example, if we want a setup in which we have a full body, an upper body and a weapon entity that we want to control separately and be able to synchronize animations on, we could have three scopes in our mannequin character, one to control full body fragments, one for upper body and a final one for the weapon. Notice how the
[animation layers](../Mannequin%20Animation%20Layers.md)
 that specify which layers of the character instance in the scope context we use are a property of the scope.

![Image](https://www.cryengine.com/docs/static/attachments/23998378)

![Image](https://www.cryengine.com/docs/static/attachments/23998374)

##
Creating the Controller Definition

The structure of the character we will be controlling through mannequin is setup in what we call a
*
[Controller Definition](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
*
. We usually load controller definitions from XML files.

In controller definitions we specify what
[Tags](/docs/static/engines/cryengine-5/categories/23756816)
 make up its global state, what animation states (we will usually refer to an animation state as a
*
[FragmentId](../Mannequin%20Concepts/FragmentIDs.md)
*
), and how the character is broken down into scopes.

We will try to create as much of this setup as possible through the editor, but currently there are some steps that require a bit of XML hand editing.

The following is an example of the minimal controller definition file we'll need. We usually place controller definition files in the
`
Animations/Mannequin/ADB
`
 folder.

```

`
Animations/Mannequin/ADB/sampleControllerDefs.xml:
<ControllerDef>
 <Tags filename="Animations/Mannequin/ADB/sampleTags.xml"/>
 <Fragments filename="Animations/Mannequin/ADB/sampleFragmentIds.xml"/>
 <ScopeDefs>
  <FullBody layer="0" numLayers="3" context="MainCharacter"/>
 </ScopeDefs>
</ControllerDef>

`

```

##
Creating the Tag Definition Files

The <Tags> and <Fragments> filenames point to the global tags and fragmentId definition files that the character will be using. For the controller definition to be valid we will need both files to exist and be valid tag definition files.

The mannequin editor contains a tag definition editor that we can use to create the two tag definition files. For the moment we will keep those two files empty.

Open the Mannequin Editor by clicking on its icon on the tools bar (it is also located under
**
View -> Views -> Mannequin Editor
**
)
**
.
**

The
[tag definition editor](../Mannequin%20Tag%20Definition%20Editor.md)
 is located under "File->Tag Definition Editor...".

![Image](https://www.cryengine.com/docs/static/attachments/23998384)

![Image](https://www.cryengine.com/docs/static/attachments/23998381)

To create a new tag definition we only need to press on the create new tag definition button.

![Image](https://www.cryengine.com/docs/static/attachments/23998385)

A prompt will require us to specify the filename (without extension) of the tag definition file we want. By default it will be placed in the
`
Animations/Mannequin/ADB
`
 folder.

![Image](https://www.cryengine.com/docs/static/attachments/23998382)

We should repeat this step for the two files we need to create: "sampleTags" and "sampleFragmentIds"

![Image](https://www.cryengine.com/docs/static/attachments/23998386)

The content of the files should look similar to this:

```

`
Animations/Mannequin/ADB/sampleTags.xml:
<TagDefinition version="2" />

`

```

```

`
Animations/Mannequin/ADB/sampleFragmentIds.xml:
<TagDefinition version="2" />

`

```

The tag definition editor can be used to add tags manually to the fragmentIds tag definition file, but we should never need to: The editor will do this under the hood whenever we add FragmentIds in the main interface.

Tag definitions that don't end with the name "tags.xml" will not be visible in the tag definition editor unless the "Filter Tags" option is disabled.

![Image](https://www.cryengine.com/docs/static/attachments/23998383)

##
Scope Definitions

Let's look again at the controller definition file and focus on the
*
Scope Definition
*
 setup.

```

`
<ScopeDefs>
 <FullBody layer="0" numLayers="3" context="MainCharacter"/>
</ScopeDefs>

`

```

Each entry in the scope definition section declares a single scope.

The name used for the XML tag, "FullBody" in the example, will be the name given to the scope.

The context attribute (here "MainCharacter") specifies which scope context the scope refers to. From the code side we will later on assign what entity and character instance are associated to that scope context. A new scope context is implicitly created by declaring it, and the name is important since we will reference it later on from the code side when we set up the entity. Different scopes can reference the same scope context.

The layer and numLayers attributes specify on which
[layers](../Mannequin%20Animation%20Layers.md)
 of the character instance in the MainCharacter scope context the fragments will be playing animations on. In this case we are taking layers 0, 1 and 2.

It is possible to have scopes that don't allow any animations by specifying 0 numLayers. It is always possible to play procedural clips on a scope.

The maximum number of layers in a character instance is 16 (numbered 0 to 15).

##
Creating the Editor Preview Setup File

##
Creating an Empty Preview Setup File

The last bit of XML editing we need to do for now is to create a
[preview setup file](../Mannequin%20Files/Preview%20Setup%20File%20(xxxPreview.xml).md)
. For this we will simply need it to point to the controller definition file we just created.

```

`
Animations/Mannequin/Preview/MannequinSamplePreview.xml:
<MannequinPreview>
  <controllerDef filename="Animations\Mannequin\ADB\sampleControllerDefs.xml"/>
</MannequinPreview>

`

```

We can now load the preview file in the Mannequin Editor by going into
**
File -> Load Preview Setup...
**
 and selecting our preview file.

The views will appear empty, since at no point did we fill in the scopes contexts for our preview setup. We need to do this to specify the character or animation database files to use. We will be doing that using the
*
[Context Editor](../Mannequin%20Context%20Editor.md)
*
.

##
Preview File Scope Context Setup

To open the
*
Context Editor
*
 go to
**
File -> Context Editor...
**

![Image](https://www.cryengine.com/docs/static/attachments/23998359)

The mapping of contexts in the editor is something local to the preview files. This mimics on the editor side what we would be doing in our game code when setting the scope contexts.

You could also have many different preview setups pointing to the same controllerdef. That is used in the SDK character, where there is a 1st person preview file that loads the 1st person model only and a 3rd person preview file that loads the 3rd person model only.

For our character, we have one scope context that we've called MainCharacter. To be able to start creating fragments for it we need to associate a specific character instance and an animation database to it.

We can create a new mapping by clicking the "New" button.

![Image](https://www.cryengine.com/docs/static/attachments/23998358)

The following window allows us to edit the properties of the mapping.

![Image](https://www.cryengine.com/docs/static/attachments/23998360)

The name is how we will identify a specific scope context mapping in the editor side of Mannequin. It is local to the preview file, so from the game code we will not reference it. We will see it in the context dropdown menu in the editor and next to the scope names in the
[Previewer](../../Mannequin%20Editor.md#MannequinEditor-previewer)
. In this case we call it MainCharacter, but we could give it any name we want (e.g. SDKPlayer), or change it later without any consequences.

In more advanced setups we can have multiple mappings for the same scope context and swap them in the editor to be able to preview how other characters work with this controller definition setup and to create and edit fragments for the animation database associated to that scope context. For example, we could have a scope context for the weapon, and have a setup where we can preview different weapons without having to swap preview files, just by changing which mapping for that scope is active. For this specific case we can even have the editor do this swapping automatically based on the active tags for the character, to make the editing and preview a more seamless experience.

To select a model click on the "..." button for a file select dialog to appear. For this example we've chosen the SDK player sample character that can be found under
`
Objects/characters/human/sdk_player/sdk_player.cdf
`
.

We also need to specify which database will be used to store fragments. Since we don't have any databases yet, we will create a new one by pressing the "+" button. This will prompt us for the name we want to give to the new database. In our example we will call it sampleDatabase.

![Image](https://www.cryengine.com/docs/static/attachments/23998362)

The Start Active check box makes sure that in the Previewer this scope context mapping is enabled by default. If this is not checked, we would need to associate its activation with a specific set of tags, or manually set it up in the Previewer by right clicking on a scope and selecting the mapping that we want to activate. For our example it is more convenient to make sure that this mapping is always active, since we always want to be able to preview it.

Once we have set up the name, model and database we have specified enough information to create a valid mapping to start creating fragments on.

![Image](https://www.cryengine.com/docs/static/attachments/23998361)

Closing the context editor will save the changes to the preview file automatically.

The Mannequin Editor should now show us the SDK player character loaded in the central viewport, and the name we gave to the context in the context editor selected as current context.

![Image](https://www.cryengine.com/docs/static/attachments/23998372)

##
Creating the Initial Fragments

We can now add the fragmentIds we want. We will call them "Idle" and "Motion" to match the animation states we will be requesting through code.

For an in-depth explanation on how to create
[fragmentIds](../Mannequin%20Concepts/FragmentIDs.md)
 and
[fragments](../Mannequin%20Concepts/Mannequin%20Fragments.md)
 check out their respective articles or the
[tutorial articles](/docs/static/engines/cryengine-5/categories/23756816/pages/23308482)
.

Once we have the fragmentIds we create a fragment for each.

Idle:

![Image](https://www.cryengine.com/docs/static/attachments/23998366)

Motion:

![Image](https://www.cryengine.com/docs/static/attachments/23998367)

##
Creating our Entity

##
Initialization and Setup

Mannequin controlled entities access mannequin through the
*
[Action Controller](Mannequin%20ActionController.md)
*
. When an entity wants to play a fragment it will create an Action and queue it on the action controller. Actions can also start fragments themselves, so it is possible to write actions that have logic that controls which fragment is playing. It is a good idea to only write logic that takes care of animation selection logic in the Actions. There is no technical restriction against it, but relying on the Action Controller as an Action framework for game logic is not greatly encouraged since it is tuned for animation playback.

In any case, before we can start actions and have fragments playing on our entity, there is some code setup needed.

The entity is responsible for keeping track of its action controller and
*
animation context
*
 (see also the UML diagram at the beginning of this article), so somewhere in our data structure for the entity we should hold ownership of each of them:

```

`
// MannequinSample.h:
class CMannequinSample
: public CGameObjectExtensionHelper< CMannequinSample, IGameObjectExtension >
{
...
private:
  IActionController* m_pActionController;
  SAnimationContext* m_pAnimationContext;
...
};

// MannequinSample.cpp:
CMannequinSample::CMannequinSample()
: m_pAnimationContext( NULL )
, m_pActionController( NULL )
{
}

CMannequinSample::~CMannequinSample()
{
  SAFE_RELEASE( m_pActionController );
  SAFE_DELETE( m_pAnimationContext );
}

`

```

The initialization of the action controller and the animation context (can be placed in PostInit for example) can roughly look like the following code snippet:

```

`
void CMannequinSample::PostInit( IGameObject* pGameObject )
{
  ...
  pEntity->LoadCharacter( 0, "Objects/characters/human/sdk_player/sdk_player.cdf" );
  ...

  // Mannequin Initialization
  IMannequin& mannequinInterface = gEnv->pGame->GetIGameFramework()->GetMannequinInterface();
  IAnimationDatabaseManager& animationDatabaseManager = mannequinInterface.GetAnimationDatabaseManager();

  // Loading the controller definition that we previously created.
  // This is owned by the animation database manager
  const SControllerDef* const pControllerDef = animationDatabaseManager.LoadControllerDef( "Animations/Mannequin/ADB/sampleControllerDefs.xml" );
  if ( pControllerDef == NULL )
  {
    CryWarning( VALIDATOR_MODULE_GAME, VALIDATOR_ERROR, "Failed to load controller definition for MannequinSample." );
    return;
  }

  // Creation of the animation context.
  CRY_ASSERT( m_pAnimationContext == NULL );
  m_pAnimationContext = new SAnimationContext( *pControllerDef );

  // Creation of the action controller
  CRY_ASSERT( m_pActionController == NULL );
  m_pActionController = mannequinInterface.CreateActionController( pEntity, *m_pAnimationContext );

  // Scope Context Setup.
  // In our controller definition we have a scope context that we called MainCharacter
  // The Scope Context Setup will associate this entity, the character instance we loaded at the beginning,
  // and the animation database where we saved our fragments to this scope context.
  const TagID mainCharacterScopeContextId = m_pAnimationContext->controllerDef.m_scopeContexts.Find( "MainCharacter" );
  if ( mainCharacterScopeContextId == TAG_ID_INVALID )
  {
    CryWarning( VALIDATOR_MODULE_GAME, VALIDATOR_ERROR, "Failed to find MainCharacter scope context id for MannequinSample in controller definition." );
    return;
  }

  ICharacterInstance* const pCharacterInstance = pEntity->GetCharacter( 0 );
  CRY_ASSERT( pCharacterInstance != NULL );

  // Loading a database
  const IAnimationDatabase* const pAnimationDatabase = animationDatabaseManager.Load( "Animations/Mannequin/ADB/sampleDatabase.adb" );
  if ( pAnimationDatabase == NULL )
  {
    CryWarning( VALIDATOR_MODULE_GAME, VALIDATOR_ERROR, "Failed to load animation database for MannequinSample." );
    return;
  }

  // Setting Scope contexts can happen at any time, and what entity or character instance we have bound to a particular scope context
  // can change during the lifetime of an action controller.
  m_pActionController->SetScopeContext( mainCharacterScopeContextId, *pEntity, pCharacterInstance, pAnimationDatabase );

  ...
}

`

```

##
Starting Fragments

To start a fragment on our character we must queue it on the action controller. Here is a sample snippet that pushes a default action that plays the Idle fragmentId:

```

`
const FragmentID idleFragmentId = m_pAnimationContext->controllerDef.m_fragmentIDs.Find( "Idle" );
const int actionPriority = 0;

IActionPtr pAction = new TAction< SAnimationContext >( actionPriority, idleFragmentId );
m_pActionController->Queue( pAction );

`

```

When we queue an action in the action controller it is just placed into a priority ordered queue.

##
Update Loop

Each frame we will need to tick the action controller for it to resolve queued actions. During this resolve the action controller needs to go through the queued actions and compare them with the actions installed on the scopes it wants to use, and decide if they should be started right away or if they should be delayed and kept in the queue until later. Action priorities and flags are an integral part of how this is decided.

```

`
if ( m_pActionController != NULL )
{
  m_pActionController->Update( frameTimeSeconds );
}

`

```

During the call to the action controller update and after the resolve, the installed actions will be updated. During the update is also when animations are queued in the animation system, so it is a factor to take into account in order to decide where to place the action controller update.

##
Adding Variation

##
Adding Random Variation

At this stage we have no fragment variation within a fragmentId. Every time we start the Idle fragment we will see the same idle animation. If we had several characters starting the same fragment at the same time it would most likely look dull. We can achieve a bit more variation by adding more fragments. If we add a new fragment to the Idle fragmentId we can see in the fragment browser that we now have more than one option. Now, when we queue the Idle fragment, since we have more than one valid fragment to play, a random one will be selected.

![Image](https://www.cryengine.com/docs/static/attachments/23998371)

Queries for the best possible matching fragment to play on a scope are performed on the animation database. When there are multiple valid fragments (i.e. Options), the default behavior is to obtain a random one. Nevertheless, it is possible to force the system to pick a specific option by specifically selecting an option index. It is not necessary for the option index to be in the range of valid options for a fragment (it will be forced in that range automatically using 'modulo').

```

`
IActionPtr pAction = new TAction< SAnimationContext >( actionPriority, idleFragmentId );
pAction->SetOptionIdx( 245 ); // The default option index for an action is the special value OPTION_IDX_RANDOM.
m_pActionController->Queue( pAction );

`

```

When using OPTION_IDX_RANDOM each option has an equal chance of being selected.

##
Adding Variation with Tags

Let's say we want this character to have two stances, which we can call Stand and Crouch. From the code side, we usually don't want to have to select the Idle_Stand, Idle_Crouch animation states. This becomes unmanageable quickly, specially since our character will grow to something more complex and probably have many more extra bits of information that encode how a character should animate (e.g. Is the character holding an item? Which item type? Which item exactly? Is the character tired? Hurt?). Most of the time, from the code side, we don't want to care about such a fine grained level of detail, we want to abstract it a bit. What we really just want to do is request the Idle animation state, or request the Motion animation state. Then have the best animation selected for us given the state of our entity.

While fragment options are useful for resolving variations between equally valid fragments, they are not designed for doing this kind of meaningful choices between fragments.

For such a kind of fragment selection we use tags. Tags are keywords that we use to give some context information to our fragments for their selection. We have a set of tags that are global and that can be used by all its fragments, and tags that are local to each fragmentId (so we don't completely fill up the global tags with labels that are only used for fragments with a specific fragmentId).

This too allows animators to aid in deciding how many variations or states are needed to portray accurately a specific state, and have that easily selected through code by just enabling or disabling tags.

In our case we will want to mark fragments that are to be played only when crouched with the Crouch tag and the fragments that should only be played when standing with the Stand tag.

When selecting a fragment we need to give the system enough information on which tags are active so that it can play the best fragment for a specific situation. We store the global tags for our character in the animation context, and we directly request "fragmentId-specific tags" when we request a fragmentId. The following pseudocode illustrates this.

```

`
// Pseudo code
if ( crouched )
{
  SetGlobalTagOnAnimationContext( "Crouch" )
}

// "Hit" is the fragmentId
// "FromLeft" and "ByExplosion" are tags specific to the "Hit" fragmentId.
QueueInActionController( "Hit", "FromLeft+ByExplosion" )

`

```

For completeness, the real code would look like this:

```

`
CRY_ASSERT( m_pAnimationContext );
CRY_ASSERT( m_pActionController );

if ( isCrouched )
{
  const TagID crouchTagId = m_pAnimationContext->state.GetDef().Find( "Crouch" );
  if ( crouchTagId != TAG_STATE_INVALID )
  {
    m_pAnimationContext->state.Set( crouchTagId, true );
  }
}

const FragmentID hitFragmentId = m_pAnimationContext->controllerDef.m_fragmentIDs.Find( "Hit" );
if ( hitFragmentId != FRAGMENT_ID_INVALID )
{
  TagState hitFragmentTags = TAG_STATE_EMPTY;
  const CTagDefinition* const pHitTagDefinition = pActionController->GetTagDefinition( hitFragmentId  );
  if ( pHitTagDefinition )
  {
    const TagId fromLeftTagId = pHitTagDefinition->Find( "FromLeft" );
    if ( fromLeftTagId != TAG_STATE_INVALID )
    {
      pHitTagDefinition->Set( hitFragmentTags, fromLeftTagId, true );
    }

    const TagId byExplosionTagId = pHitTagDefinition->Find( "ByExplosion" );
    if ( byExplosionTagId != TAG_STATE_INVALID )
    {
      pHitTagDefinition->Set( hitFragmentTags, byExplosionTagId, true );
    }
  }

  const int actionPriority = 0;
  IActionPtr pAction = new TAction< SAnimationContext >( actionPriority, hitFragmentId, hitFragmentTags );
  m_pActionController->Queue( pAction );
}

`

```

##
Adding the Crouch and Stand Tags

We will be using the global tags for adding the stance. In our case this is information that is important enough for all of our fragments to share; it has a very big visual impact on the pose of the character.

The global tags for our controller definition are stored in sampleTags.xml. We can edit them through the tag editor to add these new Crouch and Stand tags.

In the tag definition editor select the sampleTags.xml tag definition and click on the add new tag button.

![Image](https://www.cryengine.com/docs/static/attachments/23998393)

A prompt will appear requesting to give a name to the new tag.

![Image](https://www.cryengine.com/docs/static/attachments/23998392)

We will need a tag for each possible stance the character should be able to have.

![Image](https://www.cryengine.com/docs/static/attachments/23998387)

Since both tags are mutually exclusive, we will want to group them together, so they can never be active at the same time. It is a good idea to group tags whenever it is possible.

We can create a group by selecting the new group button.

![Image](https://www.cryengine.com/docs/static/attachments/23998389)

And giving it the name that we want. In our case Stance.

![Image](https://www.cryengine.com/docs/static/attachments/23998391)

Then we just need to drag and drop the Crouch and Stand tags into the Stance group.

![Image](https://www.cryengine.com/docs/static/attachments/23998390)

![Image](https://www.cryengine.com/docs/static/attachments/23998388)

Two tags in the same tag definition cannot have the same name. Even when they are in different groups.

We cannot use the
*
absence
*
 of a tag for fragment selection. For example, if we want to tag fragments to be selected when
*
not
*
 crouched we will need to encode such a state in a "NotCrouched" or similar tag. Similarly there is no support for a 'logical or' of tags, we only support 'logical and' currently.

##
Assigning Tags to Fragments.

When we are editing a fragment we can set the tags that we want it to have for its selection. By double clicking on a fragment to edit it in the fragment browser, the properties table under it will allow to select the tags we want to assign to it.

![Image](https://www.cryengine.com/docs/static/attachments/23998379)

Notice how when we change the tags, the fragment browser reflects that fact by placing the fragment in a subfolder with the name of the tag.

![Image](https://www.cryengine.com/docs/static/attachments/23998380)

We can repeat this so that we have each fragment categorized with the appropriate Stance tag.

![Image](https://www.cryengine.com/docs/static/attachments/23998368)

We usually have more than a single tag. A more complex example might look closer to this:

![Image](https://www.cryengine.com/docs/static/attachments/23998369)

##
Fragment Selection Details

(see specific article
[Fragment Selection Process](../Mannequin%20Concepts/Fragment%20Selection%20Process.md)
 for more details)

When an action gets installed on a scope it will try to find the fragment that should play on it.

It will need to do a query on the animation database (associated with the scope through the scope context) to find the fragment that best fits the request. The query information is a combination of fragment id, tags, and option index.

To resolve this query, the animation database will go through its entries that match the fragmentId, and will return the
**
first
**
 one it finds where
**
all the tags for the entry in the database are active in the tags specified in the query
**
.

Each entry in the database is a set of fragments with the same tags (options). To decide which fragment of this set of options is returned as result of the query, the option index is used (modulo number of options) to obtain a single fragment of the set.

Entries in the database are ordered based on their tags' priority, that's why the first match and best match are the same. Tags with a higher priority value are ranked higher. A fragment with a single tag of priority 2 has a higher priority than a fragment with twenty tags with priority 1. A fragment with two tags of priority 1 has a higher priority than a fragment with one tag of priority 1. The ordering between two fragments the same number of tags with the same priority distribution is undefined.

Since the best match search in the database heavily depends on the ranking of fragments and their order, it's important to be able to get a clear idea of how this looks like. We can see the order of fragments in the database by unchecking the Show Folders option in the fragment panel.

![Image](https://www.cryengine.com/docs/static/attachments/23998365)

The priority of a tag can be set in the tag definition editor by selecting a tag. Since the order in which fragments are stored in the database depends on the tag priorities, changing tag priorities might require resaving the databases.

Advanced (multiple scopes): When there is a fragment that takes over several scopes, it tries to query for and installs a fragment
**
once per scope context
**
. For example, if we are taking over FullBody+UpperBody it would do the query and the installation on the Fullbody scope and skip the UpperBody since they refer to the same scope context.

When we have multiple scopes, we can associate a tag to a scope in order to have a different fragment played on that scope. In this case, the tag of the scope becomes part of the required tags in the query to the database for that scope. This means that scopes that have tags associated have their own fragments.

##
Good Practices with  Fragments

In our database we now have all our fragments marked either with the Stance or Crouch tags. If we ran our example program now with the database in the current state, and request the "Idle" fragmentId, we would not obtain a matching fragment. This is because in our code we are not setting any tags in our animation context, so we have no fragment that has all its tags active in the global tags for the character.

Not having a match can be valid use case, but we must be careful. It's important to not allow this to happen by mistake in full body (base) layers, since this might translate in our characters going into T-Pose. We can make sure this never happens by having some default fragment to always fall back to. In our case we can remove the Stand tag so they become the default fragments for our fragmentIds.

![Image](https://www.cryengine.com/docs/static/attachments/23998370)

An equally valid solution is to keep the tags as they were before and duplicate fragments that are generic enough and make them the default fragments. In our case this would be the fragments tagged with "Stand".

##
Changing the Global Tag State.

To change the
[global tag state](../Mannequin%20Concepts/Mannequin%20TagState.md)
 from code to reflect our logical state we must do it through the animation context we created during the entity initialization.

```

`
// Example on how to set the Crouch tag on the global animation context
CRY_ASSERT( m_pAnimationContext );
const TagID crouchTagId = m_pAnimationContext->state.GetDef().Find( "Crouch" );
if ( crouchTagId != TAG_STATE_INVALID )
{
  const bool enableTag = true;
  m_pAnimationContext->state.Set( crouchTagId, enableTag );
}

`

```

If we place this code after the "Idle" fragmentID is started in the sample code (queued into the action controller and the action controller has resolved it during its update) we will observe that character does not play the fragment tagged "crouch". This is because Mannequin will not change the current fragment unless it is explicitly asked to. Actions need to be queued and installed (or SetFragment needs to be called inside an action) in order for the current fragment to change, and only then a fragment is placed in the scopes for playback.

We have several ways to make sure that we always are playing the best fragment for a specific situation. In our case, we want to automatically always have the best possible "Idle" fragment playing whenever the global tag state changes. There are two reasonable ways of achieving this goal: We can define on a fragmentId level that it should always be playing the best possible match, or we can write some code in the action to always select the best fragment for the current situation.

If we want to enforce it on a fragmentId level we just need to edit a fragmentId in the editor and select the Auto Update option.

![Image](https://www.cryengine.com/docs/static/attachments/23998364)

If we prefer to get more control we need to write a custom action. On each update, our action needs to check if there is a better fragment than the currently playing one. If that's the case, then it needs to request a new fragment. An action can re-queue itself by calling SetFragment, so there's no need to create a new action from within the action:

```

`
class CSampleAction
: public TAction< SAnimationContext >
{
public:
  typedef TAction< SAnimationContext > TBase;

  CSampleAction( int priority, FragmentID fragmentId = FRAGMENT_ID_INVALID, TagState fragTags = TAG_STATE_EMPTY, uint32 flags = 0, ActionScopes scopeMask = 0, uint32 userToken = 0 )
    : TBase( priority, fragmentId, fragTags, flags, scopeMask, userToken )
  {
  }

  virtual EStatus Update( float timePassedSeconds )
  {
    // Remember to call the base Update function!
    TBase::Update( timePassedSeconds );

    const IScope& rootScope = GetRootScope();
    const bool foundBetterMatchingFragment = rootScope.IsDifferent( m_fragmentID, m_fragTags );
    if ( foundBetterMatchingFragment )
    {
      SetFragment( m_fragmentID, m_fragTags );
    }

    return m_eStatus;
  }
};

`

```

We can queue this an action of this class instead of queuing one of the default class.

```

`
IActionPtr pAction = new CSampleAction( actionPriority, idleFragmentId );
m_pActionController->Queue( pAction );

`

```

The code we've written in our custom action's Update method is quite similar to what IAction::Update does when the current fragment is marked as auto update. The essential difference is that with our custom code we are enforcing this constraint (the best match will always be playing) not on a fragmentId level, but on an action level. There are advantages to both: It is useful to be able to use the auto update feature because we can use it with any custom action without having to explicitly add the code shown above, and it becomes data driven as we are depending on the fragmentId definitions. As for a main disadvantage, custom actions cannot easily override the auto update behavior for a FragmentId. If this restriction is acceptable, it is recommended to use the auto update flag instead of writing the check for "IsDifferent" yourself.

##
Starting Movement Fragments

To achieve our first goal of controlling the "Idle" and "Motion" animation states of the character we need to queue the "Motion" fragmentID when our character is moving and our "Idle" fragmentID when our character is stationary.

There are two main places were adding such control logic might be appropriate.

-
External control logic is starting actions: The movement logic for our character is controlled by the entity (for example via a state machine) and this control logic can start actions as we did for the Idle action.

-
Internal Action logic is setting fragments: The movement logic for our character should still be controlled by the entity in a similar way as in the previous case, but the control of the animation logic is left up to a custom action. In our case, we can write a custom action that would take into account the state of our entity (is it moving or stationary?) and then sets the appropriate fragmentID, option index, fragment-specific tags etc.
In the end, we commonly use a combination of both, with higher level control logic taking care of the generic action that should be started, and the internal action logic taking care of animation specific logic that might not belong on the higher level logic.

[Core Mannequin Classes](#core-mannequin-classes)
[Mannequin Setup](#mannequin-setup)
[Creating our Entity](#creating-our-entity)
[Adding Variation](#adding-variation)
[Changing the Global Tag State.](#changing-the-global-tag-state)
[Starting Movement Fragments](#starting-movement-fragments)
