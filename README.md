# Issue 20927

This is a demo of [an issue](https://github.com/nrwl/nx/issues/20927) with caching of root projects.

## Reproduction steps

1. Run `nx test`, which succeeds
2. Now update `src/app/app.spec.tsx` with a failur (e.g. `throw new Error()`)
3. Run `nx test` again

**Expected:**

Test fails due to (2)

**Actual:**

Test is cached and passes

Note: It's the same with `build` and `lint`.

## Additional details

This bug seems to only affects the root project (i.e. `projectRoot === '.'`). If you repeat the above steps with the `ui` project, it will fail on step (3) due to the cache being busted via code change.


