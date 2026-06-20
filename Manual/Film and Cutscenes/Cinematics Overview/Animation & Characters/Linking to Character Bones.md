# Linking to Character Bones

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874184
- Page ID: 26874184
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Animation & Characters > Linking to Character Bones
- Parent: Animation & Characters

## Content

##
Overview

You can attach entities to characters by creating a bone attachment link. This is useful when your character is picking or moving objects and then placing them back in the scene. The existing
**
entity link
**
 system has been extended for the bone attachment.

##
Step-by-step

-
The bone attachment link is manipulated by using the existing link/unlink tools.

-
Make sure your entities are named properly - this prevents any err when linking.

-
You can already place your object that you want to link to the character, in this example it's placed near the right hand of the character. It does not need to be accurate but close enough, as you can always adjust the object later after the link is created.

-
When linking, if you press a
**
shift
**
 key and the target entity has a skeletal mesh, it displays the list of bones as a popup like below:

-
If you select a bone to attach from the list, the purple link line is show with the name of the bone attached above.

(Notice that the link line correctly points to the right hand bone of the character instead of to the center of the entity.)

-
Once done, make sure you turn the link button off. Select another object and select the object(Gun) back. You can confirm that an entity link has been created actually in the 'Entity Links' section of the panel.

(
**
The prefix '@'
**
 is essential. It's used to identity the link as a bone attachment link. So,
**
do not make a normal entity link that starts with '@'
**
.)

-
You can always rename the link name to the bone you want it to be connected to.

-
In this case, renamed the link so the bone is attached to the weapon_bone (Still kept the '@' intact in the naming).

-
If you want to break a link, you can use the unlink tool as usual.

##
Bone link transformation control by a TrackView sequence

-
Usually a TrackView sequence controls the local transformation of the entity. (e.g. in the usual linked parent-child relationship)

-
So there is a special local transformation control support for this kind of link in the movie system.

-
Basically if you add a bone-linked entity to a sequence, you can see something like the below:

-
The part from "-@" shows this'll be processed specially since it's a bone-attached entity.

-
You can add an animation to your character and to your linked object.

-
You can preview the link while scrubbing or playing the trackview sequence. If required, you can adjust the linked object's placement without repeating any of the steps above.

-
If you want to transform the entity in world coordinate (though the use case for this set-up is hard to imagine), you can do it by using the context menu as below:

-
Then the node title shows it's no longer in the special mode:

-
You can go back to the local transformation mode by using again the context menu:

##
Caveat

Since it's based on the entity link, it can only connect two entities. If you want to link a non-entity to a bone of an entity, you should use a dummy entity and a normal parent-child link additionally.

[Step-by-step](#step-by-step)
[Bone link transformation control by a TrackView sequence](#bone-link-transformation-control-by-a-trackview-sequence)
[Caveat](#caveat)
[Step-by-step](#step-by-step)
[Bone link transformation control by a TrackView sequence](#bone-link-transformation-control-by-a-trackview-sequence)
[Caveat](#caveat)

##
Overview

You can attach entities to characters by creating a bone attachment link. This is useful when your character is picking or moving objects and then placing them back in the scene. The existing
**
entity link
**
 system has been extended for the bone attachment.

##
Step-by-step

-
The bone attachment link is manipulated by using the existing link/unlink tools.

-
Make sure your entities are named properly - this prevents any err when linking.

-
You can already place your object that you want to link to the character, in this example it's placed near the right hand of the character. It does not need to be accurate but close enough, as you can always adjust the object later after the link is created.

-
When linking, if you press a
**
shift
**
 key and the target entity has a skeletal mesh, it displays the list of bones as a popup like below:

-
If you select a bone to attach from the list, the purple link line is show with the name of the bone attached above.

(Notice that the link line correctly points to the right hand bone of the character instead of to the center of the entity.)

-
Once done, make sure you turn the link button off. Select another object and select the object(Gun) back. You can confirm that an entity link has been created actually in the 'Entity Links' section of the panel.

(
**
The prefix '@'
**
 is essential. It's used to identity the link as a bone attachment link. So,
**
do not make a normal entity link that starts with '@'
**
.)

-
You can always rename the link name to the bone you want it to be connected to.

-
In this case, renamed the link so the bone is attached to the weapon_bone (Still kept the '@' intact in the naming).

-
If you want to break a link, you can use the unlink tool as usual.

##
Bone link transformation control by a TrackView sequence

-
Usually a TrackView sequence controls the local transformation of the entity. (e.g. in the usual linked parent-child relationship)

-
So there is a special local transformation control support for this kind of link in the movie system.

-
Basically if you add a bone-linked entity to a sequence, you can see something like the below:

-
The part from "-@" shows this'll be processed specially since it's a bone-attached entity.

-
You can add an animation to your character and to your linked object.

-
You can preview the link while scrubbing or playing the trackview sequence. If required, you can adjust the linked object's placement without repeating any of the steps above.

-
If you want to transform the entity in world coordinate (though the use case for this set-up is hard to imagine), you can do it by using the context menu as below:

-
Then the node title shows it's no longer in the special mode:

-
You can go back to the local transformation mode by using again the context menu:

##
Caveat

Since it's based on the entity link, it can only connect two entities. If you want to link a non-entity to a bone of an entity, you should use a dummy entity and a normal parent-child link additionally.
