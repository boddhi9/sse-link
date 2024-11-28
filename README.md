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