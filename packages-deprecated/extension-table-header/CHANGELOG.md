# Change Log

## 3.0.7

### Patch Changes

- @tiptap/extension-table@3.0.7

## 3.0.6

### Patch Changes

- @tiptap/extension-table@3.0.6

## 3.0.5

### Patch Changes

- @tiptap/extension-table@3.0.5

## 3.0.4

### Patch Changes

- @tiptap/extension-table@3.0.4

## 3.0.3

### Patch Changes

- @tiptap/extension-table@3.0.3

## 3.0.2

### Patch Changes

- @tiptap/extension-table@3.0.2

## 3.0.1

### Major Changes

- a92f4a6: We are now building packages with tsup which does not support UMD builds, please repackage if you require UMD builds

### Minor Changes

- 131c7d0: This adds all of the table packages to the `@tiptap/extension-table` package.

  ## TableKit

  The `TableKit` export allows configuring the entire table with one extension, and is the recommended way of using the table extensions.

  ```ts
  import { TableKit } from '@tiptap/extension-table'

  new Editor({
    extensions: [
      TableKit.configure({
        table: {
          HTMLAttributes: {
            class: 'table',
          },
        },
        tableCell: {
          HTMLAttributes: {
            class: 'table-cell',
          },
        },
        tableHeader: {
          HTMLAttributes: {
            class: 'table-header',
          },
        },
        tableRow: {
          HTMLAttributes: {
            class: 'table-row',
          },
        },
      }),
    ],
  })
  ```

  ## Table repackaging

  Since we've moved the code out of the table extensions to the `@tiptap/extension-table` package, you can remove the following packages from your project:

  ```bash
  npm uninstall @tiptap/extension-table-header @tiptap/extension-table-cell @tiptap/extension-table-row
  ```

  And replace them with the new `@tiptap/extension-table` package:

  ```bash
  npm install @tiptap/extension-table
  ```

  ## Want to use the extensions separately?

  For more control, you can also use the extensions separately.

  ### Table

  This extension adds a table to the editor.

  Migrate from default export to named export:

  ```diff
  - import Table from '@tiptap/extension-table'
  + import { Table } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { Table } from '@tiptap/extension-table'
  ```

  ### TableCell

  This extension adds a table cell to the editor.

  Migrate from `@tiptap/extension-table-cell` to `@tiptap/extension-table`:

  ```diff
  - import TableCell from '@tiptap/extension-table-cell'
  + import { TableCell } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { TableCell } from '@tiptap/extension-table'
  ```

  ### TableHeader

  This extension adds a table header to the editor.

  Migrate from `@tiptap/extension-table-header` to `@tiptap/extension-table`:

  ```diff
  - import TableHeader from '@tiptap/extension-table-header'
  + import { TableHeader } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { TableHeader } from '@tiptap/extension-table'
  ```

  ### TableRow

  This extension adds a table row to the editor.

  Migrate from `@tiptap/extension-table-row` to `@tiptap/extension-table`:

  ```diff
  - import TableRow from '@tiptap/extension-table-row'
  + import { TableRow } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { TableRow } from '@tiptap/extension-table'
  ```

### Patch Changes

- 1b4c82b: We are now using pnpm package aliases for versions to enable better version pinning for the monorepository
- 89bd9c7: Enforce type imports so that the bundler ignores TypeScript type imports when generating the index.js file of the dist directory
- 8c69002: Synced beta with stable features
- Updated dependencies [1b4c82b]
- Updated dependencies [a92f4a6]
- Updated dependencies [89bd9c7]
- Updated dependencies [131c7d0]
- Updated dependencies [991f43c]
- Updated dependencies [8c69002]
  - @tiptap/extension-table@3.0.1

## 3.0.0-beta.30

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.30

## 3.0.0-beta.29

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.29

## 3.0.0-beta.28

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.28

## 3.0.0-beta.27

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.27

## 3.0.0-beta.26

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.26

## 3.0.0-beta.25

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.25

