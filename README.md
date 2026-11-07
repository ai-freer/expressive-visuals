# Expressive Visuals

[English](README.md) | [中文](README_CN.md)

A heuristic creative skill for work whose value is primarily visual: web pages, interactive pieces, 3D scenes and models, images, video, and animation.

It prompts across content, form, and viewing. Start from the values, worldview, relationships, and *yijing* (意境, the lingering mood a work evokes) in the source material or concept; find an entry point and axes of change; then consider visual language, shape and space, light and atmosphere, camera, attention, the viewer's relationship to the work, and how experience unfolds over time. Finally, land the judgment in visible results. Reference study and viewing the actual work can also deepen understanding.

These open prompts widen creative choices. Use them as the task requires; there is no need to answer each one, cover them all, or submit a separate analysis document. They preserve the model's own understanding and creative judgment and do not prescribe a single style or model-specific method.

The entry point is [SKILL.md](SKILL.md). To faithfully rebuild approved concept art, use [3D Reconstruction from Concept Art](references/concept-to-3d.md) in the same skill. It covers camera and structure diagnosis, visual mechanisms, controlled comparisons, and integrated evidence under the intended viewing conditions.

## Evaluating transfer

Cross-style transfer remains unproven. An informative trial uses an unfamiliar concept with different visual traits and supplies only the goal, viewing conditions, and necessary constraints, without route hints. Before implementation, the agent identifies the key visual trait and candidate explanations with different predictions. The evidence is a rendered study that captures the trait, a comparison exposing the method's limits, and a supported decision to retain, revise, or replace the approach. Retaining the original approach is valid when the comparison supports it. Choosing the right problem without user correction matters as much as the final image; a trial in which the user supplies the key diagnosis or route is guided. One result establishes performance on that case, not general capability.

## Usage

Install this repository as the `expressive-visuals` skill directory in any client that supports `SKILL.md`. In clients that support invocation by name, use `$expressive-visuals`. Discovery and loading depend on the client.

Current version: 1.5.4.

License: [MIT](LICENSE).
