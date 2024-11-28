# sse-link

# Installation

```bash
# npm
npm install sse-link

# Yarn
yarn add sse-link

# pnpm
pnpm add sse-link
```

# Usage

```typescript
// Server
import { createSession } from "better-sse";

app.get("/sse", async (req, res) => {
	const session = await createSession(req, res);

	session.push("Hello world!");
});
```

```typescript
// Client
const sse = new EventSource("/sse");

sse.addEventListener("message", ({ data }) => {
	console.log(JSON.parse(data));
});
```

```typescript
import { createSession, createChannel } from "better-sse";

const channel = createChannel();

app.get("/sse", async (req, res) => {
	const session = await createSession(req, res);

	channel.register(session);

	channel.broadcast("A user has joined.", "join-notification");
});
```

```typescript
const session = await createSession(req, res);

const list = [1, 2, 3];

await session.iterate(list);
```

```typescript
const session = await createSession(req, res);

const stream = Readable.from([1, 2, 3]);

await session.stream(stream);
```

## Local Development

Install Node:

```bash
curl -L https://git.io/n-install | bash
n auto
```

Install pnpm:

```bash
npm i -g pnpm
```

Install dependencies:

```bash
pnpm i
```

Run tests:

```bash
pnpm t
```

    | stage | timebox | topic | presenter |
    |:-----:|:-------:|-------|-----------|
    | 3     | 15m     | [Intl.DurationFormat](https://github.com/tc39/proposal-intl-duration-format) for Stage 4. ([PR](https://github.com/tc39/ecma402/pull/943)) ([slides](https://docs.google.com/presentation/d/1bAuZ0ZSSYUdJxiDYXz2tUWHZwaOmYkNoLpQBBy_qz1w/edit?usp=sharing))| Ben Allen |
    | 2.7   | 15m     | [`Error.isError`](https://github.com/tc39/proposal-is-error/issues/7) to stage 3? | Jordan Harband |
    | 2.7   | 15m     | [iterator sequencing](https://github.com/tc39/proposal-iterator-sequencing) for Stage 3 ([tests](https://github.com/tc39/test262/pull/4326)) ([slides](https://docs.google.com/presentation/d/1EHMDcnV9zJ1E7BRhKmYtzHchZvOzjWynR3W-VdNxglw)) | Michael&nbsp;Ficarra |
    | 2.7   | 40m     | [`import defer`](https://github.com/tc39/proposal-defer-import-eval/) updates ([slides](https://docs.google.com/presentation/d/1yFbqn6px5rIwAVjBbXgrYgql1L90tKPTWZq2A5D6f5Q/)) | Nicolò Ribaudo |
    | 2.7   | 60m     | [ShadowRealm](https://github.com/tc39/proposal-shadowrealm) for Stage 3 ([slides](https://ptomato.name/talks/tc39-2024-12)) | Philip Chimento |
    | 2     | 5m      | [AsyncContext](https://github.com/tc39/proposal-async-context) request for Stage 2.7 reviewers | Andreu Botella |
    | 2     | 30m     | [Upsert (formerly Map.emplace)](https://github.com/tc39/proposal-upsert) Update and request for Stage 2 reviewers ([Slides](https://docs.google.com/presentation/d/15sWTvdWIo9Jt12LFRNBPJo1N_8xsMSCB3jy73HBFX-M/))| Daniel Minor |
    | 2     | 60m     | [ESM Phase Imports](https://github.com/tc39/proposal-esm-phase-imports) for Stage 2.7 | Guy Bedford |
    | 1     | 30m     | [Immutable ArrayBuffer](https://github.com/tc39/proposal-immutable-arraybuffer) to stage 2 ([slides.key](https://github.com/tc39/proposal-immutable-arraybuffer/raw/refs/heads/main/immu-arraybuffer-talks/immu-arrayBuffers-stage2.key), [slides.pdf](https://github.com/tc39/proposal-immutable-arraybuffer/blob/main/immu-arraybuffer-talks/immu-arrayBuffers-stage2.pdf), [docs slides](https://docs.google.com/presentation/d/1S1ixC7AVg3s_p4ZNhu3zBMcIcKbFkmp6umnsQUKOIqw/edit?usp=sharing)) | Mark Miller |
    | 1     | 30m     | [Measure](https://github.com/tc39-transfer/proposal-measure) Stage 1 update |  Ben Allen |
    | 1     | 60m     | [Error Stacks Structure](https://github.com/tc39/proposal-error-stacks) for Stage 2 | Jordan Harband |
    | 0     | 30m     | [Import Sync](https://github.com/guybedford/proposal-import-sync) discussion, request for Stage 1? | Guy Bedford |
    | 0     | 30m     | [More Currency Display Choices](https://github.com/eemeli/proposal-intl-currency-display-choices) for Stage 1/2 | Eemeli Aro |
    | 0     | 60m     | ***Stabilize*** to stage 1 ([youtube talk](https://www.youtube.com/watch?v=VHr4Jvvt0vc), [slides.key](https://github.com/Agoric/proposal-stabilize/raw/refs/heads/main/stabilize-talks/stabilize-stage1.key), [slides.pdf](https://github.com/Agoric/proposal-stabilize/blob/main/stabilize-talks/stabilize-stage1.pdf), [docs slides](https://docs.google.com/presentation/d/1474EreKln5bErl-pMUUq2PnX5LRo2Z93jxxGBNbZmco/edit?usp=sharing)) | Mark Miller |