## 3.0.0-beta.24

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.24

## 3.0.0-beta.23

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.23

## 3.0.0-beta.22

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.22

## 3.0.0-beta.21

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.21

## 3.0.0-beta.20

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.20

## 3.0.0-beta.19

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.19

## 3.0.0-beta.18

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.18

## 3.0.0-beta.17

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.17

## 3.0.0-beta.16

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.16

## 3.0.0-beta.15

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.15

## 3.0.0-beta.14

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.14

## 3.0.0-beta.13

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.13

## 3.0.0-beta.12

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.12

## 3.0.0-beta.11

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.11

## 3.0.0-beta.10

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.10

## 3.0.0-beta.9

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.9

## 3.0.0-beta.8

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.8

## 3.0.0-beta.7

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.7

## 3.0.0-beta.6

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.6

## 3.0.0-beta.5

### Patch Changes

- 8c69002: Synced beta with stable features
- Updated dependencies [8c69002]
  - @tiptap/extension-table@3.0.0-beta.5

## 3.0.0-beta.4

### Patch Changes

- @tiptap/extension-table@3.0.0-beta.4

## 3.0.0-beta.3

### Patch Changes

- 1b4c82b: We are now using pnpm package aliases for versions to enable better version pinning for the monorepository
- Updated dependencies [1b4c82b]
  - @tiptap/extension-table@3.0.0-beta.3

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

### Minor Changes

- 131c7d0: This adds all of the table packages to the `@tiptap/extension-table` package.

  ## TableKit

  The `TableKit` export allows configuring the entire table with one extension, and is the recommended way of using the table extensions.

  ```ts
  import { TableKit } from '@tiptap/extension-table'

  new Editor({
    extensions: [
      TableKit.configure({
        table: {
          HTMLAttributes: {
            class: 'table',
          },
        },
        tableCell: {
          HTMLAttributes: {
            class: 'table-cell',
          },
        },
        tableHeader: {
          HTMLAttributes: {
            class: 'table-header',
          },
        },
        tableRow: {
          HTMLAttributes: {
            class: 'table-row',
          },
        },
      }),
    ],
  })
  ```

  ## Table repackaging

  Since we've moved the code out of the table extensions to the `@tiptap/extension-table` package, you can remove the following packages from your project:

  ```bash
  npm uninstall @tiptap/extension-table-header @tiptap/extension-table-cell @tiptap/extension-table-row
  ```

  And replace them with the new `@tiptap/extension-table` package:

  ```bash
  npm install @tiptap/extension-table
  ```

  ## Want to use the extensions separately?

  For more control, you can also use the extensions separately.

  ### Table

  This extension adds a table to the editor.

  Migrate from default export to named export:

  ```diff
  - import Table from '@tiptap/extension-table'
  + import { Table } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { Table } from '@tiptap/extension-table'
  ```

  ### TableCell

  This extension adds a table cell to the editor.

  Migrate from `@tiptap/extension-table-cell` to `@tiptap/extension-table`:

  ```diff
  - import TableCell from '@tiptap/extension-table-cell'
  + import { TableCell } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { TableCell } from '@tiptap/extension-table'
  ```

  ### TableHeader

  This extension adds a table header to the editor.

  Migrate from `@tiptap/extension-table-header` to `@tiptap/extension-table`:

  ```diff
  - import TableHeader from '@tiptap/extension-table-header'
  + import { TableHeader } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { TableHeader } from '@tiptap/extension-table'
  ```

  ### TableRow

  This extension adds a table row to the editor.

  Migrate from `@tiptap/extension-table-row` to `@tiptap/extension-table`:

  ```diff
  - import TableRow from '@tiptap/extension-table-row'
  + import { TableRow } from '@tiptap/extension-table'
  ```

  Usage:

  ```ts
  import { TableRow } from '@tiptap/extension-table'
  ```

## 3.0.0-next.5

## 3.0.0-next.4

### Minor Changes

