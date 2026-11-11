# 3D Reconstruction from Concept Art

## The target and its viewing conditions

The currently approved concept, existing style definitions, and latest render establish the target and the remaining discrepancy. Later approved revisions can supersede parts of an image without replacing its other decisions. Style names alone are too broad: silhouette, mark direction, edge quality, value grouping, and material response explain what makes this particular image distinctive.

Viewing conditions determine what a convincing reconstruction must preserve. A fixed illustration, an orbitable asset, and a playable scene expose different failures. A single image constrains visible relationships but does not establish hidden surfaces or depth uniquely. A concept may also bend perspective, proportion, or construction to serve composition. Such deviations can be effective in a fixed view; moving cameras expose their spatial costs. The useful choice is which image relationships to preserve, which spatial inconsistencies to resolve, and where the intended viewing range permits approximation.

## Whole-image diagnosis and camera fit

Matched framing, aspect ratio, and display size make comparison meaningful. Small views reveal composition and value masses; target-size views reveal structural readability and surface marks. Across foreground, midground, and background, silhouettes, visible-face proportions, occlusion, supports, and negative space reveal whether an object fulfills its role in the image. More texture cannot repair a missing mass or misplaced dark opening; conversely, correct outlines with weak volume may implicate values, lighting, or atmosphere rather than geometry. The scale of the discrepancy helps identify which explanation is worth testing.

A shared image coordinate system turns these relationships into comparable evidence. Grid overlays, landmark pairs, and contour overlays locate projected positions, extents, and gaps, rather than world dimensions or depth. Coordinates expressed as fractions of image width and height remain comparable across resolutions when the crop is unchanged. Useful grid density depends on the discrepancy being judged; extra lines can obscure edges or imply unsupported precision. Unmarked images preserve the visual character that measurement overlays can hide.

Patterns of landmark error help locate a cause, without proving it. Similar displacement across unrelated objects suggests a framing, camera, or overall placement issue; a discrepancy confined to one part suggests a local proportion, orientation, or structural issue. Reshaping each object to compensate for a shared error can damage an otherwise coherent scene. Horizon, vanishing directions, visible-face proportions, and known dimensions constrain camera height, orientation, field of view, and scene scale. Focal length changes framing, while camera position changes perspective. A useful camera fit explains several landmarks together; artistic perspective inconsistencies may prevent a single exact solution.

## Editable structure and visual readability

Measured relationships become editable constraints through parameters that can explain them. A landmark pair may constrain a projected span, while an occlusion boundary constrains which part appears in front. Separating observations from inferred dimensions keeps camera and geometry hypotheses revisable. Shared guides help related parts retain connections, support, and alignment as they change. Dependencies still matter: increasing a beam's thickness can close a formerly valid clearance, and changing a curved path can make repeated parts intersect. Real construction references help explain unfamiliar joints without overriding intentional stylization in the concept.

When code is a candidate for the reconstruction, [Code-driven 3D](code-driven-3d.md) explores how to turn observed contours, volumes, and spatial relationships into editable geometry, materials, and light.

Physical connection and visual readability are separate claims. Geometry inspection can establish contact; the target view establishes apparent scale, depth, and separation. A connected joint can disappear into shadow, while a projected overlap can conceal a disconnected support. For example, if a roof seems too heavy, a silhouette comparison can distinguish an oversized outline from a dark underside that merges with the supports; a neutral-material render then helps locate the contribution of surface color. Neither view alone establishes full visual fidelity.

## Competing mechanisms and regional treatment

A visible phenomenon does not specify its implementation. Geometry, surface color, lighting, and compositing can produce similar evidence in one frame. A watercolor bleed edge might be painted on a surface or generated at a light–shadow boundary. With camera and object fixed, moving the light separates these explanations: the painted edge stays put; the lighting-driven edge moves. The desired behavior under actual viewing conditions determines which route fits. When the concept cannot decide, the mechanism remains an assumption; equally suitable routes can be compared by cost and editability.

A coherent style need not apply the same treatment everywhere. Hard edges may explain construction, separated marks may articulate foliage, and broad value planes may carry rock volume. Masks can preserve these differences, but object and material labels are only proxies for visual function. Different regions of one object may need different edge behavior, mark density, or contrast to serve the same overall style.

## Comparisons that support causal judgment

A useful comparison addresses one causal question whose answer changes the next decision. Independent repairs can coexist in one iteration; changing several factors in the same comparison establishes only their combined effect. Naming the result that would disprove an explanation makes it possible to abandon a route instead of indefinitely attributing failure to unfinished tuning.

Controls depend on the uncertainty: comparing paint distribution benefits from a fixed model, camera, and light, while distinguishing color from relief may require a grazing view or light movement. Random arrangements are variables too. Stable samples in unchanged regions keep procedural texture or vegetation changes interpretable. If an edit has no visible effect, its contribution may be hidden by occlusion, fog, or compositing; isolation helps locate where the effect disappears.

Numerical comparisons support diagnosis but do not certify resemblance. Stronger gradients may indicate clearer form or more noise; matching value distributions says little about where light and dark occur. Corresponding regions need matching visual roles, not just matching pixel coordinates. Treatments also interact: local brightening and global grading can compound, while repeated softening can erase useful edges. Repeated compensating edits suggest an upstream cause or accumulated processing worth isolating.

## Integrated evidence and the next decision

A local improvement matters when it survives reintegration at the intended scale. Repeatable full views and diagnostic crops expose regressions against both the concept and the previous render. Camera or structural changes can invalidate earlier judgments about landmarks, occlusion, and connections. Finer detail with the same dominant discrepancy suggests a wrong diagnosis or an unsuitable method; a good main view that breaks during an intended lateral move suggests missing coverage, incorrect depth, or a representation tied too closely to one projection.

Evidence supports claims within the conditions examined. A local study tests a mechanism; a complete render reveals how geometry, materials, light, and atmosphere work together in that view. Neither a still frame nor an inventory of source files establishes editability or behavior in play; those depend on the working project. When concept pixels are sampled, projected, or extended, separating their contribution from independently modeled or generated content clarifies what the resemblance demonstrates and what remains untested.

Progress means that the original discrepancy has diminished without sacrificing established strengths. Remaining gaps clarify whether to retain, revise, or replace the approach.
