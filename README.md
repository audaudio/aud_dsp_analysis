# aud_dsp_analysis

English | [Deutsch](README.de.md)

[![CI](https://github.com/audaudio/aud_dsp_analysis/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/audaudio/aud_dsp_analysis/actions/workflows/quick_check.yaml)

Analysis nodes of the Audanika Audio Engine: amplitude, FFT and pitch taps, meters, scope and spectrum buffers.

Part of the Audanika Audio Engine; planned in [aud_audio_pm](https://github.com/audaudio/aud_audio_pm).

## Motivation

The repo exists before its code: the package graph of the Audanika Audio
Engine is complete from the start, so that every package has its place,
its pipeline and its version from day one. The package is step S10c of
[the plan of the engine](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-07-17-audanika-audio-engine.md) and will hold:

- amplitude, FFT and pitch taps as nodes of the engine
- meters, scope and spectrum buffers for the UI
- pitch tracking from the literature (YIN, McLeod)

Until then it carries the `package_ffi` template, which
[ticket 41](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-25-41-retire-the-template-api-of-the-stub-packages.md) retires.

## Installation

The package is not published to pub.dev; an app resolves it from its git
tags:

```yaml
dependencies:
  aud_dsp_analysis:
    git:
      url: git@github.com:audaudio/aud_dsp_analysis.git
      tag_pattern: "{{version}}"
    version: ^0.0.3
```

## Usage

Today the package exports only the `sum` and `sumAsync` of the
`package_ffi` template over its generated bindings, which the tests and
`example/` call:

```dart
import 'package:aud_dsp_analysis/aud_dsp_analysis.dart';

Future<void> main() async {
  print(sum(1, 2));
  print(await sumAsync(3, 4));
}
```

It prints:

```text
3
7
```

## Limitations

- No DSP code yet: nothing of the planned nodes is implemented
- The template API `sum` and `sumAsync` goes away with ticket 41 and is
  nothing to build on

## Documentation

- [The plan of the Audanika Audio Engine](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-07-17-audanika-audio-engine.md),
  step S10c
- [The architecture of the engine](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/architecture/architecture.md)
  with the package graph and the platforms
- [dsp-001](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/dsp-001.md):
  DSP packages take code only with clear provenance
- [Ticket 41](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-25-41-retire-the-template-api-of-the-stub-packages.md):
  retire the template API of the stub packages
- The guides in [`doc/guides`](doc/guides)

## Status

Planned: step S10c of the plan of the engine, no code yet. The platforms
of the package graph are iOS, Android, macOS, Windows, Linux and the web.
Before 1.0 — the API may change between minor versions.

## Contributing

Work is done ticket by ticket with the `gg` workflow; see the
[Develop Guide](doc/guides/develop-guide.md) and the
[Review Guide](doc/guides/for-ai/ai-review-guide.md).

## License

MIT — see [LICENSE](LICENSE).
