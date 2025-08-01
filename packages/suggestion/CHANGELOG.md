# Change Log

## 3.0.7

### Patch Changes

- @tiptap/core@3.0.7
- @tiptap/pm@3.0.7

## 3.0.6

### Patch Changes

- Updated dependencies [2e71d05]
  - @tiptap/core@3.0.6
  - @tiptap/pm@3.0.6

## 3.0.5

### Patch Changes

- @tiptap/core@3.0.5
- @tiptap/pm@3.0.5

## 3.0.4

### Patch Changes

- Updated dependencies [7ed03fa]
  - @tiptap/core@3.0.4
  - @tiptap/pm@3.0.4

## 3.0.3

### Patch Changes

- Updated dependencies [75cabde]
  - @tiptap/core@3.0.3
  - @tiptap/pm@3.0.3

## 3.0.2

### Patch Changes

- @tiptap/core@3.0.2
- @tiptap/pm@3.0.2

## 3.0.1

### Major Changes

- a92f4a6: We are now building packages with tsup which does not support UMD builds, please repackage if you require UMD builds
- 7eaa34d: Removed tippy.js and replaced it with [Floating UI](https://floating-ui.com/) - a newer, more lightweight and customizable floating element library.

  This change is breaking existing menu implementations and will require a manual migration.

  **Affected packages:**

  - `@tiptap/extension-floating-menu`
  - `@tiptap/extension-bubble-menu`
  - `@tiptap/extension-mention`
  - `@tiptap/suggestion`
  - `@tiptap/react`
  - `@tiptap/vue-2`
  - `@tiptap/vue-3`

  Make sure to remove `tippyOptions` from the `FloatingMenu` and `BubbleMenu` components, and replace them with the new `options` object. Check our documentation to see how to migrate your existing menu implementations.

  - [FloatingMenu](https://tiptap.dev/docs/editor/extensions/functionality/floatingmenu)
  - [BubbleMenu](https://tiptap.dev/docs/editor/extensions/functionality/bubble-menu)

  You'll also need to install `@floating-ui/dom` as a peer dependency to your project like this:

  ```bash
  npm install @floating-ui/dom@^1.6.0
  ```

  The new `options` object is compatible with all components that use these extensions.

### Minor Changes

- a80e62f: Added support for empty query messages via decorations

### Patch Changes

- 1b4c82b: We are now using pnpm package aliases for versions to enable better version pinning for the monorepository
- 89bd9c7: Enforce type imports so that the bundler ignores TypeScript type imports when generating the index.js file of the dist directory
- 8c69002: Synced beta with stable features
- Updated dependencies [1b4c82b]
- Updated dependencies [1e91f9b]
- Updated dependencies [a92f4a6]
- Updated dependencies [8de8e13]
- Updated dependencies [20f68f6]
- Updated dependencies [5e957e5]
- Updated dependencies [89bd9c7]
- Updated dependencies [d0fda30]
- Updated dependencies [0e3207f]
- Updated dependencies [37913d5]
- Updated dependencies [28c5418]
- Updated dependencies [32958d6]
- Updated dependencies [12bb31a]
- Updated dependencies [9f207a6]
- Updated dependencies [412e1bd]
- Updated dependencies [062afaf]
- Updated dependencies [ff8eed6]
- Updated dependencies [704f462]
- Updated dependencies [95b8c71]
- Updated dependencies [8c69002]
- Updated dependencies [664834f]
- Updated dependencies [ac897e7]
- Updated dependencies [087d114]
- Updated dependencies [32958d6]
- Updated dependencies [fc17b21]
- Updated dependencies [62b0877]
- Updated dependencies [e20006b]
- Updated dependencies [5ba480b]
- Updated dependencies [d6c7558]
- Updated dependencies [062afaf]
- Updated dependencies [9ceeab4]
- Updated dependencies [32958d6]
- Updated dependencies [bf835b0]
- Updated dependencies [4e2f6d8]
- Updated dependencies [32958d6]
  - @tiptap/core@3.0.1
  - @tiptap/pm@3.0.1

## 3.0.0-beta.30

### Patch Changes

- @tiptap/core@3.0.0-beta.30
- @tiptap/pm@3.0.0-beta.30

## 3.0.0-beta.29

### Minor Changes

- a80e62f: Added support for empty query messages via decorations

### Patch Changes

- @tiptap/core@3.0.0-beta.29
- @tiptap/pm@3.0.0-beta.29

## 3.0.0-beta.28

### Patch Changes

- @tiptap/core@3.0.0-beta.28
- @tiptap/pm@3.0.0-beta.28

## 3.0.0-beta.27

### Patch Changes

- Updated dependencies [412e1bd]
  - @tiptap/core@3.0.0-beta.27
  - @tiptap/pm@3.0.0-beta.27

## 3.0.0-beta.26

### Patch Changes

- Updated dependencies [5ba480b]
  - @tiptap/core@3.0.0-beta.26
  - @tiptap/pm@3.0.0-beta.26

## 3.0.0-beta.25

### Patch Changes

- Updated dependencies [4e2f6d8]
  - @tiptap/core@3.0.0-beta.25
  - @tiptap/pm@3.0.0-beta.25

## 3.0.0-beta.24

### Patch Changes

- @tiptap/core@3.0.0-beta.24
- @tiptap/pm@3.0.0-beta.24

## 3.0.0-beta.23

### Patch Changes

- @tiptap/core@3.0.0-beta.23
- @tiptap/pm@3.0.0-beta.23

## 3.0.0-beta.22

### Patch Changes

- @tiptap/core@3.0.0-beta.22
- @tiptap/pm@3.0.0-beta.22

## 3.0.0-beta.21

### Patch Changes

- Updated dependencies [813674c]
- Updated dependencies [fc17b21]
  - @tiptap/core@3.0.0-beta.21
  - @tiptap/pm@3.0.0-beta.21

## 3.0.0-beta.20

### Patch Changes

- @tiptap/core@3.0.0-beta.20
- @tiptap/pm@3.0.0-beta.20

## 3.0.0-beta.19

### Patch Changes

- Updated dependencies [9ceeab4]
  - @tiptap/core@3.0.0-beta.19
  - @tiptap/pm@3.0.0-beta.19

## 3.0.0-beta.18

### Patch Changes

- @tiptap/core@3.0.0-beta.18
- @tiptap/pm@3.0.0-beta.18

## 3.0.0-beta.17

### Patch Changes

- Updated dependencies [e20006b]
  - @tiptap/core@3.0.0-beta.17
  - @tiptap/pm@3.0.0-beta.17

## 3.0.0-beta.16

### Patch Changes

- Updated dependencies [ac897e7]
- Updated dependencies [bf835b0]
  - @tiptap/core@3.0.0-beta.16
  - @tiptap/pm@3.0.0-beta.16

## 3.0.0-beta.15

### Patch Changes

- Updated dependencies [087d114]
  - @tiptap/core@3.0.0-beta.15
  - @tiptap/pm@3.0.0-beta.15

## 3.0.0-beta.14

### Patch Changes

- Updated dependencies [95b8c71]
  - @tiptap/core@3.0.0-beta.14
  - @tiptap/pm@3.0.0-beta.14

## 3.0.0-beta.13

### Patch Changes

- @tiptap/core@3.0.0-beta.13
- @tiptap/pm@3.0.0-beta.13

## 3.0.0-beta.12

### Patch Changes

- @tiptap/core@3.0.0-beta.12
- @tiptap/pm@3.0.0-beta.12

## 3.0.0-beta.11

### Patch Changes

- @tiptap/core@3.0.0-beta.11
- @tiptap/pm@3.0.0-beta.11

## 3.0.0-beta.10

### Patch Changes

- @tiptap/core@3.0.0-beta.10
- @tiptap/pm@3.0.0-beta.10

## 3.0.0-beta.9

### Patch Changes

- @tiptap/core@3.0.0-beta.9
- @tiptap/pm@3.0.0-beta.9

## 3.0.0-beta.8

### Patch Changes

- @tiptap/core@3.0.0-beta.8
- @tiptap/pm@3.0.0-beta.8

## 3.0.0-beta.7

### Patch Changes

- Updated dependencies [d0fda30]
  - @tiptap/core@3.0.0-beta.7
  - @tiptap/pm@3.0.0-beta.7

## 3.0.0-beta.6

### Patch Changes

- @tiptap/core@3.0.0-beta.6
- @tiptap/pm@3.0.0-beta.6

## 3.0.0-beta.5

### Patch Changes

- 8c69002: Synced beta with stable features
- Updated dependencies [8c69002]
- Updated dependencies [62b0877]
  - @tiptap/core@3.0.0-beta.5
  - @tiptap/pm@3.0.0-beta.5

## 3.0.0-beta.4

### Patch Changes

- Updated dependencies [5e957e5]
- Updated dependencies [9f207a6]
  - @tiptap/core@3.0.0-beta.4
  - @tiptap/pm@3.0.0-beta.4

## 3.0.0-beta.3

### Patch Changes

- 1b4c82b: We are now using pnpm package aliases for versions to enable better version pinning for the monorepository
- Updated dependencies [1b4c82b]
  - @tiptap/core@3.0.0-beta.3
  - @tiptap/pm@3.0.0-beta.3

## 3.0.0-beta.2

## 3.0.0-beta.1

## 3.0.0-beta.0

## 3.0.0-next.8

## 3.0.0-next.7

### Patch Changes

- 89bd9c7: Enforce type imports so that the bundler ignores TypeScript type imports when generating the index.js file of the dist directory

## 3.0.0-next.6

### Major Changes

- a92f4a6: We are now building packages with tsup which does not support UMD builds, please repackage if you require UMD builds
- 7eaa34d: Removed tippy.js and replaced it with [Floating UI](https://floating-ui.com/) - a newer, more lightweight and customizable floating element library.

  This change is breaking existing menu implementations and will require a manual migration.

  **Affected packages:**

  - `@tiptap/extension-floating-menu`
  - `@tiptap/extension-bubble-menu`
  - `@tiptap/extension-mention`
  - `@tiptap/suggestion`
  - `@tiptap/react`
  - `@tiptap/vue-2`
  - `@tiptap/vue-3`

  Make sure to remove `tippyOptions` from the `FloatingMenu` and `BubbleMenu` components, and replace them with the new `options` object. Check our documentation to see how to migrate your existing menu implementations.

  - [FloatingMenu](https://tiptap.dev/docs/editor/extensions/functionality/floatingmenu)
  - [BubbleMenu](https://tiptap.dev/docs/editor/extensions/functionality/bubble-menu)

  You'll also need to install `@floating-ui/dom` as a peer dependency to your project like this:

  ```bash
  npm install @floating-ui/dom@^1.6.0
  ```

  The new `options` object is compatible with all components that use these extensions.

## 3.0.0-next.5

## 3.0.0-next.4

## 3.0.0-next.3

## 3.0.0-next.2

### Patch Changes

- ec8d654: Added a new option ´allowToIncludeChar` that allows the usage of the suggestion char inside the query

## 3.0.0-next.1

### Major Changes

- a92f4a6: We are now building packages with tsup which does not support UMD builds, please repackage if you require UMD builds

### Patch Changes

- Updated dependencies [a92f4a6]
- Updated dependencies [da76972]
  - @tiptap/core@3.0.0-next.1
  - @tiptap/pm@3.0.0-next.1

## 3.0.0-next.0

### Major Changes

- 7eaa34d: Removed tippy.js and replaced it with [Floating UI](https://floating-ui.com/) - a newer, more lightweight and customizable floating element library.

  This change is breaking existing menu implementations and will require a manual migration.

  **Affected packages:**

  - `@tiptap/extension-floating-menu`
  - `@tiptap/extension-bubble-menu`
  - `@tiptap/extension-mention`
  - `@tiptap/suggestion`
  - `@tiptap/react`
  - `@tiptap/vue-2`
  - `@tiptap/vue-3`

  Make sure to remove `tippyOptions` from the `FloatingMenu` and `BubbleMenu` components, and replace them with the new `options` object. Check our documentation to see how to migrate your existing menu implementations.

  - [FloatingMenu](https://tiptap.dev/docs/editor/extensions/functionality/floatingmenu)
  - [BubbleMenu](https://tiptap.dev/docs/editor/extensions/functionality/bubble-menu)

  You'll also need to install `@floating-ui/dom` as a peer dependency to your project like this:

  ```bash
  npm install @floating-ui/dom@^1.6.0
  ```

  The new `options` object is compatible with all components that use these extensions.

### Patch Changes

- Updated dependencies [0ec0af6]
  - @tiptap/core@3.0.0-next.0
  - @tiptap/pm@3.0.0-next.0

## 2.12.0

## 2.11.9

## 2.11.8

## 2.11.7

## 2.11.6

## 2.11.5

## 2.11.4

## 2.11.3

## 2.5.8

### Patch Changes

- Updated dependencies [a08bf85]
  - @tiptap/core@2.5.8
  - @tiptap/pm@2.5.8

## 2.5.7

### Patch Changes

- Updated dependencies [b012471]
- Updated dependencies [cc3497e]
  - @tiptap/core@2.5.7
  - @tiptap/pm@2.5.7

## 2.5.6

### Patch Changes

- Updated dependencies [b5c1b32]
- Updated dependencies [618bca9]
- Updated dependencies [35682d1]
- Updated dependencies [2104f0f]
  - @tiptap/pm@2.5.6
  - @tiptap/core@2.5.6

## 2.5.5

### Patch Changes

- Updated dependencies [4cca382]
- Updated dependencies [3b67e8a]
  - @tiptap/core@2.5.5
  - @tiptap/pm@2.5.5

## 2.5.4

### Patch Changes

- dd7f9ac: There was an issue with the cjs bundling of packages and default exports, now we resolve default exports in legacy compatible way
- Updated dependencies [dd7f9ac]
  - @tiptap/core@2.5.4
  - @tiptap/pm@2.5.4

## 2.5.3

### Patch Changes

- @tiptap/core@2.5.3
- @tiptap/pm@2.5.3

## 2.5.2

### Patch Changes

- Updated dependencies [07f4c03]
  - @tiptap/core@2.5.2
  - @tiptap/pm@2.5.2

## 2.5.1

### Patch Changes

- @tiptap/core@2.5.1
- @tiptap/pm@2.5.1

## 2.5.0

### Patch Changes

- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
  - @tiptap/core@2.5.0
  - @tiptap/pm@2.5.0

## 2.5.0-pre.16

### Patch Changes

- @tiptap/core@2.5.0-pre.16
- @tiptap/pm@2.5.0-pre.16

## 2.5.0-pre.15

### Patch Changes

- @tiptap/core@2.5.0-pre.15
- @tiptap/pm@2.5.0-pre.15

## 2.5.0-pre.14

### Patch Changes

- @tiptap/core@2.5.0-pre.14
- @tiptap/pm@2.5.0-pre.14

## 2.5.0-pre.13

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.13
  - @tiptap/pm@2.5.0-pre.13

## 2.5.0-pre.12

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.12
  - @tiptap/pm@2.5.0-pre.12

## 2.5.0-pre.11

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.11
  - @tiptap/pm@2.5.0-pre.11

## 2.5.0-pre.10

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.10
  - @tiptap/pm@2.5.0-pre.10

## 2.5.0-pre.9

### Patch Changes

- Updated dependencies [14a00f4]
  - @tiptap/core@2.5.0-pre.9
  - @tiptap/pm@2.5.0-pre.9

## 2.5.0-pre.8

### Patch Changes

- Updated dependencies [509676e]
  - @tiptap/core@2.5.0-pre.8
  - @tiptap/pm@2.5.0-pre.8

## 2.5.0-pre.7

### Patch Changes

- @tiptap/core@2.5.0-pre.7
- @tiptap/pm@2.5.0-pre.7

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.

# [2.4.0](https://github.com/ueberdosis/tiptap/compare/v2.3.2...v2.4.0) (2024-05-14)

### Features

- added jsdocs ([#4356](https://github.com/ueberdosis/tiptap/issues/4356)) ([b941eea](https://github.com/ueberdosis/tiptap/commit/b941eea6daba09d48a5d18ccc1b9a1d84b2249dd))

## [2.3.2](https://github.com/ueberdosis/tiptap/compare/v2.3.1...v2.3.2) (2024-05-08)

**Note:** Version bump only for package @tiptap/suggestion

## [2.3.1](https://github.com/ueberdosis/tiptap/compare/v2.3.0...v2.3.1) (2024-04-30)

**Note:** Version bump only for package @tiptap/suggestion

# [2.3.0](https://github.com/ueberdosis/tiptap/compare/v2.2.6...v2.3.0) (2024-04-09)

**Note:** Version bump only for package @tiptap/suggestion

## [2.2.6](https://github.com/ueberdosis/tiptap/compare/v2.2.5...v2.2.6) (2024-04-06)

**Note:** Version bump only for package @tiptap/suggestion

## [2.2.5](https://github.com/ueberdosis/tiptap/compare/v2.2.4...v2.2.5) (2024-04-05)

**Note:** Version bump only for package @tiptap/suggestion

## [2.2.4](https://github.com/ueberdosis/tiptap/compare/v2.2.3...v2.2.4) (2024-02-23)

**Note:** Version bump only for package @tiptap/suggestion

## [2.2.3](https://github.com/ueberdosis/tiptap/compare/v2.2.2...v2.2.3) (2024-02-15)

**Note:** Version bump only for package @tiptap/suggestion

## [2.2.2](https://github.com/ueberdosis/tiptap/compare/v2.2.1...v2.2.2) (2024-02-07)

**Note:** Version bump only for package @tiptap/suggestion

## [2.2.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0...v2.2.1) (2024-01-31)

**Note:** Version bump only for package @tiptap/suggestion

# [2.2.0](https://github.com/ueberdosis/tiptap/compare/v2.1.16...v2.2.0) (2024-01-29)

# [2.2.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.2.0-rc.8) (2024-01-08)

# [2.2.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.6...v2.2.0-rc.7) (2023-11-27)

# [2.2.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.5...v2.2.0-rc.6) (2023-11-23)

# [2.2.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.2.0-rc.4) (2023-10-10)

# [2.2.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.2...v2.2.0-rc.3) (2023-08-18)

# [2.2.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.0...v2.2.0-rc.1) (2023-08-18)

# [2.2.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.2.0-rc.0) (2023-08-18)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.16](https://github.com/ueberdosis/tiptap/compare/v2.1.15...v2.1.16) (2024-01-10)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.15](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.1.15) (2024-01-08)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.14](https://github.com/ueberdosis/tiptap/compare/v2.1.13...v2.1.14) (2024-01-08)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.13](https://github.com/ueberdosis/tiptap/compare/v2.1.12...v2.1.13) (2023-11-30)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.12](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.1.12) (2023-10-11)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.11](https://github.com/ueberdosis/tiptap/compare/v2.1.10...v2.1.11) (2023-09-20)

### Reverts

- Revert "v2.2.11" ([6aa755a](https://github.com/ueberdosis/tiptap/commit/6aa755a04b9955fc175c7ab33dee527d0d5deef0))

## [2.1.10](https://github.com/ueberdosis/tiptap/compare/v2.1.9...v2.1.10) (2023-09-15)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.9](https://github.com/ueberdosis/tiptap/compare/v2.1.8...v2.1.9) (2023-09-14)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.8](https://github.com/ueberdosis/tiptap/compare/v2.1.7...v2.1.8) (2023-09-04)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.7](https://github.com/ueberdosis/tiptap/compare/v2.1.6...v2.1.7) (2023-09-04)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.6](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.1.6) (2023-08-18)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.5](https://github.com/ueberdosis/tiptap/compare/v2.1.4...v2.1.5) (2023-08-18)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.4](https://github.com/ueberdosis/tiptap/compare/v2.1.3...v2.1.4) (2023-08-18)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.3](https://github.com/ueberdosis/tiptap/compare/v2.1.2...v2.1.3) (2023-08-18)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.2](https://github.com/ueberdosis/tiptap/compare/v2.1.1...v2.1.2) (2023-08-17)

**Note:** Version bump only for package @tiptap/suggestion

## [2.1.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0...v2.1.1) (2023-08-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.14...v2.1.0) (2023-08-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.14](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.13...v2.1.0-rc.14) (2023-08-11)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.13](https://github.com/ueberdosis/tiptap/compare/v2.0.4...v2.1.0-rc.13) (2023-08-11)

# [2.1.0-rc.12](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.11...v2.1.0-rc.12) (2023-07-14)

# [2.1.0-rc.11](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.10...v2.1.0-rc.11) (2023-07-07)

# [2.1.0-rc.10](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.9...v2.1.0-rc.10) (2023-07-07)

# [2.1.0-rc.9](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.8...v2.1.0-rc.9) (2023-06-15)

# [2.1.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.7...v2.1.0-rc.8) (2023-05-25)

# [2.1.0-rc.5](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.4...v2.1.0-rc.5) (2023-05-25)

# [2.1.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.3...v2.1.0-rc.4) (2023-04-27)

# [2.1.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.2...v2.1.0-rc.3) (2023-04-26)

# [2.1.0-rc.2](https://github.com/ueberdosis/tiptap/compare/v2.0.3...v2.1.0-rc.2) (2023-04-26)

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0c1bba3](https://github.com/ueberdosis/tiptap/commit/0c1bba3137b535776bcef95ff3c55e13f5a2db46))

# [2.1.0-rc.12](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.11...v2.1.0-rc.12) (2023-07-14)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.11](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.10...v2.1.0-rc.11) (2023-07-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.10](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.9...v2.1.0-rc.10) (2023-07-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.9](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.8...v2.1.0-rc.9) (2023-06-15)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.7...v2.1.0-rc.8) (2023-05-25)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.6...v2.1.0-rc.7) (2023-05-25)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.5...v2.1.0-rc.6) (2023-05-25)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.5](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.4...v2.1.0-rc.5) (2023-05-25)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.3...v2.1.0-rc.4) (2023-04-27)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.2...v2.1.0-rc.3) (2023-04-26)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.2](https://github.com/ueberdosis/tiptap/compare/v2.0.3...v2.1.0-rc.2) (2023-04-26)

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0c1bba3](https://github.com/ueberdosis/tiptap/commit/0c1bba3137b535776bcef95ff3c55e13f5a2db46))

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

**Note:** Version bump only for package @tiptap/suggestion

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

**Note:** Version bump only for package @tiptap/suggestion

## [2.0.3](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.0.3) (2023-04-13)

**Note:** Version bump only for package @tiptap/suggestion

## [2.0.2](https://github.com/ueberdosis/tiptap/compare/v2.0.1...v2.0.2) (2023-04-03)

**Note:** Version bump only for package @tiptap/suggestion

## [2.0.1](https://github.com/ueberdosis/tiptap/compare/v2.0.0...v2.0.1) (2023-03-30)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0534f76](https://github.com/ueberdosis/tiptap/commit/0534f76401bf5399c01ca7f39d87f7221d91b4f7))

# [2.0.0-beta.220](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.219...v2.0.0-beta.220) (2023-02-28)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.219](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.218...v2.0.0-beta.219) (2023-02-27)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.218](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.217...v2.0.0-beta.218) (2023-02-18)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.217](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.216...v2.0.0-beta.217) (2023-02-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.216](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.215...v2.0.0-beta.216) (2023-02-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.215](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.214...v2.0.0-beta.215) (2023-02-08)

### Bug Fixes

- fix builds including prosemirror ([a380ec4](https://github.com/ueberdosis/tiptap/commit/a380ec41d198ebacc80cea9e79b0a8aa3092618a))

# [2.0.0-beta.214](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.213...v2.0.0-beta.214) (2023-02-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.213](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.212...v2.0.0-beta.213) (2023-02-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.212](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.211...v2.0.0-beta.212) (2023-02-03)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.211](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.210...v2.0.0-beta.211) (2023-02-02)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.210](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.209...v2.0.0-beta.210) (2023-02-02)

### Features

- **pm:** new prosemirror package for dependency resolving ([f387ad3](https://github.com/ueberdosis/tiptap/commit/f387ad3dd4c2b30eaea33fb0ba0b42e0cd39263b))

# [2.0.0-beta.209](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.208...v2.0.0-beta.209) (2022-12-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.208](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.207...v2.0.0-beta.208) (2022-12-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.207](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.206...v2.0.0-beta.207) (2022-12-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.206](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.205...v2.0.0-beta.206) (2022-12-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.205](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.204...v2.0.0-beta.205) (2022-12-05)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.204](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.203...v2.0.0-beta.204) (2022-11-25)

### Bug Fixes

- **core:** rename esm modules to esm.js ([c1a0c3a](https://github.com/ueberdosis/tiptap/commit/c1a0c3ae43baac9dd5ed90903d3a0d4eaeea7702))

# [2.0.0-beta.203](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.202...v2.0.0-beta.203) (2022-11-24)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.202](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.201...v2.0.0-beta.202) (2022-11-04)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.201](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.200...v2.0.0-beta.201) (2022-11-04)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.200](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.199...v2.0.0-beta.200) (2022-11-04)

### Bug Fixes

- **suggestion:** revert [#3239](https://github.com/ueberdosis/tiptap/issues/3239) ([b38c9eb](https://github.com/ueberdosis/tiptap/commit/b38c9eb13988bcb0696ed083dd2090a7edcfe09a))

# [2.0.0-beta.199](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.198...v2.0.0-beta.199) (2022-09-30)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.198](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.197...v2.0.0-beta.198) (2022-09-29)

### Bug Fixes

- **suggestion:** set default allowedPrefixes null ([#3239](https://github.com/ueberdosis/tiptap/issues/3239)) ([04b9da4](https://github.com/ueberdosis/tiptap/commit/04b9da4760f467c446cbcf2fd08030e089d9be5f))

# [2.0.0-beta.197](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.196...v2.0.0-beta.197) (2022-09-26)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.196](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.195...v2.0.0-beta.196) (2022-09-20)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.195](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.194...v2.0.0-beta.195) (2022-09-14)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.194](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.193...v2.0.0-beta.194) (2022-09-11)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.98](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.97...@tiptap/suggestion@2.0.0-beta.98) (2022-09-03)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.97](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.96...@tiptap/suggestion@2.0.0-beta.97) (2022-06-27)

### Features

- Allow multiple prefix characters to trigger a suggestion ([#2896](https://github.com/ueberdosis/tiptap/issues/2896)) ([482cb96](https://github.com/ueberdosis/tiptap/commit/482cb960d6a17acc575bb9c535e1e87f07f06686))

# [2.0.0-beta.96](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.95...@tiptap/suggestion@2.0.0-beta.96) (2022-06-20)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.95](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.93...@tiptap/suggestion@2.0.0-beta.95) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.93](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.93...@tiptap/suggestion@2.0.0-beta.93) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.92](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.91...@tiptap/suggestion@2.0.0-beta.92) (2022-05-18)

### Bug Fixes

- fix suggestion package.json ([dd3e27b](https://github.com/ueberdosis/tiptap/commit/dd3e27b0e49cb7b7a63c0068437060472345c51b))

### Features

- Add `onBeforeStart` and `onBeforeUpdate` handlers to the render function ([70cb809](https://github.com/ueberdosis/tiptap/commit/70cb809702cbbb59abc6d12d85fd4d1291f88f5a))
- Add a generic type for suggestion items ([7cae967](https://github.com/ueberdosis/tiptap/commit/7cae9673f0086973b4d31e1343375ed5ad04ee0a))

# [2.0.0-beta.91](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.90...@tiptap/suggestion@2.0.0-beta.91) (2022-04-27)

### Bug Fixes

- prevent suggestions from being active when editor is readonly ([45990cd](https://github.com/ueberdosis/tiptap/commit/45990cdc0f8c9b7d31fe31cabe4b29088851d9f6))

# [2.0.0-beta.90](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.89...@tiptap/suggestion@2.0.0-beta.90) (2022-01-25)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.89](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.88...@tiptap/suggestion@2.0.0-beta.89) (2022-01-21)

### Bug Fixes

- fixes an error when using the mention extension and pasting text ending with "@", fix [#2413](https://github.com/ueberdosis/tiptap/issues/2413) ([55fa220](https://github.com/ueberdosis/tiptap/commit/55fa2208996f648a2ca06b0a363a249ff5e39169))

# [2.0.0-beta.88](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.87...@tiptap/suggestion@2.0.0-beta.88) (2022-01-20)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.87](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.86...@tiptap/suggestion@2.0.0-beta.87) (2022-01-13)

### Bug Fixes

- support all characters for suggestion char, fix [#2385](https://github.com/ueberdosis/tiptap/issues/2385) ([42d3ee8](https://github.com/ueberdosis/tiptap/commit/42d3ee8fc9882a9fb9f87e696cebd0e6146d2e62))

# [2.0.0-beta.86](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.85...@tiptap/suggestion@2.0.0-beta.86) (2022-01-04)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.85](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.84...@tiptap/suggestion@2.0.0-beta.85) (2021-12-04)

### Bug Fixes

- call onExit hook when editor is destroyed, fix [#1645](https://github.com/ueberdosis/tiptap/issues/1645) ([5d2ef71](https://github.com/ueberdosis/tiptap/commit/5d2ef71d33bea9ba6bf1aeb3cceee08af27f1e75))

# [2.0.0-beta.84](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.83...@tiptap/suggestion@2.0.0-beta.84) (2021-12-02)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.83](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.82...@tiptap/suggestion@2.0.0-beta.83) (2021-11-17)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.82](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.81...@tiptap/suggestion@2.0.0-beta.82) (2021-11-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.81](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.80...@tiptap/suggestion@2.0.0-beta.81) (2021-11-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.80](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.79...@tiptap/suggestion@2.0.0-beta.80) (2021-11-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.79](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.78...@tiptap/suggestion@2.0.0-beta.79) (2021-11-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.78](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.77...@tiptap/suggestion@2.0.0-beta.78) (2021-11-05)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.77](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.76...@tiptap/suggestion@2.0.0-beta.77) (2021-10-31)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.76](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.75...@tiptap/suggestion@2.0.0-beta.76) (2021-10-26)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.75](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.74...@tiptap/suggestion@2.0.0-beta.75) (2021-10-25)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.74](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.73...@tiptap/suggestion@2.0.0-beta.74) (2021-10-14)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.73](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.72...@tiptap/suggestion@2.0.0-beta.73) (2021-10-14)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.72](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.71...@tiptap/suggestion@2.0.0-beta.72) (2021-10-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.71](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.70...@tiptap/suggestion@2.0.0-beta.71) (2021-09-20)

### Bug Fixes

- Add type for async items on suggestions (fix TS strict types complaining) ([#1912](https://github.com/ueberdosis/tiptap/issues/1912)) ([4a6c3cb](https://github.com/ueberdosis/tiptap/commit/4a6c3cbaac9690f1261b8d435195878b6f60ad64))

# [2.0.0-beta.70](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.69...@tiptap/suggestion@2.0.0-beta.70) (2021-09-15)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.69](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.68...@tiptap/suggestion@2.0.0-beta.69) (2021-09-06)

### Features

- allow triggering suggestions without prefix space ([#1826](https://github.com/ueberdosis/tiptap/issues/1826), fix [#1384](https://github.com/ueberdosis/tiptap/issues/1384)) ([4dd0d6d](https://github.com/ueberdosis/tiptap/commit/4dd0d6d4dce20c78974bf53619a827f8ba1718e3))

# [2.0.0-beta.68](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.67...@tiptap/suggestion@2.0.0-beta.68) (2021-08-23)

### Bug Fixes

- get correct clientRect when using async suggesteion items, fix [#1782](https://github.com/ueberdosis/tiptap/issues/1782) ([839acc1](https://github.com/ueberdosis/tiptap/commit/839acc1d9f713b89f366cd7da63330fd0243c31b))

# [2.0.0-beta.67](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.66...@tiptap/suggestion@2.0.0-beta.67) (2021-08-23)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.66](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.65...@tiptap/suggestion@2.0.0-beta.66) (2021-08-20)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.65](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.64...@tiptap/suggestion@2.0.0-beta.65) (2021-08-13)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.64](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.63...@tiptap/suggestion@2.0.0-beta.64) (2021-08-13)

### Bug Fixes

- improve suggestion handling for chinese input, fix [#1449](https://github.com/ueberdosis/tiptap/issues/1449) ([9789372](https://github.com/ueberdosis/tiptap/commit/9789372cea901b21059d53c30ff301efb35fb720))

# [2.0.0-beta.63](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.62...@tiptap/suggestion@2.0.0-beta.63) (2021-08-13)

### Bug Fixes

- add pluginKey option to suggestion plugin, fix [#1282](https://github.com/ueberdosis/tiptap/issues/1282) ([7cf3350](https://github.com/ueberdosis/tiptap/commit/7cf3350a832181f8cc1fa7ea1afec8f8d083e507))

# [2.0.0-beta.62](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.61...@tiptap/suggestion@2.0.0-beta.62) (2021-08-09)

### Bug Fixes

- use correct state when doc changed externally ([#1646](https://github.com/ueberdosis/tiptap/issues/1646)) ([60606f9](https://github.com/ueberdosis/tiptap/commit/60606f99a1df3c694cc2faa0522c772ef419e9fe))

# [2.0.0-beta.61](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.60...@tiptap/suggestion@2.0.0-beta.61) (2021-07-26)

### Bug Fixes

- Fix multi character suggest ([#1620](https://github.com/ueberdosis/tiptap/issues/1620)) ([83a53c1](https://github.com/ueberdosis/tiptap/commit/83a53c16db4e8bbe06a37a0fe15e0a9e79bdb2ed))

# [2.0.0-beta.60](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.59...@tiptap/suggestion@2.0.0-beta.60) (2021-07-26)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.59](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.58...@tiptap/suggestion@2.0.0-beta.59) (2021-06-23)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.58](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.57...@tiptap/suggestion@2.0.0-beta.58) (2021-06-17)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.57](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.56...@tiptap/suggestion@2.0.0-beta.57) (2021-05-27)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.56](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.55...@tiptap/suggestion@2.0.0-beta.56) (2021-05-18)

### Bug Fixes

- add support for using suggestions at top level, fix [#1340](https://github.com/ueberdosis/tiptap/issues/1340) ([0d9e488](https://github.com/ueberdosis/tiptap/commit/0d9e48883641d1c4aeeb9c9aa941e2e6419b2e7a))

# [2.0.0-beta.55](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.54...@tiptap/suggestion@2.0.0-beta.55) (2021-05-17)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.54](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.53...@tiptap/suggestion@2.0.0-beta.54) (2021-05-13)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.53](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.52...@tiptap/suggestion@2.0.0-beta.53) (2021-05-07)

### Bug Fixes

- move @tiptap/core to peerDependency ([a03a01a](https://github.com/ueberdosis/tiptap/commit/a03a01ab042f7c655139a08ed547a58d8b1d386f))

# [2.0.0-beta.52](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.51...@tiptap/suggestion@2.0.0-beta.52) (2021-05-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.51](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.50...@tiptap/suggestion@2.0.0-beta.51) (2021-05-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.50](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.49...@tiptap/suggestion@2.0.0-beta.50) (2021-05-07)

### Bug Fixes

- revert adding exports ([bc320d0](https://github.com/ueberdosis/tiptap/commit/bc320d0b4b80b0e37a7e47a56e0f6daec6e65d98))

# [2.0.0-beta.49](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.48...@tiptap/suggestion@2.0.0-beta.49) (2021-05-06)

### Bug Fixes

- revert adding type: module ([f8d6475](https://github.com/ueberdosis/tiptap/commit/f8d6475e2151faea6f96baecdd6bd75880d50d2c))

# [2.0.0-beta.48](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.47...@tiptap/suggestion@2.0.0-beta.48) (2021-05-06)

### Bug Fixes

- add exports to package.json ([1277fa4](https://github.com/ueberdosis/tiptap/commit/1277fa47151e9c039508cdb219bdd0ffe647f4ee))

# [2.0.0-beta.47](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.46...@tiptap/suggestion@2.0.0-beta.47) (2021-05-06)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.46](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.45...@tiptap/suggestion@2.0.0-beta.46) (2021-05-06)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.45](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.44...@tiptap/suggestion@2.0.0-beta.45) (2021-05-05)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.44](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.43...@tiptap/suggestion@2.0.0-beta.44) (2021-05-05)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.43](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.42...@tiptap/suggestion@2.0.0-beta.43) (2021-05-04)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.42](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.41...@tiptap/suggestion@2.0.0-beta.42) (2021-04-27)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.41](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.40...@tiptap/suggestion@2.0.0-beta.41) (2021-04-27)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.40](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.39...@tiptap/suggestion@2.0.0-beta.40) (2021-04-27)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.39](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.38...@tiptap/suggestion@2.0.0-beta.39) (2021-04-23)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.38](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.37...@tiptap/suggestion@2.0.0-beta.38) (2021-04-23)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.37](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.36...@tiptap/suggestion@2.0.0-beta.37) (2021-04-22)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.36](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.35...@tiptap/suggestion@2.0.0-beta.36) (2021-04-21)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.35](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.34...@tiptap/suggestion@2.0.0-beta.35) (2021-04-20)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.34](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.33...@tiptap/suggestion@2.0.0-beta.34) (2021-04-20)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.33](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.32...@tiptap/suggestion@2.0.0-beta.33) (2021-04-16)

### Bug Fixes

- fix type for clientRect ([07c6d51](https://github.com/ueberdosis/tiptap/commit/07c6d513388c4538140e0ff37dc9035c9dc6fea3))

# [2.0.0-beta.32](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.31...@tiptap/suggestion@2.0.0-beta.32) (2021-04-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.31](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.30...@tiptap/suggestion@2.0.0-beta.31) (2021-04-15)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.30](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.29...@tiptap/suggestion@2.0.0-beta.30) (2021-04-15)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.29](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.28...@tiptap/suggestion@2.0.0-beta.29) (2021-04-12)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.28](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.27...@tiptap/suggestion@2.0.0-beta.28) (2021-04-12)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.27](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.26...@tiptap/suggestion@2.0.0-beta.27) (2021-04-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.26](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.25...@tiptap/suggestion@2.0.0-beta.26) (2021-04-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.25](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.24...@tiptap/suggestion@2.0.0-beta.25) (2021-04-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.24](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.23...@tiptap/suggestion@2.0.0-beta.24) (2021-04-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.23](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.22...@tiptap/suggestion@2.0.0-beta.23) (2021-04-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.22](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.21...@tiptap/suggestion@2.0.0-beta.22) (2021-04-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.21](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.20...@tiptap/suggestion@2.0.0-beta.21) (2021-04-08)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.20](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.19...@tiptap/suggestion@2.0.0-beta.20) (2021-04-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.19](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.18...@tiptap/suggestion@2.0.0-beta.19) (2021-04-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.18](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.17...@tiptap/suggestion@2.0.0-beta.18) (2021-04-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.17](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.16...@tiptap/suggestion@2.0.0-beta.17) (2021-04-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.16](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.15...@tiptap/suggestion@2.0.0-beta.16) (2021-04-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.15](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.14...@tiptap/suggestion@2.0.0-beta.15) (2021-04-06)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.14](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.13...@tiptap/suggestion@2.0.0-beta.14) (2021-04-04)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.13](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.12...@tiptap/suggestion@2.0.0-beta.13) (2021-04-02)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.12](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.11...@tiptap/suggestion@2.0.0-beta.12) (2021-04-01)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.11](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.10...@tiptap/suggestion@2.0.0-beta.11) (2021-04-01)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.10](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.9...@tiptap/suggestion@2.0.0-beta.10) (2021-03-31)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.9](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.8...@tiptap/suggestion@2.0.0-beta.9) (2021-03-28)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.8](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.7...@tiptap/suggestion@2.0.0-beta.8) (2021-03-28)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.7](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.6...@tiptap/suggestion@2.0.0-beta.7) (2021-03-28)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.6](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.5...@tiptap/suggestion@2.0.0-beta.6) (2021-03-24)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.5](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.4...@tiptap/suggestion@2.0.0-beta.5) (2021-03-18)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.4](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.3...@tiptap/suggestion@2.0.0-beta.4) (2021-03-18)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.3](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.2...@tiptap/suggestion@2.0.0-beta.3) (2021-03-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.2](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-beta.1...@tiptap/suggestion@2.0.0-beta.2) (2021-03-09)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-beta.1](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.12...@tiptap/suggestion@2.0.0-beta.1) (2021-03-05)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.12](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.11...@tiptap/suggestion@2.0.0-alpha.12) (2021-02-28)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.11](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.10...@tiptap/suggestion@2.0.0-alpha.11) (2021-02-26)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.10](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.9...@tiptap/suggestion@2.0.0-alpha.10) (2021-02-26)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.9](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.8...@tiptap/suggestion@2.0.0-alpha.9) (2021-02-18)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.8](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.7...@tiptap/suggestion@2.0.0-alpha.8) (2021-02-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.7](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.6...@tiptap/suggestion@2.0.0-alpha.7) (2021-02-16)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.6](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.5...@tiptap/suggestion@2.0.0-alpha.6) (2021-02-07)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.5](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.4...@tiptap/suggestion@2.0.0-alpha.5) (2021-02-05)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.4](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.3...@tiptap/suggestion@2.0.0-alpha.4) (2021-01-29)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.3](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.2...@tiptap/suggestion@2.0.0-alpha.3) (2021-01-29)

**Note:** Version bump only for package @tiptap/suggestion

# [2.0.0-alpha.2](https://github.com/ueberdosis/tiptap/compare/@tiptap/suggestion@2.0.0-alpha.1...@tiptap/suggestion@2.0.0-alpha.2) (2021-01-28)

**Note:** Version bump only for package @tiptap/suggestion

# 2.0.0-alpha.1 (2021-01-28)

**Note:** Version bump only for package @tiptap/suggestion
