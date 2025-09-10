I need your help to identify the exact cause of this bug and implement an effective solution. To do this, carefully follow the workflow below, in this specific order:

Workflow:

Step 1: Clarification (if needed)
- If any part of this prompt is unclear or confusing, ask clarifying questions before proceeding.
- Do not ask questions unnecessarily… only ask if essential information is missing.

Step 2: Deeply Understand the Issue (Ultrathink)
- Carefully review and analyze the entire relevant codebase.
- Trace through the code step-by-step until you fully understand the bug and all relevant context.
- Continue analyzing until you feel completely confident in your understanding. If in doubt, research more deeply. It’s better to over-research than under-research.

Step 3: Special Case (if the cause is extremely obvious)
- If, after completing Step 2, you identify the root cause with extremely high confidence (95%+ certainty), explicitly state this clearly. Be realistic here. Do NOT be overconfident.
- In this scenario, instead of generating unrelated causes (see below for context), propose multiple practical variations of fixes for this single, clearly identified cause.
- Then proceed directly to Step 7 (Implementation), creating separate sub-agents and git worktrees for each variation, and implementing each fix independently.

Step 4: Identify Possible Causes (if cause is not extremely obvious)
- Thoughtfully generate a comprehensive list of at least 20 plausible causes for the bug.
- Be thorough. Explore various angles, even ones that initially seem less likely.

Step 5: Refine and Prioritize Causes
- Carefully review your list from Step 4.
- Remove theories that don’t hold up upon closer analysis.
- Combine related or overlapping theories into clearer, more likely scenarios.
- Add any additional theories you may have initially missed.
- Clearly rewrite and finalize this refined list.

Step 6: Rank by Likelihood
- Rank your refined theories clearly and explicitly, ordering them from most likely to least likely based on the probability of each theory being the true root cause.

Step 7: Propose Solutions
- For each of the top 10 most likely causes, clearly outline a practical and actionable solution to fix the issue.

Step 8: Implement Solutions Using Sub-agents
- For each of these top 10 cause/solution pairs (or multiple variations in the Special Case scenario), create a separate sub-agent, each with its own git worktree.
- Each sub-agent should clearly understand the specific cause it’s addressing and implement the corresponding solution directly in its own git worktree.

Step 9: Test the Solutions
- If testing each solution is possible given your available resources, perform tests (one worktree at a time) to determine if the bug is fixed.
- “Possible” means you have the appropriate tools and resources (e.g., a CURL command for API bugs; browser access for frontend bugs).
- If testing is not possible due to resource limitations, clearly summarize the implemented solutions and provide explicit, step-by-step instructions for me to test each solution manually.

⸻

Please carefully and thoughtfully complete every step of this workflow, maintaining clear communication throughout. Keep me updated at each major step, but only pause if you encounter something that requires my input.
