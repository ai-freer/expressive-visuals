---
name: expressive-visuals
description: Creative guidance for work whose value is primarily visual and experiential, including web pages, interactive pieces, 3D scenes and models, images, video, and animation. Use when conceiving, making, improving, or reviewing such work from source material, references, or concepts, and when rebuilding 3D assets or scenes from approved concept art or diagnosing why a render does not match it. Also covers modeling individual 3D forms, reconstructing scenes, and building original worlds through code, with Three.js as the main modeling and staging tool. For interactive 3D work, use it to design what a viewer can discover or change and how the scene responds. Usually unnecessary for routine UI maintenance or purely technical fixes.
metadata:
  version: "1.7.0"
---

# Expressive Visuals

Aim to make the work a perceptible, understandable experience with lingering resonance. Understand what is worth conveying, find a form that carries it, and design how the viewer encounters it. Expression grows from understanding and selection; making and viewing the actual work can also revise that understanding.

## Choosing a 3D approach

For questions of layout, rhythm, or atmosphere in a poster, page, or film, start with the [creative prompts](#prompts-to-revisit-while-creating). Use a 3D guide when the open question concerns fidelity to an image in 3D, building a form or scene, or what a viewer discovers by acting. The interaction examples also apply to 2D when the same action works on a page. Each guide can be used on its own.

- **What must match the approved image?** [3D Reconstruction from Concept Art](references/concept-to-3d.md) helps plan a reconstruction before the first render or diagnose a later mismatch in framing, proportion, occlusion, or light. Use it in the chosen tool, including Blender. An image offered only as inspiration leaves these decisions open.
- **How should the form or scene be built?** [Code-driven 3D](references/code-driven-3d.md) covers editable geometry, materials, light, and composition, with Three.js as the main tool. An original vase made for a single still can stop here. For a browser scene, this guide also covers what to ship and measure, even without interaction.
- **What will the viewer discover by acting?** [Code-driven 3D Interaction](references/code-driven-3d-interaction.md) connects a viewer’s action to a change they can see or hear. Try an action with a placeholder or an existing model: can turning a crank reveal something that the still image conceals? This applies to web exhibits, narrative pieces, and games.

Combine guides where the work crosses those boundaries:

| Brief | How to use the guides together |
|---|---|
| Reconstruct a vase in code from an approved image. | **Reconstruction + modeling:** identify the rim and shoulder the image constrains, shape them, then compare the same view. |
| Design an original mechanism the reader can operate. | **Modeling + interaction:** define the parts and pivots, then use their motion to show what the reader’s turn of the crank does. |
| Add exploration to an existing scene whose opening must match the concept. | **Reconstruction + interaction:** check the approved opening view; try the reveal and the return. Add modeling if the geometry itself needs work. |
| Build an explorable place in code from approved art. | **All three:** identify what the opening must preserve, build the space, then walk the route to judge what becomes visible, when, and why. Matching the opening frame does not establish that the route works or the reveal reads. |

Let the hardest part of the brief guide the next step. A face that must deform convincingly may benefit from an authored rig; a particular brush mark may be easiest to keep as painted; a still that depends on multiple light bounces may merit an offline render. If the handoff requires an editable Blender scene, plan for that source from the outset. Any of these choices can apply to one part of a larger Three.js work.

Choose evidence to fit the question: compare the intended view with the approved image, try a second edit to see which relationships hold, or watch a first-time viewer discover and repeat the action. A replay can verify the response without establishing that anyone understood it.

## Working definitions

Expressiveness is the capacity of form to make the qualities, relationships, emotions, and tensions in the content perceptible. *Yijing* (意境) is the whole experience that content, form, and viewing produce together: from what is concretely shown, the viewer senses a situation, temperament, or meaning and is left with associations that linger.

Borrow Yan Fu’s translation standard of fidelity, clarity, and elegance (信达雅): be faithful to the content and purpose, make the key meaning legible in viewing, and give the form fitting, distinctive affective power. The three interact. *Yijing* can be bright, severe, everyday, absurd, or the wonder of grasping a mechanism; the subject determines the temperament.

## Prompts to revisit while creating

These prompts span content, form, and viewing, and point to places you can design deliberately. Select, combine, downplay, or reinterpret them, or find approaches not listed. Do not run them in order, answer each one, or produce a separate analysis document. After thinking, choose the one or two things most worth feeling, and make them hold in concrete shape, space, light, material, or process.

- **What in the content is worth conveying?** Beyond characters, objects, and events, what values, worldview, and *yijing* can be read in the source? Which relationships, choices, changes, or costs move people? Separate what the material states from your own interpretation; ambiguity, contradiction, and the unknown can stay.

- **What entry point turns understanding into experience?** Given purpose, audience, and medium, look for a situation, action, image, spatial relationship, or process that carries the meaning. An episode, a gesture, an environment’s response, or even an absence can serve. Faithful depiction, distillation, recombination, and symbolism are all open; different readings can yield different works.

- **In a series or progression, what changes?** Beyond quantity and intensity, identity, body, range of influence, relationships, or mode of existence can change. Each thread can have its own axis of change; start and end can echo each other or turn meaningfully.

- **What visual language fits this work?** Choose among realism, abstraction, exaggeration, or other artistic approaches according to the content, purpose, and intended feeling. Shape, light and shadow, color, material, texture, and motion all shape style. Relate these choices to this work; harmony, contrast, and mixture can each carry meaning. A similar motif can gain its own character in a different subject through composition, relationships, and motion.

- **What makes this world tangible?** How do silhouette, proportion, scale, distance, and density express relationships and situation? Can posture, gaze, contact, and load make the connections between things believable? Where does the light come from, and what in this world emits it? How do overall illumination and local highlights form layers so that light and dark each mean something? How do materials respond to the environment, how does texture suggest touch and history, and how does motion show weight, force, and life? Watch how these factors interact, so detail adds meaning, credibility, or the pleasure of discovery.

- **What is the air of this situation?** Can environment, haze, dust, depth layering, color temperature, and sound place the viewer inside a mood? Atmosphere comes from situation, light, environment, and camera together; check that they point to the same feeling rather than reading as an isolated render effect.

- **What comes forward, and what recedes?** How visible must the key meaning be? Clarity can have hierarchy, and omission can express. Richness, simplification, occlusion, and empty space each have a role; a figure, an object, the environment, or the relationship between them can carry the center. Fit the viewer’s attention and imaginative room to the work.

- **How does the viewer relate to the work?** Being inside it, observing from outside, or acting within it each create a sense of position. How do viewpoint, distance, angle, perspective, and framing shape understanding and feeling? Approaching, looking out, looking up, passing through, or turning around create different situations. The camera also narrates: what it reveals first, what it withholds, its height and distance from the subject, and how it moves and pauses all shape the viewer’s relationship to the content. Interaction expresses too. Consider how attention is guided and how much room for exploration the viewer keeps.

- **How does feeling form over time?** Flow, deformation, speed, rhythm, pause, and stillness can convey qualities and emotion. After first sight, lingering, and exploration, does the work reveal new relationships or meanings? Give motion and the viewing process a character that suits the content, so individual moments add up to an experience.

- **If there is a reference work, what makes it move people?** Notice what content it chose, how it organized relationships, how it staged viewing, and why its form worked in that context; notice its trade-offs and limits too. Bring that understanding back to the current subject, purpose, and constraints to develop your own expression. Similar affective power can come from different shapes, styles, and methods.

- **What does the actual work convey?** Return to the visible frames and interactions. Notice where attention lands, which relationships hold, and which forms weaken the intent. From first sight, close detail, the full view, and after interaction, check whether the content is accurate, the key meaning is legible, and the intended effect happens. Watch whether local enhancement hurts overall readability, atmosphere, or coherence, and calibrate judgment by what viewing shows. For facts or mechanisms, check whether artistic treatment changes what the viewer understands.

These prompts point toward an expression that fits the current work; there is no single visual answer. Follow the user’s purpose, style, and technical choices, exercise judgment within the space the task allows, and land that judgment in visible results.