- 131c7d0: This change repackages all of the table extensions to be within the `@tiptap/extension-table` package (other packages are just a re-export of the `@tiptap/extension-table` package). It also adds the `TableKit` export which will allow configuring the entire table with one extension.

## 3.0.0-next.3

## 3.0.0-next.2

## 3.0.0-next.1

### Major Changes

- a92f4a6: We are now building packages with tsup which does not support UMD builds, please repackage if you require UMD builds

### Patch Changes

- Updated dependencies [a92f4a6]
- Updated dependencies [da76972]
  - @tiptap/core@3.0.0-next.1

## 3.0.0-next.0

### Patch Changes

- Updated dependencies [0ec0af6]
  - @tiptap/core@3.0.0-next.0

## 2.12.0

## 2.11.9

## 2.11.8

## 2.11.7

## 2.11.6

## 2.11.5

## 2.11.4

## 2.11.3

## 2.11.2

## 2.11.1

## 2.11.0

## 2.10.4

## 2.10.3

## 2.10.2

## 2.10.1

## 2.10.0

## 2.9.1

## 2.9.0

### Patch Changes

- 21df331: Tables now properly respect colwidths with multiple values, fixing resizeable columns when the first row has a colspan

## 2.8.0

## 2.5.8

### Patch Changes

- Updated dependencies [a08bf85]
  - @tiptap/core@2.5.8

## 2.5.7

### Patch Changes

- Updated dependencies [b012471]
- Updated dependencies [cc3497e]
  - @tiptap/core@2.5.7

## 2.5.6

### Patch Changes

- Updated dependencies [618bca9]
- Updated dependencies [35682d1]
- Updated dependencies [2104f0f]
  - @tiptap/core@2.5.6

## 2.5.5

### Patch Changes

- Updated dependencies [4cca382]
- Updated dependencies [3b67e8a]
  - @tiptap/core@2.5.5

## 2.5.4

### Patch Changes

- dd7f9ac: There was an issue with the cjs bundling of packages and default exports, now we resolve default exports in legacy compatible way
- Updated dependencies [dd7f9ac]
  - @tiptap/core@2.5.4

## 2.5.3

### Patch Changes

- @tiptap/core@2.5.3

## 2.5.2

### Patch Changes

- Updated dependencies [07f4c03]
  - @tiptap/core@2.5.2

## 2.5.1

### Patch Changes

- @tiptap/core@2.5.1

## 2.5.0

### Patch Changes

- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
  - @tiptap/core@2.5.0

## 2.5.0-pre.16

### Patch Changes

- @tiptap/core@2.5.0-pre.16

## 2.5.0-pre.15

### Patch Changes

- @tiptap/core@2.5.0-pre.15

## 2.5.0-pre.14

### Patch Changes

- @tiptap/core@2.5.0-pre.14

## 2.5.0-pre.13

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.13

## 2.5.0-pre.12

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.12

## 2.5.0-pre.11

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.11

## 2.5.0-pre.10

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.10

## 2.5.0-pre.9

### Patch Changes

- Updated dependencies [14a00f4]
  - @tiptap/core@2.5.0-pre.9

## 2.5.0-pre.8

### Patch Changes

- Updated dependencies [509676e]
  - @tiptap/core@2.5.0-pre.8

## 2.5.0-pre.7

### Patch Changes

- @tiptap/core@2.5.0-pre.7

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.

# [2.4.0](https://github.com/ueberdosis/tiptap/compare/v2.3.2...v2.4.0) (2024-05-14)

### Features

