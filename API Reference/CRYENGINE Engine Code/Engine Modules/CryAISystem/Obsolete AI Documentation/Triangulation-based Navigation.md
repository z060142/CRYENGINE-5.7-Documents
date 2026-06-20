# Triangulation-based Navigation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306468
- Page ID: 23306468
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Triangulation-based Navigation
- Parent: Obsolete AI Documentation

## Content

This documentation is obsolete and applies to the pre-
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048672](
MNM
)
 navigation system AI used in CRYENGINE 3.3 and earlier.

##
Overview

The CryAISystem uses a non-directed graph as the basis of its spatial representation. Parts of this graph are calculated in a pre-process step in the CryENGINE Sandbox, and some are processed in real time as the game executes. The properties of this graph and how it is used to generate paths and navigation is discussed in this section.

##
General properties of the graph

A graph is a data structure that consists of two data types – nodes and links. The nodes represent the repositories of the data organized in the graph, while the links provide connections between the nodes (and thus between the data contained within the nodes). A non-directed graph means that there are no directions associated to the links (or that every link is bidirectional) - in essence when one node is connected to another that automatically implies that the other node is also connected to the first.

In the CryAISystem, the graph nodes represent a certain portion of space that is clear of obstacles. The data they contain describes this portion of space using some properties. The links contain data that is used to calculate whether a certain agent can pass from one node into another – so they are not just simple links but they also contain data - like the nodes. There are no limits to the amount of links a node has.

Nodes can be created in two ways - there is the automatic generation of nodes using a triangulation procedure (obstacles are triangulated on the map), which generates about 90% of the graph. The user does not directly affect this operation and it can be initiated from within the CryENGINE Sandbox; this is a pre-process step. The second way to create nodes in the graph is by manually placing them in the CryENGINE Sandbox and then manually linking them together to the underlying automatic generated graph.

The auto generated graph ALWAYS HAS TO EXIST, even if the map is completely empty. Within the CryAISystem, the graph is never 0 - it always contains at least one node that describes the whole game world.

##
Triangulation

The generated triangulation is the core of the navigation algorithm. It is performed in order to calculate the initial graph, which can then be modified by the user or used as is. The basic principle behind the triangulation is that it creates a triangle between each three obstacles that are in some proximity to each other. The resulting triangle consists always of free space that the agents can move through, because the vertices of the triangle are the obstacles themselves. The edges of the triangles govern where the agents can pass from one triangle into the adjacent one. The triangles then become nodes of the graph and the edges become links between the triangles.

Why was triangulation chosen? Even though it provides a reasonable approximation to the actual game space, it takes up the smallest amount of memory since it packs vast open spaces without obstacles in a single triangle. It does not require that the designer of the level spend a lot of time placing manual waypoints (although this is still a possibility for designers that really want to control the environment). Finally, the triangulation topology lends translates very elegantly into a graph, and the operation and the way paths are calculated are easy to grasp within a triangulation (hopefully).

Following is a detailed description of all the sub steps that are performed in order to generate a final graph. Every step will be accompanied with an example that will try to explain the procedures in a more visual way.

When an empty level is created, its triangulation is non-existent. However, the graph still contains one dummy node that represents the whole empty level. If a triangulation is generated on an empty map, it will create dummy obstacles on the edges of the map (in total 4) and will generate 2 big triangles that connect these 4 dummy obstacles. Thus the graph will contain a total of 3 nodes - the one dummy node that is always created - plus the two nodes each of which describes one of the triangles. The two triangle nodes would have one link each to the other, while one of them (the one that is created first) will also contain a link to the initial dummy node.

When a triangulation is initiated on a normal level (one with obstacles), the first step is to request from the physics subsystem ALL physical entities that collide with the player (e.g. obstacles). All the obstacles returned are taken as simple points (without volume). The point position taken for the triangulation is the origin point in the objects local space. Note that in this step the size of the actual obstacle or its shape is not relevant - so big buildings and small rocks are all handled in the same way - as a point.

