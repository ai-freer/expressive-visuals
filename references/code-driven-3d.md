# Code-driven 3D

Use Three.js to model a subject, compose it under a camera, and judge the result while the choices that produced it are still easy to change. For a bowl, this might mean pulling the shoulder inward and watching both its silhouette and the reflected light change. For a landscape, it might mean lowering a ridge until a distant summit appears. Both edits can be worth making for a single still.

Three.js is the core tool in this guide. Modeling through code is a broader practice: a Blender Python script or a Geometry Nodes graph can also preserve how a form was built. Three.js brings the model, camera, materials, and interaction into the same running browser scene. A human or coding agent can change a few profile points, inspect the source diff, and compare renders from the same camera. For a web piece, the study can grow into the delivered work. For another medium, carry it forward if it helps with the next revision or the required handoff.

## Start with an observation or an intention

**Working from a reference.** Suppose a ceramic vessel in a photograph looks top-heavy. Its projected outline and the visible ellipse of its mouth are observations; the depth of its hidden back and the thickness of its wall are hypotheses. The [reconstruction guide](concept-to-3d.md) helps fit the camera and decide which relationships the image actually constrains. A small first implementation could revolve a handful of radius–height pairs into a mesh. Compare the mouth, shoulder, and foot in the reference view before adding glaze. An orbit can expose a pinched shoulder or a missing inner wall, but cannot prove that an unseen handle existed. An asymmetric handmade vessel may need different cross-sections around its axis; perfect symmetry is a modeling choice, not evidence.

**Working from scratch.** Suppose the aim is to make a grove feel sheltered until the viewer catches sight of open sky. Begin with an eye-height camera, a dark canopy mass, two foreground trunks, and the shape of the opening. Try changing the lean of one trunk. If the opening becomes legible, that edit already serves the intention; thousands of individual leaves might not. For a still, judge the opening from the chosen frame. For a walk, also try the few steps where it first appears.

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

Let the closest *intended* view set the scale of detail. For an assembly that opens to inspection, attach the detail view to the part so that moving it preserves the framing. Show enough of the housing to explain where the part fits. A bearing edge that catches light in this view earns its bevel; a row of bolts hidden in every intended view may need no geometry. In an explanatory model, a cutaway or enlarged feature can make a relationship legible. Mark any departure from scale that would change the viewer’s understanding.

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

