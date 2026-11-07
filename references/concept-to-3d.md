# 3D Reconstruction from Concept Art

## The target and its viewing conditions

The currently approved concept, existing style definitions, and latest render establish the target and the remaining discrepancy. Later approved revisions can supersede parts of an image without replacing its other decisions. Style names alone are too broad: silhouette, mark direction, edge quality, value grouping, and material response explain what makes this particular image distinctive.

Viewing conditions determine what a convincing reconstruction must preserve. A fixed illustration, an orbitable asset, and a playable scene expose different failures. A single image constrains visible relationships but does not establish hidden surfaces or depth uniquely. A concept may also bend perspective, proportion, or construction to serve composition. Such deviations can be effective in a fixed view; moving cameras expose their spatial costs. The useful choice is which image relationships to preserve, which spatial inconsistencies to resolve, and where the intended viewing range permits approximation.

## Whole-image diagnosis and camera fit

Matched framing, aspect ratio, and display size make comparison meaningful. Small views reveal composition and value masses; target-size views reveal structural readability and surface marks. Across foreground, midground, and background, the diagnostic relationships include silhouettes, visible-face proportions, occlusion order, supports, and negative space. An object with the right name may still fail its role in the image.

A shared image coordinate system turns these relationships into comparable evidence. Grid overlays, landmark pairs, and contour overlays locate positions, extents, and gaps; coordinates expressed as fractions of image width and height remain comparable across resolutions when the crop is unchanged. Grid density is useful only insofar as it resolves the discrepancy being judged; extra lines can obscure edges or imply precision the concept does not support. The unmarked images remain necessary for judging visual character.

Patterns of landmark error help locate a cause, without proving it. Similar displacement across unrelated objects suggests a framing, camera, or overall placement issue; a discrepancy confined to one part suggests a local proportion, orientation, or structural issue. Reshaping each object to compensate for a shared error can damage an otherwise coherent scene. An ordinary image grid measures projected positions, not world dimensions or depth. Horizon, vanishing directions, visible-face proportions, and known dimensions provide additional constraints on camera height, orientation, field of view, and scene scale. Focal length changes framing, while camera position changes perspective. A useful camera fit explains several landmarks together; artistic perspective inconsistencies may prevent a single exact solution.

Differences occur at different scales: overall silhouette, middle-scale planes and light–dark groups, or fine surface marks. More texture cannot repair a missing mass or misplaced dark opening. Conversely, correct outlines with weak volume may implicate values, lighting, or atmosphere rather than geometry. Geometry and appearance remain competing explanations until a comparison distinguishes them.

## Editable structure and visual readability

Measured image relationships become useful modeling constraints when connected to the parameters that can explain them. A landmark pair may constrain a projected span, while an occlusion boundary constrains which part appears in front; neither uniquely determines depth. Keeping observed positions distinct from inferred dimensions allows camera and geometry hypotheses to remain revisable. Shared guides translate these constraints into related parts that retain connections, support, and alignment as they change. Dependencies still matter: increasing a beam's thickness can close a formerly valid clearance, and changing a curved path can make repeated parts intersect. Real construction references help explain unfamiliar joints without overriding intentional stylization in the concept.

Physical connection and visual readability are separate claims. Geometry inspection can establish contact; the target view establishes apparent scale, depth, and separation. A connected joint can disappear into shadow, while a projected overlap can conceal a disconnected support. For example, if a roof seems too heavy, a silhouette comparison can distinguish an oversized outline from a dark underside that merges with the supports; a neutral-material render then helps locate the contribution of surface color. Neither view alone establishes full visual fidelity.

## Competing mechanisms and regional treatment

A visible phenomenon does not specify its implementation. Geometry, surface color, lighting, and compositing can produce similar evidence in one frame. A watercolor bleed edge might be painted on a surface or generated at a light–shadow boundary. With camera and object fixed, moving the light separates these explanations: the painted edge stays put; the lighting-driven edge moves. The desired behavior under actual viewing conditions determines which route fits. When the concept cannot decide, the mechanism remains an assumption; equally suitable routes can be compared by cost and editability.

A coherent style need not apply the same treatment everywhere. Hard edges may explain construction, separated marks may articulate foliage, and broad value planes may carry rock volume. Masks can preserve these differences, but object and material labels are only proxies for visual function. Different regions of one object may need different edge behavior, mark density, or contrast to serve the same overall style.

## Comparisons that support causal judgment

A useful comparison addresses one causal question whose answer changes the next decision. Independent repairs can coexist in one iteration; changing several factors in the same comparison establishes only their combined effect. Naming the result that would disprove an explanation makes it possible to abandon a route instead of indefinitely attributing failure to unfinished tuning.

The least costly discriminating view depends on the uncertainty: fixed-camera material swaps test surface treatment; silhouettes and neutral renders help separate shape from appearance; fixed model and lighting expose differences in paint distribution; grazing views, light movement, or camera motion distinguish color from relief. Random arrangements are variables too. Stable samples in unchanged regions keep procedural texture or vegetation changes interpretable. If an edit has no visible effect, its contribution may be hidden by occlusion, fog, or compositing; isolation reveals where it disappears before further tuning.

Numerical comparisons support diagnosis but do not certify resemblance. Stronger gradients may indicate clearer form or more noise; matching value distributions says little about where light and dark occur. Corresponding regions need matching visual roles, not just matching pixel coordinates. Treatments also interact: local brightening and global grading can compound, while repeated softening can erase useful edges. Repeated compensating edits suggest an upstream cause or accumulated processing worth isolating.

## Integrated evidence and the next decision

A local improvement matters when it survives reintegration at the intended scale. Repeatable full views and diagnostic crops expose regressions against both the concept and the previous render. Camera or structural changes can invalidate earlier judgments about landmarks, occlusion, and connections. Finer detail with the same dominant discrepancy suggests a wrong diagnosis or an unsuitable method; a good main view that breaks during an intended lateral move suggests missing coverage, incorrect depth, or a representation tied too closely to one projection.

Evidence is specific to the deliverable. A local study supports a decision through a concept crop, a controlled comparison, and its observed limits. A complete material render demonstrates integrated geometry, materials, light, and atmosphere in an inspected final frame; an editable or playable scene additionally needs evidence from its actual project and intended camera conditions. Source files preserve editability, but object counts, texture files, and iteration totals do not establish visual quality.

Progress means that the original discrepancy has diminished without sacrificing established strengths. Remaining gaps clarify whether to retain, revise, or replace the approach. When concept pixels are sampled, projected, or extended, distinguishing that contribution from independently modeled or generated content makes the evidence interpretable: a close match in one view supports that view, not an untested claim of reconstruction quality elsewhere.
