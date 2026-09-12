# Documentation project instructions

## About this project

- This is the documentation site for **EvilChat**, a decentralized end-to-end encrypted chat client on the EVIL (Event Verified Immutable Ledger) protocol
- Built on [Mintlify](https://mintlify.com): pages are MDX files with YAML frontmatter, configuration lives in `docs.json`
- The source of truth for every technical claim is the EvilChat repository (`~/Development/EvilChat`) — verify against code before documenting behavior
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP

## Terminology

- **EVIL protocol**, not "Evil" — the acronym is Event Verified Immutable Ledger
- **relay** (lowercase) — never "server" when meaning the dumb pipe; relays run no business logic
- **Vault** / **evilvault** — the personal archive daemon; `evilvault` (code style) when naming the binary
- **DID** — a user's identity; the root key's public half. Devices have **device subkeys**
- **MLS** — the only group encryption scheme (RFC 9420, via the `evil-mls` Rust core); DMs are two-member MLS groups
- **RoomKey** — retired legacy scheme; always describe as decrypt-only history, never as current behavior
- **sealed mode** / **sealed sender** — ephemeral outer signers + rotating epoch stream tags; on for all DMs, per-channel opt-in
- **epoch tag** / **stream tag** — the rotating wire address of a sealed conversation
- **park, don't drop** — the client discipline for not-yet-decryptable ciphertext
- **projection** — a local SQLite read model folded from events; projections must converge

## Style preferences

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references
- State privacy properties honestly: name what the relay can still see (timing, size, volume) whenever describing what it cannot
- Never present a roadmap item as shipped behavior; never present retired behavior (RoomKey, Double Ratchet plans) as current

## Content boundaries

- Document the protocol, the client, self-hosting, and contributor onboarding
- Do not document internal test infrastructure details (fabricators, harnesses) beyond what contributors need
- Do not paste private keys, real tokens, or real DIDs into examples — use obviously synthetic values
- The relay API has no OpenAPI spec; endpoint pages are written manually and must match `EvilChat.Relay/Program.cs`
