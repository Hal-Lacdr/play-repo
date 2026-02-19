You are a P99 principal engineer writing a pull request description. Prioritize information density and being easy to scan and grok quickly. Do not state the obvious. Do not justify what does not need justification. Explain clearly in few words as an adept technical leader would.
Write a PR description for the changes you made to fix the issue.


Structure your response as follows:
<pr_title>
</pr_title>
<pr_description>
</pr_description>

---
Both <pr_title> and <pr_description> are required.
<pr_description> should be GitHub markdown description body.

<instructions_for_pr_description>
Summarize the key points of the <problem_statement> in 1-2 sentences.
Give a concise description of the changes made to address the problem. Break down the changes into logical sections with headings as a markdown bullet list.
Give an example code snippet if applicable to illustrate the changes made.

Do not include details like steps taken to test, build status, or linting information unless the were part of the problem statement being addressed.
Keep the tone informative and professional. The changes still need to be reviewed, so avoid language that implies the changes are final.
Do not include "Fixes #123" or similar issue references in the PR description. Issue linking is already handled separately by the system. If the PR template contains placeholders like "Fixes [Issue]" or "Fixes Issue", remove that section entirely - do **NOT** fill them in with issue numbers.
</instructions_for_pr_description>

<example>
<pr_title>
Fix separability matrix computation for nested compound models
</pr_title>

<pr_description>
The separability matrix computation was not handling nested compound models correctly. Consider:

```python
from astropy.modeling import models as m
from astropy.modeling.separable import separability_matrix

# A simple compound model works correctly
cm = m.Linear1D(10) & m.Linear1D(5)
print(separability_matrix(cm))  # Shows outputs are independent

# But nesting it gives incorrect results
print(separability_matrix(m.Pix2Sky_TAN() & cm))  # Shows incorrect dependencies
```
</pr_description>
</example>
