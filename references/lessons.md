# Observed lessons and limitations

These observations come from a workflow with a user-accepted result. They are not guarantees of model performance.

| Attempt | Observation | Reusable lesson |
|---|---|---|
| Text-only Asuka embroidery generation | Thick yarn, generic chibi face, single-needle filling | Text alone did not reliably constrain identity, material, and complex motion together |
| Accurate fine-embroidery still followed by reference-image video generation | Still-image identity improved; animation retained wide stitches and large-area filling | A finished still can validate identity but cannot replace motion guidance |
| Source video plus finished still for character replacement | Multiple threads survived, but the portrait was complete at the opening and original bear-hat features remained | Check completion progress and residual source features, not just the last frame |
| Source video plus character artwork for replacement | Rejected with IPInfringementSuspect; an unchanged retry also failed | This route was not validated; do not infer a legal conclusion or keep retrying blindly |
| Same-character generative remaster of the source video | Blank opening, colored loops, and local accumulation survived; the user accepted the style | Strongest validated starting point, but still closely derived from the source |

The accepted version had minor differences: the embroidered character did not retain the reference card's raised-hand pose, a white thread tail remained at the end, and the overlay's depth of field differed from the fabric. Acceptance of the overall style does not mean future projects may skip these checks.

A successful API response, the presence of needles and thread, or a recognizable final portrait does not prove recreation success. The most distinguishing evidence is the relationship between spatial thread motion, tightening, and local assembly in the middle of the clip.
