# Code-driven 3D

Use Three.js to model a subject, compose it under a camera, and judge the result while the choices that produced it are still easy to change. For a bowl, this might mean pulling the shoulder inward and watching both its silhouette and the reflected light change. For a landscape, it might mean lowering a ridge until a distant summit appears. Both edits can be worth making for a single still.

Three.js is the core tool in this guide. Modeling through code is a broader practice: a Blender Python script or a Geometry Nodes graph can also preserve how a form was built. Three.js brings the model, camera, materials, and interaction into the same running browser scene. A human or coding agent can change a few profile points, inspect the source diff, and compare renders from the same camera. For a web piece, the study can grow into the delivered work. For another medium, carry it forward if it helps with the next revision or the required handoff.

## What the scene needs beyond Three.js

The browser supplies a canvas, graphics access through WebGL, frame callbacks, pointer and keyboard events, and audio processing through Web Audio. Three.js supplies a scene graph, cameras, meshes, lights, materials, and a [renderer](https://threejs.org/docs/pages/WebGLRenderer.html) that draws the scene from a camera. Consider selecting a lid behind display glass. The browser reports the pointer position. Scene code converts it to normalized coordinates within the active canvas viewport, then uses the current camera and a Three.js [raycaster](https://threejs.org/docs/pages/Raycaster.html) to find intersections with candidate objects, nearest first. The glass may be the first hit. Whether it blocks selection or lets the visitor lift the lid is a decision for the exhibit.

A vessel made for one still may need only its profile, glaze, lighting, and a saved camera. Render it again when one of those changes. A guided walk through a grove can follow a camera path; collision becomes useful if visitors can leave the path and a trunk should stop them. In Saltline, free movement and moving enemies justify capsule collision checks and a leg solver for a mechanical quadruped. Those choices follow from what the player can do and see. When a scene does need a controller or physics solver, an existing component that gives the intended behavior is a useful starting point.

## Start with an observation or an intention

**Modeling a known subject.** Use [records for the actual object or site](concept-to-3d.md#the-target-and-its-viewing-conditions) to constrain the dimensions that matter. A supplied catalog entry may already answer the question. For a museum vessel, a cataloged height can set the scale of the profile in model units. If a photograph is available, use it to place the mouth, shoulder, and foot in the target view. Without one, keep unmeasured profile points adjustable. A cataloged height alone establishes neither the profile nor the wall thickness. A small first implementation could revolve a handful of radius–height pairs into a mesh. Check the height and, where a reference view exists, compare those contours before adding glaze. An orbit can expose a pinched shoulder or a missing inner wall, but cannot prove that an unseen handle existed. An asymmetric handmade vessel may need different cross-sections around its axis; perfect symmetry is a modeling choice, not evidence.

**Inventing a subject.** Suppose the aim is to make a grove feel sheltered until the viewer catches sight of open sky. Begin with an eye-height camera, a dark canopy mass, two foreground trunks, and the shape of the opening. Try changing the lean of one trunk. If the opening becomes legible, that edit already serves the intention; thousands of individual leaves might not. For a still, judge the opening from the chosen frame. For a walk, also try the few steps where it first appears.

## Find a representation that makes the next edit meaningful

A few control points may be enough for one part; another may deserve a mesh shaped by hand. Choose a representation by the edit it should preserve.

| Visible decision | A representation to try | A revealing edit or view |
|---|---|---|
| A shell’s rim turns outward; its opening has depth. | Profile rings with editable cross-sections, an inner surface, and a distinct lip. | Change the opening while preserving the foot; inspect the rim from just above eye level. |
| A tree leans into a clearing while its roots grip a slope. | Branch curves with taper and attachment points; retain individually placed roots that define the pose. | Tilt the trunk. If roots float or the crown closes the clearing, the hierarchy is missing a constraint. |
| An arcade frames a courtyard. | Shared spring points and arch profiles, with the passage and head clearance specified separately. | Widen one bay. Supports, openings, and the path should still meet; repeated decoration need not stretch. |
| A folded-paper bird reads as alert. | A few faceted planes with explicit crease edges; an authored head where its silhouette matters most. | Turn the head slightly. Check the negative space under the beak before adding paper grain. |
| A field of abstract ribbons parts around a void. | Swept curves with a controlled twist and a reserved empty volume. | Vary density while holding camera and seed fixed. Does the void remain the focus? |

In Three.js a profile can become a lathed mesh, a path can carry a tube, and irregular surfaces can use explicit vertices and faces in a buffer geometry. Keep the curves, landmarks, dimensions, or seed alongside the generated mesh when they carry the intended edit. If one local correction requires retuning many unrelated parameters, a direct vertex edit, a sculpt, or a painted asset may be the more faithful source for that part.

For a hinge, use the same axis to place the pin, bore the bearing, and turn the arm. Lengthen the arm, then sweep it through its arc: a centered pin establishes alignment; a casing that catches halfway through reveals a separate clearance problem. Reuse whatever relationship should survive the edit. The ribs of the giant in [The Clockmaker’s Heart](https://claude.ai/artifact/6MjtQjf4ee1ZZjEpafaEpa) illustrate the complementary choice: each curve can be shaped for this particular chest while its ends still meet their sockets.

## Build out from a shape to a scene

Work outward from silhouette and connections to the view they make together. Block in the main masses from the intended eye height. In a still, which edges frame the subject? Along a route, what hides the destination, and at what point does it come into view? In [Saltline](https://claude.ai/artifact/BGY1SztrAYcJQHSsnHHGmp), gaps between containers reveal distant cranes whose silhouettes also appear in puddles. Changing the gap changes the route, the view, and the reflection. Judge those relationships before detailing the container walls.

Let the closest *intended* view set the scale of detail. A bearing edge that catches light in close-up earns its bevel; a row of bolts hidden in every intended view may need no geometry. In an explanatory model, a cutaway or enlarged feature can make a relationship legible. Mark any departure from scale that would change the viewer’s understanding.

Organize the source around things one might ask to change: the path through the scene, the profile of the seat, the gesture of a figure. Give generated objects stable identities and local frames. A separate seed per object keeps an added tree from rearranging all the others. [Instancing](https://threejs.org/docs/pages/InstancedMesh.html) can help when many objects share geometry and material; it offers little to a one-off silhouette. Preserve movable pivots and individually selectable parts when combining geometry.

### Working with authored assets

Choose the source of each part by what someone will need to revise. A path that must bend around a new clearing suits a generator; a particular hand gesture may be easier to preserve in an authored rig and clip. A mesh generated offline can enter the browser as a GLB: keep the script if its dimensions must remain editable. In [What the water keeps](https://what-the-water-keeps.vercel.app/src/engine/boat-hero.js), a loaded boat mesh and a shader that paints its surface do different jobs. Either can change without rebuilding the other as long as their material assignments and coordinate conventions still agree.

For a glTF asset, use [GLTFLoader](https://threejs.org/docs/pages/GLTFLoader.html) with the decoder or texture loader its compression requires. Check units, axes, pivot, and contact against an existing scene object. A detailed render mesh need not double as a collision surface: a simpler proxy can describe a hull at the waterline. Derive both from the same dimensions, or overlay them after resizing to catch a growing gap.

For a handoff in the other direction, [GLTFExporter](https://threejs.org/docs/pages/GLTFExporter.html) can export supported meshes and materials. Reopen the export where it will be used and try the requested edit. A vase exported as a mesh may look identical yet have lost its editable profile; include the generator when that profile matters. Custom shaders may need baking or a material made for the receiving tool.

## Give different assets a common material language

Set a few relationships that should survive a change of asset or light: where shadow values sit, how far color shifts toward the light, which surfaces catch sharp reflections, and how contrast falls away with distance. In a painted night scene, a matte coat can stay readable in shadow while a small glass lamp carries the sharpest highlight. Put an imported figure beside a generated wall under the same light, then move them into the haze. If the figure stays bright while the wall recedes, inspect which material missed the scene’s fog before darkening the figure’s texture. A shared light or fog input leaves room for distinct pigments and finishes.

### Decide what a mark follows

Turn a glazed pot under a fixed light: a painted motif should stay on the same patch of clay while the highlight shifts across it. Choose the placement accordingly:

- **Scale:** a meadow’s broad dry patch belongs to the terrain, veins to the leaf, and fine roughness to its surface. Using one noise frequency for all three obscures scale.
- **Coordinates:** world space can carry the dry patch across tiles; local coordinates or UVs keep veins on a turning leaf. Screen coordinates suit deliberate image-space effects, but a screen-fixed mark will slide across an orbiting object.
- **Lifetime:** bake or cache stable detail; update wind, illumination, or a changing waterline as needed. Preserve an approved mark directly when a generator would discard its shape.

## Light for the intended reading

Use light as a diagnostic before committing to mood. With camera and material fixed, move a grazing light across a fold. A traveling highlight shows a change in shading; even a flat mesh with a normal or bump map can produce it. Disable those maps and inspect a section or the silhouette before reshaping the fold. A dark line that stays fixed may belong to pigment. A neutral material pass can reveal a poor section profile that saturated colors concealed. Color maps and roughness or normal data also have different [color-space requirements](https://threejs.org/manual/pages/color-management.html); changing the lights cannot correct a duplicated display conversion.

A broad reflected shape can reveal the shoulder of a pot better than many point lights. Where a pale rim disappears into a white background, try a narrow bevel, then a dark card for it to reflect. Change one at a time: the bevel gives the reflection space to turn, the card gives it contrast if the material’s reflection actually includes it. With a fixed environment map, put the card in the captured environment and regenerate the map; a dark plane added only to the visible scene will not change that reflection. On a rough glaze, a prefiltered environment (Three.js’s `PMREMGenerator`) supplies reflections at the appropriate roughness.

At landscape scale, put the distant sky, ground, and reflective surfaces in the same air. If the water meets the sky in an unexpected bright seam, compare the fog color used by the sky and by the reflection. [Tidewright](https://claude.ai/artifact/JTgyEMn7sn1q2riWrMb7D4) uses custom WebGL2: its reflection can simplify the clouds and still meet the sky at a common horizon color. In a Three.js scene, the sky and water materials can read the same horizon color even if they use different shaders.

Use [post-processing](https://threejs.org/manual/pages/post-processing.html) where it changes the reading in a useful way. A broad stroke may group a distant hillside and also erase the thin cable that explains how a bridge is held up. Vary stroke size with depth or protect the cable during compositing. Compare the pass on and off at fixed exposure, then move the camera: the hillside should hold together without the cable flickering. If the silhouette is weak in both versions, return to the form.

## Stage motion and contact

A still can stop at the chosen frame. For a moving view, block the moments on either side of a reveal and travel between them. A lamp at the edge of a boat can give the foreground scale; a lamp on its centerline may hide the bridge the viewer is approaching. Move the lamp before decorating the bridge. Across a change of scene, preserving the heading or a recognizable landmark lets the surroundings change without losing the viewer.

For moving contact, decide which state the parts share. A hand can follow the handle of an animated oar; the blade’s position relative to the current water surface determines when a disturbance begins and where it travels. Sample the same wave shape and time for rendering and contact so the blade meets the surface the viewer sees. Inspect entry, push, exit, and recovery, then shorten the stroke. A ring that appears on schedule while the blade is still in the air exposes two independent loops. If the viewer can take the oar, use [Code-driven 3D Interaction](code-driven-3d-interaction.md) to decide what stopping or reversing the stroke should do.

## Inspect the result and the next revision

**Still: is the bowl opening too narrow, or does the glaze make it look that way?** Save the finished view before editing. Reuse its camera pose and projection, output size and pixel ratio, lighting, and exposure. A camera saved with the scene can suffice; a named preset pays off when you revisit the view often. Once the assets are ready, render the unchanged bowl with a plain matte material from that camera. With a matched reference, compare the projected inner and outer edges. For an original still, use the intended reading instead: can you see the inner wall at delivery size?

If the outside contour fits but the matte opening is too narrow, try widening only the inner lip. Overlay the matte frames before and after: the inner edge should move toward the target while the outer edge stays put. If the opening already reads well in matte but disappears under the glaze, keep the profile, restore the glaze, and try changing the reflected light. In either branch, compare the finished frame with the saved original at delivery size. Did the opening become clearer without losing the shape of the rim?

**Walk: did the clearing change shape, or did it come into view later?** Save the short camera path through the grove with its viewing directions. For **composition**, capture both versions at the same distance along that path, facing the same way. For **reveal timing**, pick a recognizable cue, such as the distant summit clearing the canopy, and note the path distance where it first appears in each version. If it moves from 8 m to 11 m, the edit delays the reveal even if those two frames look alike. Watch the stretch at the intended travel speed to judge the pause and catch flicker between stills.

A saved path is enough for a static grove. If wind or player input changes the view, restore the relevant starting state and seed, replay any inputs at the same steps, and capture at the same *elapsed simulation time* (for example, after 120 updates of 1/60 s). Saltline’s object previews and benchmark route are examples for a scene that warrants them. Frame times answer a separate performance question; measure them on the intended device, since headless captures may use software WebGL.

To compare authoring routes, give each the same revision and the same features to preserve: *Lower the canopy but keep the opening to the sky, the silhouette of the nearest branch, and the path width.* Compare time to a convincing result and what else moved unintentionally. A small package, a close match to one image, and an easy second edit are separate achievements.

## Check the cost of drawing the scene

Compare the same camera route on the intended device at a fixed resolution and quality. Record median and tail frame times (p95/p99) and where the spikes occur. When trying adaptive quality, record the actual resolution. Halving both dimensions of a reflection target quarters its pixels but still requires scene submission and vertex work. If a lower resolution helps, isolate reflection, transparency, fog, and post passes; otherwise look at simulation, draw submission, synchronization, and the display’s frame cap.

A hitch on first approach to a new object can occur long after startup. Compare the first and second pass, then time generation, shader compilation, and upload separately. Across several restarts, track texture dimensions, mip chains, render targets, and resource counts; a 1024² RGBA8 texture is 4 MiB before mipmaps. If counts grow or effects double, check resource ownership, listeners, and looping sounds. Removing a mesh does not automatically [release its GPU resources](https://threejs.org/manual/pages/how-to-dispose-of-objects.html).

## Decide what travels to the browser

For a cam driven by a crank, if the only change is rotation, one compressed cam mesh sent once and rotated locally is a fair baseline. Compare that GLB with a profile and generator, giving both the same controls, target detail, and lighting. If readers can reshape the cam, give *both* versions that edit too; count any extra data or code and compare the cost of revising the shape. Code may save transfer or make revisions easier, but these are separate results. Keep a distinctive painted mark or recorded gesture as an asset when a recipe would lose its character.

For a hosted scene, distinguish raw build size from cold-cache bytes and requests, including libraries and assets; time the first useful view, and the first effective input if the work has one. Separate files can let a browser cache a model across visits. A self-contained HTML can suit an offline exhibit: open the promised local file with an empty cache and the network disabled, and visit the promised views. For a delivered still image, measure the image the audience receives; the modeling runtime need not travel at all.

Keep the editable source, recipes, seeds, pinned dependency versions, approved assets, build instructions, and a repeatable viewing or test route. These let the next maker reproduce both the package and the conditions under which it was judged.
