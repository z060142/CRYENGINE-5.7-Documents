# Particle Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450622
- Page ID: 29450622
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Particle Nodes
- Parent: Flow Graph Node Reference

## Content

### AttributeGet

Returns the value of the specified Attribute.

![Image](https://www.cryengine.com/docs/static/attachments/65438697)

Input | Description
--- | ---
**Get** | Triggers the node.
**Attribute** | The name of the Attribute from which the value will be taken. Names are case sensitive, please make sure to type the names correctly.
Output | Description
**Value** | Outputs the value that was taken from the Attribute defined in the Attribute input.
**Error** | Outputs when an error occurs in the acquisition of the Attribute's value.

### AttributeSet

Changes the value of the specified Attribute.

![Image](https://www.cryengine.com/docs/static/attachments/65438696)

Input | Description
--- | ---
**Set** | Triggers the node.
**Attribute** | The name of the Attribute whose the value should be changed. Names are case sensitive, please make sure to type the names correctly.
**Value** | The new value that the Attribute's value will be set to.
Output | Description
**Error** | Outputs when an error occurs in the change of the Attribute's value.

[AttributeGet](#attributeget)[AttributeSet](#attributeset)
