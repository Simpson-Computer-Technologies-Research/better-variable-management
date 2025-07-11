# better-variable-management

Was watching a video, noticed bad code. Here are improvements.

### BAD

Comments (and arrays + hardcoded indices) are difficult to maintain.

```js
const array = [ ... ];

// Is stats valid?
if (array[367] == 1) {
  ...
}
```

### OKAY

If you still want to use arrays for memory optimization.

```js
const store = [ ... ] as const;
const STORE_INDEX_IS_STATS_VALID = 367;

const isStatsValid = store[STORE_INDEX_IS_STATS_VALID];
if (isStatsValid) {
  ...
}
```

### EVEN BETTER

Use a map/object for best DX.

```js
const store = { ... } as const;

if (store.isStatsValid) {
  ...
}
```
