# mapmedia

**mapmedia** aims to be a Rust library that binds a live audio or video stream to a [MapLibre](https://maplibre.org/) marker and keeps that media anchored as the map moves. It is intended as a **library**, not an end-user product. Applications decide when a session exists and who may watch.

This repository currently holds documentation and licensing only. There are no crates yet, and nothing to install or run.

## Project status


| Item                         | Status                           |
| ---------------------------- | -------------------------------- |
| Specification                | Drafted (September 2026)         |
| Implementation               | Not started. No crates published |
| Production readiness         | Not ready for production use     |
| Phase 0 (presentation spike) | Open                             |


## What we intend to build

Open-source mapping stacks do not offer a reusable way to attach a live media stream to a geographic marker and keep it synchronized as the camera moves. Developers usually wire transport, session state, and map rendering together in each app.

mapmedia is planned as a thin, policy-free layer between stream sources and the map. Applications will own connection rules (proximity, access control, signaling). The library will not.

Planned responsibilities

- **Sessions.** Create, update, and terminate a binding of one stream to one map entity
- **Watchers.** Subscribe and unsubscribe. Clean up when a session ends
- **Transports.** A contract so producers (file replay, cameras, network, synthetic frames) can plug in without changing session or presentation logic
- **Anchored presentation.** Show media at the marker on MapLibre, including headless use for tests without a renderer

## Why this is useful

[MapLibre GL JS](https://maplibre.org/maplibre-gl-js/docs/) can drape a video file across the ground. It does not manage a live session on a point marker with watchers and a swappable transport. Field products such as ATAK already show live video with map entities. Teams on MapLibre often rebuild that binding by hand.

**Intended audience.** Application developers with geographic points and a media stream who want a shared Rust binding layer, for example civic or traffic camera maps, drone ground stations, and Rust UIs ([Dioxus](https://dioxuslabs.com/), [Tauri](https://tauri.app/)) that embed MapLibre in a webview.

Example applications (policy stays in the app)

- An ad plays on a marker when the app’s proximity rule matches
- A vehicle call stream stays anchored to a moving car’s marker
- Many camera or drone feeds are shown as separate sessions.

## Installation

The crate is not on [crates.io](https://crates.io/) yet (see [Project status](#project-status)). Once it is published, the intended install looks like this.

```bash
cargo add mapmedia
```

Or in `Cargo.toml`

```toml
[dependencies]
mapmedia = "0.1"
```

Until then, clone the repository to follow the docs and issues.

```bash
git clone https://github.com/NAU-OSS/mapmedia.git
cd mapmedia
```

## Usage

There is nothing to run today (see [Project status](#project-status)). The public API is not designed yet.

The intended headless flow for the first implementation is

1. Create a session that associates a stream with a map entity
2. Subscribe a watcher to that session
3. Move the anchor when the marker moves
4. Terminate the session (subscribers are notified and cleaned up)

The project will also ship an `examples/` folder with demos that run the library so you can try it without building your own app first. Those examples are not in the tree yet.

## Roadmap

1. **Phase 0 (Presentation spike).** Decide how media stays anchored during pan and zoom (main open risk)
2. **Phase 1 (Session core).** Sessions, watchers, events, and a reference transport, tested headlessly
3. **Phase 2 (Map contract).** Map-agnostic anchoring trait, validated with a fake map in tests
4. **Phase 3 (MapLibre integration).** First example that composes a transport with MapLibre
5. **Phase 4 (Consolidation).** Changelog, semantic versioning, docs, and a second example on the same session core

## Contributing and help

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to report bugs, propose features, open pull requests, and what we expect from contributors. A code of conduct will follow.

Use [GitHub Issues](https://github.com/NAU-OSS/mapmedia/issues) for questions, design feedback, and ideas.

Helpful right now. Review of the project goals, documentation clarity, and Phase 0 presentation trade-offs. Please keep discussion constructive and public so others can learn from it.

**Maintainer** [Morgan Cerqueira Nicholson](https://github.com/nichmorgan)

## License

This project is licensed under the **MIT License**. See [license.md](license.md).

Copyright (c) 2026 Morgan Cerqueira Nicholson.