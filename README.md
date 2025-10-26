# sharedb-node

Provides a [ShareDB](https://github.com/share/sharedb) database adapter that uses simple flat JSON files to store updates. It's intended for when you need something more than the in-memory adapter, but don't need a "real" database.

You can only use this if you don't need more than a single Node instance that reads/writes to it. There's no attempt to allow high-availability setups. That said, you can still do hundreds/thousands of reads and writes per second from a single process without too many issues.

## Use

Install from npm using `npm install sharedb-json`.

```js
import ShareDB from "sharedb";
import json1 from "ot-json1";

import { JSONDB } from "sharedb-json";

ShareDB.types.register(json1.type);
export const backend = new ShareDB({ presence: true, db: new JSONDB({}) });
export const connection = backend.connect();
```