This set of points received from the previous step is put through a triangulation process that generates a triangulation of the points in 2D. This triangulation is something similar to a Delaunay triangulation, although it is not quite the same. The Delaunay triangulation has some more strict rules about the properties of the triangles that come out as a result of the triangulation. A demonstration of the process of the triangulation can be found in many places on the Internet (
[http://cage.ugent.be/~dc/alhtml/Delaunay.html](
http://cage.ugent.be/~dc/alhtml/Delaunay.html
)
). This is performed offline (as a pre-processing step) as it can be potentially very time consuming (depending on the amount of obstacles and their distribution).

The triangulation generated in the previous step is used to create the navigational graph. Each triangle is translated into a node (its geometrical center is taken as the position of the node) and each triangle node is connected to the nodes of all its adjacent triangles. Basically, these are all the triangles (actually exactly 3) that share an edge with the node's triangle. The nodes also record properties of the triangles at this point that may or may not be used during pathfinding (does the triangle border a water area, the slope of the triangle etc). With this procedure an early version of the navigational graph is created with the following properties:

-
Each node has exactly 3 links (except one node that has been created initially which also links to the dummy initial node that is always created).

-
The links describe a sort of spatial relationship between the triangles - in other words they can now easily determine which triangle is neighboring which.

-
The triangulation itself represents a 3D plane that follows somewhat the surface of the terrain (how closely depends on the obstacle distribution)
At the end of the previous step we have a working graph that represents some kind of spatial information, but it's incomplete as it regards all obstacles as points. Also there has been no influence from the game designer thus far to put some areas of the map out of reach for the enemies. To remedy this situation, the designer can place Forbidden Areas in the CryENGINE Sandbox, which are processed next.

##
Forbidden Areas

In every game there are areas where the designer would like to keep the enemies out. Examples for this are water surfaces, steep hills, ravines, etc. To make it possible to indicate to the AI enemies in CryAISystem that they should not go into some certain areas the designer can use Forbidden Areas.

The Forbidden Areas are 2D shapes that consist of three-dimensional points. What that means is that while the forbidden area doesn't necessarily need to be flat, the difference in the z coordinate for the points is irrelevant - the closes analogy is that the areas are infinitely high prisms. The edges of the forbidden areas define infinitely high walls that the enemies can never cross. The area enclosed by the forbidden area is NOT actually forbidden. An enemy can freely be spawned there and he will work normally. BUT, no one from outside of the forbidden area will be allowed in, and no one from inside of the forbidden area will be allowed out.

In this sense, it would be better to call these areas Forbidden Shapes to indicate that it is indeed the edges of the shape that are forbidden to cross - but the name is historic. An enemy inside a forbidden area will not make an effort to exit it.

If some enemy tries to generate a path whose destination would take him outside of the forbidden area that is enclosing the enemy, the path will be quickly rejected as impossible. The same will happen if an enemy tries to generate a path whose endpoint is within some forbidden area that doesn't include the enemy as well. It has to be said however that enclosing enemies inside forbidden areas is not a good idea as their primary purpose is to enclose portions of the map where the designer does NOT want the enemies to be. Consequences of not following this advice are given here.

Edges of forbidden areas are included into the triangulation graph after it has been created. As edges are added to the triangulation, triangles are split accordingly making it so that every forbidden area edge always coincides with the edges of one or more triangles. The links created that correspond to these forbidden edges are specially marked as forbidden (not passable). As a result, the triangulation generated in the first step gets fragmented to smaller triangles along the forbidden areas edges. The graph is kept in a stable state after each edge is added, so it is possible to have non-closed forbidden areas. Unfortunately in the present code state of CryAISystem this is not supported - all forbidden areas are assumed closed automatically.

##
Link Data

Finally, the last step of the automatic triangulation is to analyze the edges of every triangle and determine which part (if any) of the edge length represents empty (passable) space, and which part is not empty (but inside an obstacle). This is the step in which the actual volumes of obstacles are taken into consideration, and depending on the number of incident triangles to an obstacle vertex in the triangulation a more or less accurate approximation of the obstacle's volume is created. At this stage, all obstacles are abstracted as infinitely high prisms and only the space between them along a triangle edge is marked as passable.

When an enemy generates a path through the graph, it also analyzes the links of the nodes as it traverses them and makes sure that it can “fit” in the empty area of the edge between the two triangle nodes before it takes the next node into consideration. Edges that have been created as a result of the addition of the forbidden areas are automatically marked with a negative amount of free space so that implicitly means they can never be crossed.

