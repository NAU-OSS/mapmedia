# Contributing to mapmedia

Thank you for considering a contribution to mapmedia. Contributions of every kind help the project move forward.

This repository is early. Today it holds documentation and licensing only. There are no crates yet. The most useful help right now is review of project goals, documentation clarity, and Phase 0 presentation trade-offs (see the [roadmap](README.md#roadmap) in the README). When implementation starts, code contributions will be welcome on the same terms below.

## Ways to help

- Improve or clarify documentation
- Review design notes and give constructive feedback on issues
- Discuss Phase 0 presentation risks (how media stays anchored during pan and zoom)
- Later: implement sessions, transports, tests, and MapLibre examples once crates exist

Documentation, design feedback, and careful review count as contributions.

## How to contribute

1. Check [open issues](https://github.com/NAU-OSS/mapmedia/issues) and the [README](README.md) so your work fits the current scope and roadmap.
2. For anything larger than a small documentation fix, open an issue first so we can agree on direction before you spend time on a pull request.
3. Fork the repository and create a branch from `main`.
4. Make your changes. Keep the pull request focused on one concern.
5. Open a pull request against `main`. Describe what changed and why. Link related issues.
6. For substantial work, open a **draft** pull request early so others can follow along and give feedback before the change is finished.

The maintainer will review pull requests. You should get an acknowledgment soon even if a full review takes longer. Feel free to ask questions on the pull request or a related issue.

## Code style

There is no crate to format today. When Rust code lands, please:

- Format with `rustfmt`
- Keep the change Clippy-clean for the code you touch
- Document public items with `rustdoc`
- Prefer clear names and comments that state intent and edge cases

Match the style of surrounding code when it exists. If you are unsure, ask on the issue or pull request.

## Testing

When code exists:

- Behavior changes should include tests
- Tests must use the `rstest` pattern (`#[rstest]`, fixtures, and case parameters as appropriate)
- Prefer the headless path described in the README (sessions, watchers, anchors) so tests do not require a MapLibre renderer
- Run `cargo test` before opening a pull request and mention the result in the description

Documentation-only changes do not need tests.

## Documentation standards

Treat the [README](README.md) as the project’s scope statement: mapmedia is a thin, policy-free layer between stream sources and the map. Applications own connection rules; the library does not.

- Update the README (and later crate docs / examples) in the same change when behavior or project status changes
- Write in plain language; assume readers may be new to MapLibre or Rust map UIs
- Prefer public issues and pull requests for design discussion so others can learn from the archive

## How to report bugs

Open a [GitHub issue](https://github.com/NAU-OSS/mapmedia/issues) and include:

- What you expected
- What happened instead
- Steps to reproduce
- Environment details that matter (OS, Rust version, browser or MapLibre version when relevant)
- Logs, screenshots, or a minimal example when you have them

**Security.** Do not file security reports as public issues. Contact the maintainer privately on GitHub: [nichmorgan](https://github.com/nichmorgan).

## How to propose new features

1. Open an issue before a large pull request.
2. Explain the problem you are solving, not only the solution.
3. Show how the idea fits the [roadmap](README.md#roadmap) and the library’s role (sessions, watchers, transports, anchored presentation).
4. Keep application policy (proximity rules, access control, signaling) out of the library proposal unless you are arguing for a deliberate scope change.

Discussion aims for consensus: listen, address concerns, and keep the thread aimed at a next step. When opinions stay split, the maintainer is the tiebreaker. Ideas outside the project’s scope will still get a thank-you and a pointer back to the README.

## Community guidelines and expectations

We want a constructive, welcoming place to work on this project.

- Be kind and respectful in issues, pull requests, and reviews
- Assume good intent; focus on the work, not the person
- Keep project discussion public (issues and pull requests) so others can follow along
- Guide conversations toward a clear next action; close threads that are no longer moving
- Do not tolerate harassment, personal attacks, or bad-faith disruption

These expectations sit alongside the formal [Code of Conduct](CODE_OF_CONDUCT.md), which is the binding standard for the project. If something goes wrong and you need a private channel, contact the maintainer: [Morgan Cerqueira Nicholson](https://github.com/nichmorgan).

## License

By contributing, you agree that your contributions are licensed under the project’s [MIT License](license.md).
