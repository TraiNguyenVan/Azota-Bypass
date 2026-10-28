# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Version numbers follow the `@version` header in `azota.js`. No git tags are
published yet, so the links below point at commits and commit ranges instead.

## [Unreleased]

Nothing yet.

## [2.1] - 2026-10-28

### Added

- OpenAI-compatible provider option: the Gemini `generateContent` call is
  rewritten to `POST {Base URL}/chat/completions` and the reply is translated
  back into the Gemini response shape (`632a711`).
- Configurable Gemini model, with the `models/` prefix stripped and invalid
  names ignored (`632a711`).
- `⚙ AI Provider` settings dialog (SweetAlert2, with a `window.prompt`
  fallback) that validates Base URL and Model before saving (`632a711`).
- Provider settings persist through `GM_setValue` (`azota_provider`,
  `azota_gemini_model`, `azota_openai_base_url`, `azota_openai_model`,
  `azota_openai_api_key`) (`632a711`).
- Runtime sentinel value for the Gemini key slot, so the script starts in
  OpenAI-compatible mode without a Gemini key (`1bb2080`).

### Changed

- `// @connect *` added to the userscript header so arbitrary Base URLs can be
  reached.
- Switching into OpenAI-compatible mode for the first time offers a page reload
  instead of failing silently (`1bb2080`).
- README documents provider configuration and installation (`51ff4b1`).

### Fixed

- Streamed (SSE) replies from OpenAI-compatible endpoints are parsed
  incrementally: `data:` prefixes, `[DONE]`, empty lines and malformed chunks
  are skipped, and `delta.content` fragments are joined (`99f4bfa`).

## [2.0] - 2025-04-04

### Added

- Static landing page (`index.html`) with a feature tour, usage guide and
  version history (`47ad050`, `7f3f4dd`, `efe9b16`).
- Context memory for essay questions, keeping up to 5 question/answer pairs as
  context for the next answer.
- Gemini API integration via a user-supplied key.
- Draggable, collapsible control panel with status, log view and risk warning.

### Changed

- Answer recognition improved, with a focus on multiple-choice questions.
- UI updated with smoother interactions and transitions.

## [1.0] - 2025-04-03

### Added

- Initial userscript: automatic answering for multiple-choice and essay
  questions on Azota.vn (`37fc859`).
- Answer suggestion for the question currently on screen.
- Configurable API key stored with `GM_setValue`.
- Detailed activity log.
- Project README (`4b7c117`).

[Unreleased]: https://github.com/TraiNguyenVan/Azota-Bypass/commits/main
[2.1]: https://github.com/TraiNguyenVan/Azota-Bypass/compare/efe9b16...main
[2.0]: https://github.com/TraiNguyenVan/Azota-Bypass/compare/37fc859...efe9b16
[1.0]: https://github.com/TraiNguyenVan/Azota-Bypass/commit/37fc859