The analysis of the edges is done by shooting a beam (fat ray) from the first vertex on a triangle edge towards the second and recording the point the beam hit the obstacle that is represented with the second vertex. Then the same is done from the second vertex towards the first vertex obstacle. The two collision points are compared and the distance between them calculated - which can be negative if the two obstacles overlap. If the distance is positive, then it represents the maximum value for the diameter of an upright cylinder that can pass from one triangle into another through this edge.

The information about the diameter is stored in the link itself, and that means that in some way the links are weighted from the start based on the edges that they represent.

This is the last step before the finalized graph is written into a file. These files are with the extension .bai (binary AI) and they are loaded as-is in the game itself, so it is responsibility of the designer of the level to keep his .bai files up to date.

##
A small triangulation example

Because long drawn out discussions about what does what in a computer program can be too much to read, here is a simple example that illustrates how the triangulation works and what is done at what step. It is important to understand the triangulation in order to understand how to make the enemies behave in the most believable way. The example is given in 2D because essentially the triangulation operates on a 2D plane, which is the terrain plane. How to extend it to 3D is discussed later in this chapter.

Our example setup looks like this obstacle course represented in the following figure. The obstacles are the grey polygons, and the origins of their local spaces are represented with a black dot. The forbidden areas in the picture are shown in red colour. We will follow the complete triangulation of this simple setup step by step.

As discussed above, in the first step all obstacles are enumerated from the physics sub system and their positions (the black dots on the picture) are taken. These are then triangulated into triangles to receive the result in the following picture (Note that dummy objects have been placed on the edges of the world to enclose it):

The obstacle volumes are grayed in order to show that for this stage they are not relevant. To illustrate where forbidden areas are indeed needed, we will skip the step that adds the forbidden areas (since there are none yet) and go ahead and calculate the pass properties of each triangle edge - to get an idea of how we approximate the volumes of the obstacles. We would get something that looks like this:

We can see from this picture that not all shapes are approximated in a satisfactory way (especially shapes elongated in one dimension). An example of a particularly bad approximation is the red polygonal obstacle - we see that if we regard all triangles as areas of empty space (without obstacles) we would be wrong in at least one triangle. For maps with a big amount of obstacles (like a typical CryENGINE map that has a lot of vegetation) the number of incident triangles per vertex is bigger, and the obstacle volumes are more convex - so usually the approximation is good enough. In general though, the approximation is only as good as the amount of incident triangles - more triangles, better approximation. This is illustrated in the following image where the same obstacle is shown to be approximated good and bad.

