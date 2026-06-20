# Tutorial - Preparing Geometry Normals to optimal results in Xnormal

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308611
- Page ID: 23308611
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Preparing Geometry Normals to optimal results in Xnormal
- Parent: Tutorial - Texturing

## Content

### Overview

This tutorial is about how to render hard surface objects tangents without splitting UV's, making it the cheapest and efficient way to create your UV's while maintaining a great result.

We'll use a more complex box for this example:

![Image](https://www.cryengine.com/docs/static/attachments/23999927)![Image](https://www.cryengine.com/docs/static/attachments/23999928)

First of all, we have to make sure that we have everything ready and our low poly UV's however we like, completely disregarding the splitting of hard edges.

We've connected as much together as we could like the small beveled edges etc which normally we would have to split because of the various smoothing groups we would assign to it.

![Image](https://www.cryengine.com/docs/static/attachments/23999926)

Instead of assigning different smoothing groups to define hard surfaces, we'll apply a single smoothing group to the whole object and only assign different smoothing groups to the various islands we have created the UVs for.

Meaning that every connected island receives it's own smoothing group.

![Image](https://www.cryengine.com/docs/static/attachments/23999918)

Rendering the normal map at this stage will gives us a bad result due to the various compensations we are going to get around the gradient areas.

![Image](https://www.cryengine.com/docs/static/attachments/23999921)

To combat theses common issues we are going to force the vertex normals to be flat before we start rendering by using the edit normals modifier.

To do that select the faces that are supposed to be hard edge/flat and average the normals so they straighten out.

![Image](https://www.cryengine.com/docs/static/attachments/23999922)

![Image](https://www.cryengine.com/docs/static/attachments/23999923)

![Image](https://www.cryengine.com/docs/static/attachments/23999924)

We have created a script where you are able to select multiple faces and do them all at the same time. You can download it here: [GetVertNormalsFromFace_0_2.ms](/docs/static/attachments/23999917)

Looking at the picture down below you can see the difference:

![Image](https://www.cryengine.com/docs/static/attachments/23999925)

Now you should be ready to start render out your normal map using Xnormal.

The normal map should render out with minimal compensation issues:

![Image](https://www.cryengine.com/docs/static/attachments/23999919)

And the final product below:

![Image](https://www.cryengine.com/docs/static/attachments/23999920)
