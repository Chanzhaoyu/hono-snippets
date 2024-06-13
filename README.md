# Hono Snippets

This extension is a set of Snippets for Hono. They are created so that scaffolding with Hono can be easy. You can try to remember most of these.

## Snippets Documentation

| Prefix | Description   |
| ------ | ------------- |
| `h`    | Hono Snippets |

## Snippets

<details>
<summary>h:base</summary>

```ts
import { serve } from "@hono/node-server";
import { Hono } from "hono";
const app = new Hono();

app.get("/", (c) => c.text("Hello Hono!"));

const port = 3000;
serve({
  fetch: app.fetch,
  port,
});
```

</details>

<details>
<summary>h:not-found</summary>

```ts
app.notFound((c) => {
  return c.text("Custom 404 Message", 404);
});
```

</details>

<details>
<summary>h:error-handling</summary>

```ts
app.onError((err, c) => {
  console.error(`${err}`);
  return c.text("Custom Error Message", 500);
});
```

</details>

<details>
<summary>h:api-get</summary>

```ts
app.get("/", (c) => {
  return c.text("GET /");
});
```

</details>

<details>
<summary>h:api-post</summary>

```ts
app.post("/", (c) => {
  return c.text("POST /");
});
```

</details>

<details>
<summary>h:api-put</summary>

```ts
app.put("/", (c) => {
  return c.text("PUT /");
});
```

</details>

<details>
<summary>h:api-delete</summary>

```ts
app.delete("/", (c) => {
  return c.text("DELETE /");
});
```

</details>

<details>
<summary>h:api-upload</summary>

```ts
app.post("/upload", async (c) => {
  const body = await c.req.parseBody();
  console.log(body["file"]);
});
```

</details>

<details>
<summary>h:param</summary>

```ts
const param = c.req.param();
```

</details>

<details>
<summary>h:query</summary>

```ts
const key = c.req.query("key");
```

</details>

<details>
<summary>h:body</summary>

```ts
const body = await c.req.parseBody();
```

</details>

<details>
<summary>h:json</summary>

```ts
const json = await c.req.json();
```

</details>

<details>
<summary>h:middleware</summary>

```ts
import type { Context, Next } from "hono";

export const middleware = async (c: Context, next: Next) => {
  await next();
};
```

</details>

<details>
<summary>h:serve-static</summary>

```ts
import { serveStatic } from "@hono/node-server/serve-static";

app.use("/*", serveStatic({ root: "./public" }));
```

</details>

<details>
<summary>h:cors</summary>

```ts
import { cors } from "hono/cors";

app.use(
  "*",
  cors({
    origin: "*",
    allowMethods: ["GET", "POST", "PUT", "DELETE", "OPTIONS"],
  })
);
```

</details>

<details>
<summary>h:logger</summary>

```ts
import { logger } from "hono/logger";

app.use(logger());
```

</details>

<details>
<summary>h:compress</summary>

```ts
import { compress } from "hono/compress";

app.use(compress());
```

</details>

<details>
<summary>h:get</summary>

```ts
const value = c.get("key");
```

</details>

<details>
<summary>h:set</summary>

```ts
c.set("key", "value");
```

</details>

<details>
<summary>h:context-interface</summary>

```ts
declare module "hono" {
  interface ContextVariableMap {}
}
```

</details>

## License

[MIT](license)