- added jsdocs ([#4356](https://github.com/ueberdosis/tiptap/issues/4356)) ([b941eea](https://github.com/ueberdosis/tiptap/commit/b941eea6daba09d48a5d18ccc1b9a1d84b2249dd))

## [2.3.2](https://github.com/ueberdosis/tiptap/compare/v2.3.1...v2.3.2) (2024-05-08)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.3.1](https://github.com/ueberdosis/tiptap/compare/v2.3.0...v2.3.1) (2024-04-30)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.3.0](https://github.com/ueberdosis/tiptap/compare/v2.2.6...v2.3.0) (2024-04-09)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.2.6](https://github.com/ueberdosis/tiptap/compare/v2.2.5...v2.2.6) (2024-04-06)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.2.5](https://github.com/ueberdosis/tiptap/compare/v2.2.4...v2.2.5) (2024-04-05)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.2.4](https://github.com/ueberdosis/tiptap/compare/v2.2.3...v2.2.4) (2024-02-23)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.2.3](https://github.com/ueberdosis/tiptap/compare/v2.2.2...v2.2.3) (2024-02-15)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.2.2](https://github.com/ueberdosis/tiptap/compare/v2.2.1...v2.2.2) (2024-02-07)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.2.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0...v2.2.1) (2024-01-31)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.2.0](https://github.com/ueberdosis/tiptap/compare/v2.1.16...v2.2.0) (2024-01-29)

# [2.2.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.2.0-rc.8) (2024-01-08)

# [2.2.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.6...v2.2.0-rc.7) (2023-11-27)

# [2.2.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.5...v2.2.0-rc.6) (2023-11-23)

# [2.2.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.2.0-rc.4) (2023-10-10)

# [2.2.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.2...v2.2.0-rc.3) (2023-08-18)

# [2.2.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.0...v2.2.0-rc.1) (2023-08-18)

# [2.2.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.2.0-rc.0) (2023-08-18)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.16](https://github.com/ueberdosis/tiptap/compare/v2.1.15...v2.1.16) (2024-01-10)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.15](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.1.15) (2024-01-08)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.14](https://github.com/ueberdosis/tiptap/compare/v2.1.13...v2.1.14) (2024-01-08)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.13](https://github.com/ueberdosis/tiptap/compare/v2.1.12...v2.1.13) (2023-11-30)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.12](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.1.12) (2023-10-11)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.11](https://github.com/ueberdosis/tiptap/compare/v2.1.10...v2.1.11) (2023-09-20)

### Reverts

- Revert "v2.2.11" ([6aa755a](https://github.com/ueberdosis/tiptap/commit/6aa755a04b9955fc175c7ab33dee527d0d5deef0))

## [2.1.10](https://github.com/ueberdosis/tiptap/compare/v2.1.9...v2.1.10) (2023-09-15)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.9](https://github.com/ueberdosis/tiptap/compare/v2.1.8...v2.1.9) (2023-09-14)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.8](https://github.com/ueberdosis/tiptap/compare/v2.1.7...v2.1.8) (2023-09-04)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.7](https://github.com/ueberdosis/tiptap/compare/v2.1.6...v2.1.7) (2023-09-04)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.6](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.1.6) (2023-08-18)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.5](https://github.com/ueberdosis/tiptap/compare/v2.1.4...v2.1.5) (2023-08-18)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.4](https://github.com/ueberdosis/tiptap/compare/v2.1.3...v2.1.4) (2023-08-18)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.3](https://github.com/ueberdosis/tiptap/compare/v2.1.2...v2.1.3) (2023-08-18)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.2](https://github.com/ueberdosis/tiptap/compare/v2.1.1...v2.1.2) (2023-08-17)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.1.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0...v2.1.1) (2023-08-16)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.14...v2.1.0) (2023-08-16)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.14](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.13...v2.1.0-rc.14) (2023-08-11)

**Note:** Version bump only for package @tiptap/extension-table-header

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

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.11](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.10...v2.1.0-rc.11) (2023-07-07)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.10](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.9...v2.1.0-rc.10) (2023-07-07)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.9](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.8...v2.1.0-rc.9) (2023-06-15)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.7...v2.1.0-rc.8) (2023-05-25)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.6...v2.1.0-rc.7) (2023-05-25)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.5...v2.1.0-rc.6) (2023-05-25)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.5](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.4...v2.1.0-rc.5) (2023-05-25)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.3...v2.1.0-rc.4) (2023-04-27)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.2...v2.1.0-rc.3) (2023-04-26)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.2](https://github.com/ueberdosis/tiptap/compare/v2.0.3...v2.1.0-rc.2) (2023-04-26)

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0c1bba3](https://github.com/ueberdosis/tiptap/commit/0c1bba3137b535776bcef95ff3c55e13f5a2db46))

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.0.3](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.0.3) (2023-04-13)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.0.2](https://github.com/ueberdosis/tiptap/compare/v2.0.1...v2.0.2) (2023-04-03)

**Note:** Version bump only for package @tiptap/extension-table-header

## [2.0.1](https://github.com/ueberdosis/tiptap/compare/v2.0.0...v2.0.1) (2023-03-30)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0534f76](https://github.com/ueberdosis/tiptap/commit/0534f76401bf5399c01ca7f39d87f7221d91b4f7))

# [2.0.0-beta.220](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.219...v2.0.0-beta.220) (2023-02-28)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.219](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.218...v2.0.0-beta.219) (2023-02-27)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.218](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.217...v2.0.0-beta.218) (2023-02-18)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.217](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.216...v2.0.0-beta.217) (2023-02-09)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.216](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.215...v2.0.0-beta.216) (2023-02-08)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.215](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.214...v2.0.0-beta.215) (2023-02-08)

### Bug Fixes

- fix builds including prosemirror ([a380ec4](https://github.com/ueberdosis/tiptap/commit/a380ec41d198ebacc80cea9e79b0a8aa3092618a))

# [2.0.0-beta.214](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.213...v2.0.0-beta.214) (2023-02-08)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.213](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.212...v2.0.0-beta.213) (2023-02-07)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.212](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.211...v2.0.0-beta.212) (2023-02-03)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.211](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.210...v2.0.0-beta.211) (2023-02-02)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.210](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.209...v2.0.0-beta.210) (2023-02-02)

### Features

- **pm:** new prosemirror package for dependency resolving ([f387ad3](https://github.com/ueberdosis/tiptap/commit/f387ad3dd4c2b30eaea33fb0ba0b42e0cd39263b))

# [2.0.0-beta.209](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.208...v2.0.0-beta.209) (2022-12-16)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.208](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.207...v2.0.0-beta.208) (2022-12-16)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.207](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.206...v2.0.0-beta.207) (2022-12-08)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.206](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.205...v2.0.0-beta.206) (2022-12-08)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.205](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.204...v2.0.0-beta.205) (2022-12-05)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.204](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.203...v2.0.0-beta.204) (2022-11-25)

### Bug Fixes

- **core:** rename esm modules to esm.js ([c1a0c3a](https://github.com/ueberdosis/tiptap/commit/c1a0c3ae43baac9dd5ed90903d3a0d4eaeea7702))

# [2.0.0-beta.203](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.202...v2.0.0-beta.203) (2022-11-24)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.202](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.201...v2.0.0-beta.202) (2022-11-04)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.201](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.200...v2.0.0-beta.201) (2022-11-04)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.200](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.199...v2.0.0-beta.200) (2022-11-04)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.199](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.198...v2.0.0-beta.199) (2022-09-30)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.198](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.197...v2.0.0-beta.198) (2022-09-29)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.197](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.196...v2.0.0-beta.197) (2022-09-26)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.196](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.195...v2.0.0-beta.196) (2022-09-20)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.195](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.194...v2.0.0-beta.195) (2022-09-14)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.194](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.193...v2.0.0-beta.194) (2022-09-11)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.25](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.23...@tiptap/extension-table-header@2.0.0-beta.25) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.23](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.23...@tiptap/extension-table-header@2.0.0-beta.23) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.22](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.21...@tiptap/extension-table-header@2.0.0-beta.22) (2021-11-09)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.21](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.20...@tiptap/extension-table-header@2.0.0-beta.21) (2021-11-09)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.20](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.19...@tiptap/extension-table-header@2.0.0-beta.20) (2021-11-09)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.19](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.18...@tiptap/extension-table-header@2.0.0-beta.19) (2021-10-31)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.18](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.17...@tiptap/extension-table-header@2.0.0-beta.18) (2021-10-26)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.17](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.16...@tiptap/extension-table-header@2.0.0-beta.17) (2021-09-08)

### Features

- parseHTML for attributes should return the value instead of an object now, fix [#1863](https://github.com/ueberdosis/tiptap/issues/1863) ([8a3b47a](https://github.com/ueberdosis/tiptap/commit/8a3b47a529d28b28b50d634c6ff69b8e5aad3080))

# [2.0.0-beta.16](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.15...@tiptap/extension-table-header@2.0.0-beta.16) (2021-07-26)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.15](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.14...@tiptap/extension-table-header@2.0.0-beta.15) (2021-05-18)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.14](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.13...@tiptap/extension-table-header@2.0.0-beta.14) (2021-05-13)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.13](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.12...@tiptap/extension-table-header@2.0.0-beta.13) (2021-05-07)

### Bug Fixes

- revert adding exports ([bc320d0](https://github.com/ueberdosis/tiptap/commit/bc320d0b4b80b0e37a7e47a56e0f6daec6e65d98))

# [2.0.0-beta.12](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.11...@tiptap/extension-table-header@2.0.0-beta.12) (2021-05-06)

### Bug Fixes

- revert adding type: module ([f8d6475](https://github.com/ueberdosis/tiptap/commit/f8d6475e2151faea6f96baecdd6bd75880d50d2c))

# [2.0.0-beta.11](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.10...@tiptap/extension-table-header@2.0.0-beta.11) (2021-05-06)

### Bug Fixes

- add exports to package.json ([1277fa4](https://github.com/ueberdosis/tiptap/commit/1277fa47151e9c039508cdb219bdd0ffe647f4ee))

# [2.0.0-beta.10](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.9...@tiptap/extension-table-header@2.0.0-beta.10) (2021-05-06)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.9](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.8...@tiptap/extension-table-header@2.0.0-beta.9) (2021-05-05)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.8](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.7...@tiptap/extension-table-header@2.0.0-beta.8) (2021-04-23)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.7](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.6...@tiptap/extension-table-header@2.0.0-beta.7) (2021-04-22)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.6](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.5...@tiptap/extension-table-header@2.0.0-beta.6) (2021-04-21)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.5](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.4...@tiptap/extension-table-header@2.0.0-beta.5) (2021-04-16)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.4](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.3...@tiptap/extension-table-header@2.0.0-beta.4) (2021-04-15)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.3](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.2...@tiptap/extension-table-header@2.0.0-beta.3) (2021-03-31)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.2](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-beta.1...@tiptap/extension-table-header@2.0.0-beta.2) (2021-03-28)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-beta.1](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-alpha.11...@tiptap/extension-table-header@2.0.0-beta.1) (2021-03-05)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-alpha.11](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-alpha.10...@tiptap/extension-table-header@2.0.0-alpha.11) (2021-02-16)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-alpha.10](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-alpha.9...@tiptap/extension-table-header@2.0.0-alpha.10) (2021-02-07)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-alpha.9](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-alpha.8...@tiptap/extension-table-header@2.0.0-alpha.9) (2021-02-05)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-alpha.8](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-alpha.7...@tiptap/extension-table-header@2.0.0-alpha.8) (2021-01-29)

**Note:** Version bump only for package @tiptap/extension-table-header

# [2.0.0-alpha.7](https://github.com/ueberdosis/tiptap/compare/@tiptap/extension-table-header@2.0.0-alpha.6...@tiptap/extension-table-header@2.0.0-alpha.7) (2021-01-29)

**Note:** Version bump only for package @tiptap/extension-table-header

# 2.0.0-alpha.6 (2021-01-28)

**Note:** Version bump only for package @tiptap/extension-table-header
