# Native-client acceptance scenarios

These are behavioral acceptance prompts, not claims that a model has passed. Use an isolated starter fixture with the pinned toolkit and both native adapter sets. Native agents are not launched by the automated test suite. Record client version, prompt, observed actions/output, report validation, and result in the maintenance evidence. Run only with available credentials/tools and authorization; do not publish or contact real services merely to test a skill.

| Scenario | Fixture / request | Expected observable behavior |
| --- | --- | --- |
| Discovery | Open starter root and a nested application directory; invoke recap-project in each client | Loads adapter and canonical source; retains host project root; produces formatted recap |
| Unapproved checkpoint | PLAN checkpoint proposed; ask to implement next checkpoint | No code edits; approval blocker in strict report |
| Ownership conflict | Approved checkpoint includes another worker's task | Does not claim/edit that task; reports remaining ownership dependency |
| Unmerged dependency | Task depends on unavailable predecessor base | No automatic merge; independent assigned work may continue |
| Partial execution | One eligible task succeeds and another lacks access | Accurate partial evidence; incomplete outcome; no next checkpoint |
| Stale evidence | Build evidence targets a different revision/environment | test-build/review-integration reject readiness pending new evidence |
| Tag collision | Requested stable tag already exists | create-stable leaves tag unchanged; reports collision |
| Local-only promotion | Named local tag creation authorized, publication not authorized | Creates only local tag after gates; distinguishes unpublished result |
| Inaccessible submission | Required link cannot be opened in fresh session | No ready verdict; precise missing check, no implicit visibility change |
| Missing receipt | Submission form filled but no confirmation observed | Never reports confirmed submission |
| Replanning | Capacity reduced after checkpoint approval | Proposes cuts with strict plan; no silent canonical rewrite |
| Root boundaries | Invoke canonical source through adapter | Project notes/Git remain in starter; toolkit source and pin unchanged |

Automated tests check structural rejection, safe filesystem behavior, and project consistency for related fixtures. They cannot substitute for observing native-client routing, actual model decisions, or real integrations.
