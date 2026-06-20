# Using Area Solid with Audio Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966495
- Page ID: 44966495
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Solid > Using Area Solid with Audio Entities
- Parent: Solid

## Content

- Create a Box as an AreaSolid object.
![Image](https://www.cryengine.com/docs/static/attachments/44966496)
- Now place an "AudioAreaAmbience" entity from the "Audio" group under the Create Object tab, and place the ambience sound entity near the AreaSolid Object.
- Select the ambience sound entity. Then, AudioAreaAmbience Properties can be displayed on the right panel as shown in the image below. Now fill the PlayTrigger and RtpcDistance properties.
![Image](https://www.cryengine.com/docs/static/attachments/44968805)
- Select the AreaSolid entity in the level, and then under the **Properties** tab click ** Pick** button in the ** Target Tools**field of the ** Area** section. Now select the Audio Area Ambiance entity that has been placed near to the AreaSolid to attach the ambience sound entity to the Solid object as a target.
- Try to modify the AreaSolid object with the Designer tool as explained above. If users want to visualize the sound to see how it works, they can type **s_DrawAudioDebug = abcdefvw** in the console. When approaching an open space in the AreaSolid Object, users will be able to see the red ball as follows.
- Every time the AreaSolid object is modified with the Designer Object, polygons consisting of the area solid will be transferred to the Engine side and users will be able to make sure that the interaction between the sound object and the AreaSolid object as a result of the modification.

### Useful pages about Sound system

[Audio CVars & Console Commands (5.6)](../../../../../Audio/Audio%20Overview/Audio%20CVars%20%26%20Console%20Commands.md)

[Audio Overview](../../../../../Audio/Audio%20Overview.md)

[Useful pages about Sound system](#useful-pages-about-sound-system)