Here is where we can make manual adjustments by defining a forbidden area around the obstacle that approximates bad (with experience, one can usually tell which shape would be problematic by just looking at the obstacle - buildings and all BIG objects are always prime candidates?). The forbidden area provides a simple and controlled way to locally influence the triangulation and make it possible for it to generate a better approximation of the environment. As will be discussed later, during generating of the path the agents "think" that the obstacles are a little bigger (it's a sort of Minkowski sum of the approximated polygon and a sphere that depends on the size of the agent and how it is configured in regard to how close to the obstacles he wants to pass) but still for obstacles that are really poorly approximated one needs to define a forbidden area.

All this being said: if we define a forbidden area around the obstacle shown in red in the diagram and we get the following result.

Notice that the forbidden area also contains triangulation inside of it (the approximated shape of the problematic obstacle is made transparent for that purpose). The problematic obstacle is now ideally approximated (by the forbidden area) and no agent will be allowed to step inside it. The addition of the forbidden area also added more points to the triangulation (all vertices of the forbidden shape) and this also refined the approximations of the surrounding obstacles, since now there are more incident triangles (for example the bottom leftmost obstacle and the top leftmost obstacle).

To see how this calculated spatial representation translates into a graph that is stored in memory and then used to pathfind and navigate, the following diagram superimposes the graph on top of the result of the triangulation.

The graph contains one additional node (marked as white on the picture). This is the so called safe node. It is always valid and cannot be deleted by anyone but the graph itself and is supposed to be used to always have an entry point into the graph that is guaranteed to be connected to the rest of the graph. Since there is no root node for the graph, the last returned node from a graph query is stored as such. That node is called the current node. Since sometimes it might point to a deleted node or even to null, the safe node provides a guaranteed way to get back into a valid portion of the graph.

The final observation to be made is that the nodes of the graph correspond to triangles in the triangulation, and the links of the graph correspond to triangle edges. The links themselves hold information about the edge that they describe (how big it is, what portion of it is free space etc). This information is critical during pathfinding and path beautification.

##
Path finding

The pathfinding algorithm uses a standard A* algorithm (
[http://encyclopedia.thefreedictionary.com/A-star%20algorithm](
http://encyclopedia.thefreedictionary.com/A-star%20algorithm
)
) implementation to generate the path. It works on top of the spatial representation described in the previous text.

The procedure to generate a path from one point to another is simple: first, both points are located in the graph (read this note about point location search in the triangulation). What this means is that the nodes of the graph that correspond to the triangles which contain both points are selected. One of those nodes is marked as the start node and the other as the end node. Then the A* algorithm is executed on the graph having these nodes as end nodes. The A* can use different kinds of heuristic, but most commonly it uses a simple greedy distance heuristic. The algorithm will return the optimal path through the graph from one node to the other, or at the very least it will determine that a path is not possible.

A path can be impossible if the two end nodes are on opposite sides of a forbidden area. Links that lead over forbidden area edges are not passable and are marked as having infinite cost (in the picture of the example triangulation they are colored red).

During the A* pathfinding process, care is taken to make sure that the object requesting the path can indeed pass a certain link to another node before that node is considered. To this end, links have a lot of properties that aid during pathfinding and make it easy to calculate whether a particular path requester can "fit" through the edge.

When a path is found, it is often not of a high enough quality to be taken as is for the AI object to traverse. This is a natural side effect of triangulation, as paths can be sometimes very "broken up", with fairly large turns between points. To remedy this, a second pass is done on the generated path in order to straighten it as much as possible to facilitate more realistic movement of AI Objects when they traverse it. This operation is called path "beautification".

##
Beautification of the path

Beautification of the path is an option that the system offers. It is accessible via a console variable (
**
ai_beautify_path 0/1
**
). The beautification procedure is a very simple procedure that checks whether it can skip certain points generated in the previous pathfinding step, if they are not really needed. A point in the path is not needed it if is possible to move in a direct line (without hitting and obstacle, that is) from the point before it to the point after it.

Even if no points can be skipped entirely, there is still the possibility that the simple path strays too far away from some obstacles because the triangles around it are big. In that case, the beautification procedure will make sure that the path is as tight as possible around every obstacle without actually hitting the obstacle itself.

The proximity to any obstacle that the beautification process tries to maintain can be completely configured by setting the radius of the requester of the path to different values. A requester with a bigger radius will stay further away from the obstacle than a requester with a smaller radius. In practice, the radius has to roughly correspond to the size of the object, since making it much bigger will create the problem that the object cannot pass a lot of graph links. But also making it smaller will cause the objects to "think" they can pass some links while in reality they cannot - thus they will get themselves stuck.

##
A pathfinding example (triangulation example continued)

**
Point location in the triangulation graph
**

The triangulation is continuous over the full size of the map. This means that there are no "holes" in the triangulation that have no triangles. Even triangles that are inaccessible from ALL their neighbors are still stored in the triangulation graph. This makes point location queries really fast and not dependent on the actual distribution of the triangles and obstacles in space.

The point location algorithm tries to locate which triangle contains the desired point. To this end, it starts at the current node in the graph and at every iteration selects the next graph node (or triangle) that gets it closer to the point. The selection is based on a simple triangle property: the normal vectors of the 3 triangle edges are considered and the one that points in the closest direction to the target point is selected as the link that will be followed to the next node.

Since the angles between all three normal vectors of the triangle edges will always amount to 360 degrees, we are guaranteed to find the best next node that takes us closer to the target point if we just select the one that points in that general direction.

This algorithm is really fast and has the property of quickly converging on the destination triangle. At every step of the algorithm the point is tested for inclusion into the current node's triangle.
