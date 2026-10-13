# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
Releases up to 1.6.1 are described in the [GitHub releases](https://github.com/pepuscz/passwd/releases).

## [Unreleased]

### Security

- `passwd-agent exec`, `passwd exec` and the desktop extension mask a secret even when the child prints it across several output chunks, and no longer garble multi-byte UTF-8 split between chunks.
- `passwd-agent mcp-wrap` runs `mcp-remote` pinned to an exact version (0.14.3) without a shell. Header values reach it through environment variables that it expands itself, so they no longer appear in the process list. The URL must use HTTPS (or http on a loopback host).
- On macOS the keychain encryption key is passed to `security` over stdin instead of the command line.
- `PASSWD_ORIGIN` and other URLs accept plain http only for the exact hosts `localhost`, `127.0.0.1` and `[::1]`. Look-alike hosts such as `http://localhost.example.com` are rejected.
- The desktop extension also masks the JSON-escaped form of remote MCP header values in tool responses.

### Changed

- Every published package ships a README, the LICENSE and the TypeScript sources referenced by its source maps.
- `@passwd/passwd-lib` and `@passwd/passwd-mcp` declare `engines.node >=22.12`, like the CLIs.
- `@passwd/passwd-lib` exports the streaming masker (`createStreamMasker`, `maskSecrets`, `pipeMasked`, `MASK`).
- The README describes output masking as best-effort: it catches exact values, not transformed ones.
