# AI-Assisted Development Workflow — Scam Lens

## Feature Compared

For this workflow experiment, I selected a small Scam Lens feature: a settings form for managing user information and scam-alert notification preferences. The form includes a display name, email address, notification preference, validation, and a success message after valid submission.

## Round One — Vague AI Prompt

The first implementation was created on the `round-one-vague` branch using a fresh AI session.

Prompt:

> Build a settings form for my Scam Lens React app.

The prompt intentionally provided almost no context. It did not specify the existing files, validation behavior, accessibility requirements, edge cases, design constraints, or testing requirements. The generated result was accepted as the first baseline and then reviewed manually.

## Round Two — Precise AI Prompt

The second implementation was created independently on the `round-two-precise` branch using a fresh AI session.

Prompt:

> Inspect the existing Scam Lens React project structure and identify the appropriate settings component and related styles before making changes. Build a settings form for Scam Lens with display name, email address, and scam-alert notification preference. Preserve the existing Scam Lens visual language and component structure. Use controlled React inputs. Display clear inline validation: display name is required, whitespace-only names are invalid, and email must use a valid format. Block submission when validation fails. Connect every input to an accessible label and associate validation messages with their fields. Preserve keyboard navigation and visible focus states. On valid submission, show a clear success message without reloading the page. Handle empty, whitespace-only, invalid-email, and valid inputs. Do not add unnecessary dependencies. First inspect the project and provide a short implementation plan. Then implement the feature, write tests for validation and successful/blocked submission, run the tests, fix failures, and report what was verified.

## Comparison

The vague prompt produced a workable starting point but left important decisions to the AI. The precise prompt produced a more predictable implementation because it defined the expected behavior before coding.

The biggest difference was validation. Round One did not explicitly define whitespace-only input or invalid-email behavior, so these cases required additional manual review. Round Two listed these edge cases directly and required them to be tested.

Accessibility was another important difference. Round One did not explicitly require accessible labels, error associations, keyboard navigation, or focus states. Round Two included each requirement, making accessibility part of the acceptance criteria instead of something discovered during review.

The review process was also different. Round One required more interpretation because I had to decide whether the AI's assumptions matched the intended Scam Lens behavior. Round Two provided specific requirements that could be checked one by one.

One AI mistake I caught was that a whitespace-only display name could be treated as valid unless the input was trimmed before validation. This showed why edge cases need to be explicitly specified and verified instead of assuming the generated code is correct.

The precise workflow takes slightly more time at the beginning because it requires planning and a detailed prompt. However, it reduces uncertainty and rework during review. The verification step is especially useful because the AI is asked to write and run tests instead of simply generating code.

Overall, the experiment showed that effective AI-assisted development is not just asking AI to build something. The developer needs to provide specifications, constraints, examples, edge cases, and verification requirements, then review the result against those requirements.

The main lesson from the Scam Lens experiment is that a precise AI workflow produces more predictable code and makes the developer's review process more focused and measurable.
