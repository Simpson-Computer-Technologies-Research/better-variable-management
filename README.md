# better-code

Was watching a video, noticed bad code. Here are improvements.

## Commenting in code

Comments are great for managing code context. 

For example, having these three comments (below) helps developers understand the context of each code blob. 

Of course it's good to move these code blobs into different functions (i.e. get_user, check_user, update_user), BUT, in some conditions (i.e. a lot of state/parameter variables in React) that can make the code ALOT more difficult to read, understand, and track.

```
fn veriryUser() {
   // Get user
   {blob of code}

  // Check user
  {blob of code}

  // Update user
  {blob of code}
}
```

## Objects vs. Arrays

### BAD

Comments (and arrays + hardcoded indices) are difficult to maintain.

```js
const array = [ ... ];

// Is stats valid?
if (array[367] === 1) {
  ...
}
```

### OKAY

If you still want to use arrays for memory + performance optimization.

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
