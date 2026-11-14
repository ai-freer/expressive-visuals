# Expressive Visuals

[English](README.md) | [中文](README_CN.md)

A heuristic creative skill for work whose value is primarily visual: web pages, interactive pieces, 3D scenes and models, images, video, and animation.

It prompts across content, form, and viewing. Start from the values, worldview, relationships, and *yijing* (意境, the lingering mood a work evokes) in the source material or concept; find an entry point and axes of change; then consider visual language, shape and space, light and atmosphere, camera, attention, the viewer’s relationship to the work, and how experience unfolds over time. Finally, land the judgment in visible results. Reference study and viewing the actual work can also deepen understanding.

These open prompts widen creative choices. Use them as the task requires; there is no need to answer each one, cover them all, or submit a separate analysis document. They preserve the model’s own understanding and creative judgment and do not prescribe a single style or model-specific method.

## Choosing a 3D guide

For a poster, typographic page, or film, start with the [creative prompts](SKILL.md#prompts-to-revisit-while-creating). Choose a guide below when its question is open; each stands on its own.

| Start with | Use it on its own when… |
|---|---|
| [3D Reconstruction: Concept Art and Real-World Sources](references/concept-to-3d.md) | Plan a reconstruction or diagnose a mismatch. For a real product, building, or landmark, start with the records at hand and seek additional primary sources where a dimension, version, or layout remains uncertain and matters to the work; approved art, when available, guides the target view. Use the chosen tool, including Blender. |
| [Code-driven 3D](references/code-driven-3d.md) | You want to shape a subject, light it, or compose an original scene through code. When the choice of tool is open, try a small Three.js study early, even for a single still. Browser delivery and its costs are covered here too. |
| [Code-driven 3D Interaction](references/code-driven-3d-interaction.md) | You need to discover what an action lets a viewer perceive or change. A placeholder or an existing model works; the same reasoning can serve a 2D page. |

For a model built in code to match approved art or a documented subject, combine **reconstruction and modeling**. For an original interactive mechanism, use **modeling and interaction**. If an existing scene already has its assets and needs a reveal that starts from an approved frame, use **reconstruction and interaction**. For a walkable landmark built in code, all three can help: recover the site layout from surveys, build the terrain, and test what the visitor discovers along the route. [SKILL.md](SKILL.md#choosing-a-3d-approach) gives a worked choice for each combination.

## Evaluating transfer

**Reconstruction across styles.** Cross-style transfer remains unproven. An informative trial uses an unfamiliar concept with different visual traits and supplies only the goal, viewing conditions, and necessary constraints, without route hints. Before implementation, the agent identifies the key visual trait and candidate explanations with different predictions. The evidence is a rendered study that captures the trait, a comparison exposing the method’s limits, and a supported decision to retain, revise, or replace the approach. Retaining the original approach is valid when the comparison supports it. Choosing the right problem without user correction matters as much as the final image; a trial in which the user supplies the key diagnosis or route is guided. One result establishes performance on that case, not general capability.

**Original modeling.** Give the maker a concrete second edit: widen an arch while preserving the adjoining bays and the intended view. Compare what changed, what broke, and how much rework was needed.

**Interaction.** Give a new viewer the piece without a walkthrough. Observe whether they discover the control, perceive its response, and can reproduce the consequence. A replay checks the rule; it cannot tell you what the viewer understood. The interaction guide has not been tested in a production trial.

These are proposed evaluations. To attribute an improvement to the skill, compare the same brief, tools, model, and budget with and without it; keep user assistance comparable and record it.

## Usage

Install this repository as the `expressive-visuals` skill directory in any client that supports `SKILL.md`. In clients that support invocation by name, use `$expressive-visuals`. Discovery and loading depend on the client.

Current version: 1.7.1.

License: [MIT](LICENSE).
