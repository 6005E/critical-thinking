At its core, the skill runs a triage system that routes each prompt to targeted instruction clusters based on what could go wrong: flawed framing or hidden assumptions, argument structure problems, output calibration for recommendations and plans, knowledge gaps requiring source evaluation, and domain-specific reasoning patterns. A set of always-load files applies universal checks to every substantive response — examining load-bearing assumptions, goal-action conflicts, framing that has been accepted without examination, and confidence that has outrun evidence.

Conditional files cover flaw handling (false dichotomies, invalid premises, underspecified questions, loaded framing), argument structure (premise validity, logical gaps, steelmanning, causal direction), output quality (recommendation framing, plan evaluation, prediction calibration), knowledge gaps (source hierarchy, fitness for purpose, methodological quality, triangulation), and domain files for strategic, analytical, interpersonal, quantitative, and creative tasks — each with failure modes specific to that task type.

Always-load files cover pre-execution checks, ongoing monitoring throughout execution, a pre-finalization sweep for claim-level verification, and a post-execution reflection step.

The skill is designed to earn its overhead. Conditional files only load when their triage condition is met, keeping always-load cost stable regardless of how many files are added. Instructions are held to an impact-per-token standard: high-frequency, non-redundant, and broad enough to fire across multiple task types.

Download criticial-thinking.zip from Dropbox at https://tinyurl.com/yarzjde3