Use light as a diagnostic before committing to mood. With camera and material fixed, move a grazing light across a fold. A traveling highlight indicates relief; a dark line that stays fixed may belong to pigment. A neutral material pass can reveal a poor section profile that saturated colors concealed. Color maps and roughness or normal data also have different [color-space requirements](https://threejs.org/manual/pages/color-management.html); changing the lights cannot correct a duplicated display conversion.

A broad reflected shape can reveal the shoulder of a pot better than many point lights. Where a pale rim disappears into a white background, try a narrow bevel, then a dark card for it to reflect. Change one at a time: the bevel gives the reflection space to turn, the card gives it contrast. On a rough glaze, a prefiltered environment (Three.js’s `PMREMGenerator`) supplies reflections at the appropriate roughness.

At landscape scale, put the distant sky, ground, and reflective surfaces in the same air. If the water meets the sky in an unexpected bright seam, compare the fog color used by the sky and by the reflection. [Tidewright](https://claude.ai/artifact/JTgyEMn7sn1q2riWrMb7D4) uses custom WebGL2: its reflection can simplify the clouds and still meet the sky at a common horizon color. In a Three.js scene, the sky and water materials can read the same horizon color even if they use different shaders.

Use [post-processing](https://threejs.org/manual/pages/post-processing.html) where it changes the reading in a useful way. A broad stroke may group a distant hillside and also erase the thin cable that explains how a bridge is held up. Vary stroke size with depth or protect the cable during compositing. Compare the pass on and off at fixed exposure, then move the camera: the hillside should hold together without the cable flickering. If the silhouette is weak in both versions, return to the form.

## Extend into time or interaction when the work calls for it

A still can stop at the chosen frame. For a moving view, block the moments on either side of a reveal and travel between them. A lamp at the edge of a boat can give the foreground scale; a lamp on its centerline may hide the bridge the viewer is approaching. Move the lamp before decorating the bridge. Across a change of scene, preserving the heading or a recognizable landmark lets the surroundings change without losing the viewer.

For moving contact, decide which state the parts share. A hand can follow the handle of an animated oar; the blade’s position relative to the current water surface determines when a disturbance begins and where it travels. Sample the same wave shape and time for rendering and contact so the blade meets the surface the viewer sees. Inspect entry, push, exit, and recovery, then shorten the stroke. A ring that appears on schedule while the blade is still in the air exposes two independent loops. For viewer-controlled motion, also try stopping halfway: a held pose should retain its contacts while residual effects, such as ripples, can continue.

## Inspect the result and the next revision

Choose a comparison that could change the decision: a target-view overlay for a reconstructed outline; two canopy densities for an original grove; a light sweep for a material; a continuous turn for motion shimmer. Record the framing, seed, light, exposure, resolution, quality setting, and time where relevant. An object preview diagnoses a local fault; the composed scene shows whether the correction actually matters.

A small inspection view can make a visual disagreement reproducible. For example, a project might interpret `?camera=rim&seed=7&part=bowl&material=clay&light=side&time=0&dpr=1`: one named camera, the bowl alone, a neutral surface, and a fixed instant and pixel ratio. These are controls to implement where useful. Save the viewport size too. Change just the light direction for a sweep, then return to the full scene to see whether the fix survives its real lighting. For a moving piece, a repeatable camera path can expose shimmer between the saved frames. Headless captures may use software WebGL; measure frame time on the intended device.

To compare authoring routes, give each the same revision and the same features to preserve: *Lower the canopy but keep the opening to the sky, the silhouette of the nearest branch, and the path width.* Compare time to a convincing result and what else moved unintentionally. A small package, a close match to one image, and an easy second edit are separate achievements.

## Runtime and delivery for browser work

For a browser game, try the same movement at two render rates. A fixed simulation step with a capped elapsed delta and bounded catch-up can keep collisions consistent. For first-person mouse look, request pointer lock on a user gesture; use that gesture to start or resume the audio context where needed. Pause simulation on tab hide, clear held inputs on focus loss, and reset the time accumulator on return. A useful play check is to leave mid-action, come back, regain control, and listen for a doubled or missing sound.

| Cost | Useful evidence |
|---|---|
| Distribution | Raw build bytes, cold-cache transferred bytes, request count, external dependencies. |
| Startup | First visible frame and first usable input, with texture generation, uploads, and shader compilation timed separately when diagnosing a stall. |
| Frame time | Frame times along the same camera route at locked resolution and quality; record median, p95/p99, and where the spikes occur. Then try adaptive quality and note the actual resolution. |
| Resident resources | Texture dimensions, formats, mip chains, render targets, and resource counts after several restarts. A 1024² RGBA8 texture is 4 MiB before mipmaps. Use counts to spot growth across restarts. |

Halving the width and height of a reflection target quarters its pixels, but still incurs scene submission and vertex work. If lowering internal resolution helps, isolate reflection, transparency, fog, and post passes; if it does not, investigate simulation, draw submission, synchronization, and the display's frame cap. A hitch on first approach points to a different experiment: time the first generation, upload, and compilation of that object. Repeated growth after restart warrants checking resource ownership, listeners, and looping sounds; removing a mesh does not automatically [release its GPU resources](https://threejs.org/manual/pages/how-to-dispose-of-objects.html).

A single HTML can be a convenient artifact; separate files can make a larger scene easier to cache and update. Either can be built from readable modules with pinned dependencies. Keeping recipes, seeds, approved assets, build instructions, and the test route makes later editing possible. If offline play matters, open the promised entry point with a clean cache and the network disabled. A loaded title screen, a completed playthrough, a favorable visual review, and a measured device budget answer four different questions.
