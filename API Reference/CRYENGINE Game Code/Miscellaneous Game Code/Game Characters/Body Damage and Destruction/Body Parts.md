# Body Parts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306586
- Page ID: 23306586
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Game Characters > Body Damage and Destruction > Body Parts
- Parent: Body Damage and Destruction

## Content

### Overview

Body part xml files can be found in this folder: `GameSDK/Libs/BodyDamage/`

Any number of files can be created, usually one per character type is enough. The naming convention is the following: *BodyParts_NameOfCharacter.xml*

For example:

- BodyParts_AlienGrunt.xml
- BodyParts_CryNetOps.xml

These files will be usually edited by tech artist together with game designers. They define a mapping of character bones and attachments to 'body parts', more meaningful for gameplay.

### File Contents and Structure

Let's explain it with an example. The following is a collapsed version of the body parts setup for the alien grunt.

```
<BodyDamage>
<Parts>
<Part name="armor">
<Attachment name="armor_chest_l" />
<Attachment name="armor_chest_r" />
<Bone name="L Arm01" />
<Bone name="L Arm02" />
<Bone name="L Arm03" />
<Bone name="L Arm04" />
...
</Part>
<Part name="armorHead" flags="headshot">
<Attachment name="armor_head" />
</Part>
<Part name="jellyBack">
<Bone name="jelly_back_proxy" />
</Part>
<Part name="jellyBody">
<Bone name="jellyBone" />
</Part>
<Part name="jellyHead" flags="headshot">
<Bone name="Head" />
</Part>
<Part name="tentacles">
<Bone name="Rope01 Seg01" />
<Bone name="Rope01 Seg02" />
<Bone name="Rope01 Seg03" />
...
</Part>
</Parts>
</BodyDamage>
```

### Part

A **Part** definition requires a name, and a list of character bones and/or physicalized attachments (armor plates, helmet...). This is just a mapping which allows the body damage system to map a specific hit/collision against a bone/attachment, to a 'body part'.

These body parts then, will have damage multipliers associated to them. So when something hits a collider volume, the system will check which bone controls this collider volume and looks up the corresponding 'part' name.

#### Part flags

Body parts can be flagged as 'headshot', 'foot', 'knee', 'pelvis' or 'weakspot'. This is just used by other systems, like awards ones, to identify more specific and special hits.
