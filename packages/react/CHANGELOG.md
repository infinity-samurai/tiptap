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

- 0e3207f: Add support for [markviews](https://prosemirror.net/docs/ref/#view.MarkView), which allow you to render custom views for marks within the editor. This is useful for rendering custom UI for marks, like a color picker for a text color mark or a link editor for a link mark.

  Here is a plain JS markview example:

  ```ts
  Mark.create({
    // Other options...
    addMarkView() {
      return ({ mark, HTMLAttributes }) => {
        const dom = document.createElement('b')
        const contentDOM = document.createElement('span')

        dom.appendChild(contentDOM)

        return {
          dom,
          contentDOM,
        }
      }
    },
  })
  ```

  ## React binding

  To use a React component for a markview, you can use the `@tiptap/react` package:

  ```ts
  import { Mark } from '@tiptap/core'
  import { ReactMarkViewRenderer } from '@tiptap/react'

  import Component from './Component.jsx'

  export default Mark.create({
    name: 'reactComponent',

    parseHTML() {
      return [
        {
          tag: 'react-component',
        },
      ]
    },

    renderHTML({ HTMLAttributes }) {
      return ['react-component', HTMLAttributes]
    },

    addMarkView() {
      return ReactMarkViewRenderer(Component)
    },
  })
  ```

  And here is an example of a React component:

  ```tsx
  import { MarkViewContent, MarkViewRendererProps } from '@tiptap/react'
  import React from 'react'

  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  export default (props: MarkViewRendererProps) => {
    const [count, setCount] = React.useState(0)

    return (
      <span className="content" data-test-id="mark-view">
        <MarkViewContent />
        <label contentEditable={false}>
          React component:
          <button
            onClick={() => {
              setCount(count + 1)
            }}
          >
            This button has been clicked {count} times.
          </button>
        </label>
      </span>
    )
  }
  ```

  ## Vue 3 binding

  To use a Vue 3 component for a markview, you can use the `@tiptap/vue-3` package:

  ```ts
  import { Mark } from '@tiptap/core'
  import { VueMarkViewRenderer } from '@tiptap/vue-3'

  import Component from './Component.vue'

  export default Mark.create({
    name: 'vueComponent',

    parseHTML() {
      return [
        {
          tag: 'vue-component',
        },
      ]
    },

    renderHTML({ HTMLAttributes }) {
      return ['vue-component', HTMLAttributes]
    },

    addMarkView() {
      return VueMarkViewRenderer(Component)
    },
  })
  ```

  And here is an example of a Vue 3 component:

  ```vue
  <template>
    <span className="content" data-test-id="mark-view">
      <mark-view-content />
      <label contenteditable="false"
        >Vue Component::
        <button @click="increase" class="primary">This button has been clicked {{ count }} times.</button>
      </label>
    </span>
  </template>

  <script>
  import { MarkViewContent, markViewProps } from '@tiptap/vue-3'
  export default {
    components: {
      MarkViewContent,
    },
    data() {
      return {
        count: 0,
      }
    },
    props: markViewProps,
    methods: {
      increase() {
        this.count += 1
      },
    },
  }
  </script>
  ```

- 08593a2: Throw an error in development mode if `immediatelyRender` is not set in SSR mode
- ef12b32: Added support for React 19 ref in props
- cce6497: Reintroduce flushSync to sync rendering of React and ProseMirror

### Patch Changes

- baee94b: Added full import path for external storage sync shim
- 1b4c82b: We are now using pnpm package aliases for versions to enable better version pinning for the monorepository
- 89bd9c7: Enforce type imports so that the bundler ignores TypeScript type imports when generating the index.js file of the dist directory
- 00693b8: Fixed a bug where table cell selections would not position the bubble menu accordingly
- f9a33ae: Fixed a bug that incorrectly added ref props when a component can't accept them (for example when React 19 is not used)
- 73d1888: Fixed a bug where the global resize handler of the BubbleMenu plugin would not be unregistered on destroy
- ecb0dee: Fixes an issue where ref props will be kept on non-supported react components
- 2ea0475: Allow setting HTML tags other than <span> for "as" in MarkViewContent
- 8c69002: Synced beta with stable features
- 0f14cc5: Added missing `onShow`, `onUpdate`, `onHide` and `onDestroy` options
- de0504e: attach the contentDOM to the correct position inside a react node view
- 5ba480b: Added `updateAttributes` to MarkView and its renderers to allow updating MarkView attributes
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

### Patch Changes

- @tiptap/core@3.0.0-beta.29
- @tiptap/pm@3.0.0-beta.29

## 3.0.0-beta.28

### Patch Changes

- de0504e: attach the contentDOM to the correct position inside a react node view
  - @tiptap/core@3.0.0-beta.28
  - @tiptap/pm@3.0.0-beta.28

## 3.0.0-beta.27

### Patch Changes

- Updated dependencies [412e1bd]
  - @tiptap/core@3.0.0-beta.27
  - @tiptap/pm@3.0.0-beta.27

## 3.0.0-beta.26

### Patch Changes

- baee94b: Added full import path for external storage sync shim
- 5ba480b: Added `updateAttributes` to MarkView and its renderers to allow updating MarkView attributes
- Updated dependencies [5ba480b]
  - @tiptap/core@3.0.0-beta.26
  - @tiptap/pm@3.0.0-beta.26

## 3.0.0-beta.25

### Patch Changes

- Updated dependencies [4e2f6d8]
  - @tiptap/core@3.0.0-beta.25
  - @tiptap/pm@3.0.0-beta.25

## 3.0.0-beta.24

### Minor Changes

- cce6497: Reintroduce flushSync to sync rendering of React and ProseMirror

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

### Minor Changes

- 8719e13: Removed flushSync on NodeView render which caused performance regressions, bugs with unused NodeViews still being reconciled for PMViewDesc checks and more

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

- 73d1888: Fixed a bug where the global resize handler of the BubbleMenu plugin would not be unregistered on destroy
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

- 00693b8: Fixed a bug where table cell selections would not position the bubble menu accordingly
  - @tiptap/core@3.0.0-beta.12
  - @tiptap/pm@3.0.0-beta.12

## 3.0.0-beta.11

### Patch Changes

- 0f14cc5: Added missing `onShow`, `onUpdate`, `onHide` and `onDestroy` options
  - @tiptap/core@3.0.0-beta.11
  - @tiptap/pm@3.0.0-beta.11

## 3.0.0-beta.10

### Patch Changes

- @tiptap/core@3.0.0-beta.10
- @tiptap/pm@3.0.0-beta.10

## 3.0.0-beta.9

### Patch Changes

- ecb0dee: Fixes an issue where ref props will be kept on non-supported react components
  - @tiptap/core@3.0.0-beta.9
  - @tiptap/pm@3.0.0-beta.9

## 3.0.0-beta.8

### Patch Changes

- f9a33ae: Fixed a bug that incorrectly added ref props when a component can't accept them (for example when React 19 is not used)
  - @tiptap/core@3.0.0-beta.8
  - @tiptap/pm@3.0.0-beta.8

## 3.0.0-beta.7

### Patch Changes

- Updated dependencies [d0fda30]
  - @tiptap/core@3.0.0-beta.7
  - @tiptap/pm@3.0.0-beta.7

## 3.0.0-beta.6

### Minor Changes

- ef12b32: Added support for React 19 ref in props

### Patch Changes

- 2ea0475: Allow setting HTML tags other than <span> for "as" in MarkViewContent
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

### Patch Changes

- 3aa670a: Fixed a bug in the EditorContent component that caused a crash in Firefox based browsers because of the editor view not being available when an uninitialized editor is unmounted (for example via Strict mode)

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

### Minor Changes

- 0e3207f: Add support for [markviews](https://prosemirror.net/docs/ref/#view.MarkView), which allow you to render custom views for marks within the editor. This is useful for rendering custom UI for marks, like a color picker for a text color mark or a link editor for a link mark.

  Here is a plain JS markview example:

  ```ts
  Mark.create({
    // Other options...
    addMarkView() {
      return ({ mark, HTMLAttributes }) => {
        const dom = document.createElement('b')
        const contentDOM = document.createElement('span')

        dom.appendChild(contentDOM)

        return {
          dom,
          contentDOM,
        }
      }
    },
  })
  ```

  ## React binding

  To use a React component for a markview, you can use the `@tiptap/react` package:

  ```ts
  import { Mark } from '@tiptap/core'
  import { ReactMarkViewRenderer } from '@tiptap/react'

  import Component from './Component.jsx'

  export default Mark.create({
    name: 'reactComponent',

    parseHTML() {
      return [
        {
          tag: 'react-component',
        },
      ]
    },

    renderHTML({ HTMLAttributes }) {
      return ['react-component', HTMLAttributes]
    },

    addMarkView() {
      return ReactMarkViewRenderer(Component)
    },
  })
  ```

  And here is an example of a React component:

  ```tsx
  import { MarkViewContent, MarkViewRendererProps } from '@tiptap/react'
  import React from 'react'

  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  export default (props: MarkViewRendererProps) => {
    const [count, setCount] = React.useState(0)

    return (
      <span className="content" data-test-id="mark-view">
        <MarkViewContent />
        <label contentEditable={false}>
          React component:
          <button
            onClick={() => {
              setCount(count + 1)
            }}
          >
            This button has been clicked {count} times.
          </button>
        </label>
      </span>
    )
  }
  ```

  ## Vue 3 binding

  To use a Vue 3 component for a markview, you can use the `@tiptap/vue-3` package:

  ```ts
  import { Mark } from '@tiptap/core'
  import { VueMarkViewRenderer } from '@tiptap/vue-3'

  import Component from './Component.vue'

  export default Mark.create({
    name: 'vueComponent',

    parseHTML() {
      return [
        {
          tag: 'vue-component',
        },
      ]
    },

    renderHTML({ HTMLAttributes }) {
      return ['vue-component', HTMLAttributes]
    },

    addMarkView() {
      return VueMarkViewRenderer(Component)
    },
  })
  ```

  And here is an example of a Vue 3 component:

  ```vue
  <template>
    <span className="content" data-test-id="mark-view">
      <mark-view-content />
      <label contenteditable="false"
        >Vue Component::
        <button @click="increase" class="primary">This button has been clicked {{ count }} times.</button>
      </label>
    </span>
  </template>

  <script>
  import { MarkViewContent, markViewProps } from '@tiptap/vue-3'
  export default {
    components: {
      MarkViewContent,
    },
    data() {
      return {
        count: 0,
      }
    },
    props: markViewProps,
    methods: {
      increase() {
        this.count += 1
      },
    },
  }
  </script>
  ```

- 08593a2: Throw an error in development mode if `immediatelyRender` is not set in SSR mode

## 3.0.0-next.5

### Minor Changes

- 0e3207f: Add support for [markviews](https://prosemirror.net/docs/ref/#view.MarkView), which allow you to render custom views for marks within the editor. This is useful for rendering custom UI for marks, like a color picker for a text color mark or a link editor for a link mark.

  Here is a plain JS markview example:

  ```ts
  Mark.create({
    // Other options...
    addMarkView() {
      return ({ mark, HTMLAttributes }) => {
        const dom = document.createElement('b')
        const contentDOM = document.createElement('span')

        dom.appendChild(contentDOM)

        return {
          dom,
          contentDOM,
        }
      }
    },
  })
  ```

  ## React binding

  To use a React component for a markview, you can use the `@tiptap/react` package:

  ```ts
  import { Mark } from '@tiptap/core'
  import { ReactMarkViewRenderer } from '@tiptap/react'

  import Component from './Component.jsx'

  export default Mark.create({
    name: 'reactComponent',

    parseHTML() {
      return [
        {
          tag: 'react-component',
        },
      ]
    },

    renderHTML({ HTMLAttributes }) {
      return ['react-component', HTMLAttributes]
    },

    addMarkView() {
      return ReactMarkViewRenderer(Component)
    },
  })
  ```

  And here is an example of a React component:

  ```tsx
  import { MarkViewContent, MarkViewRendererProps } from '@tiptap/react'
  import React from 'react'

  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  export default (props: MarkViewRendererProps) => {
    const [count, setCount] = React.useState(0)

    return (
      <span className="content" data-test-id="mark-view">
        <MarkViewContent />
        <label contentEditable={false}>
          React component:
          <button
            onClick={() => {
              setCount(count + 1)
            }}
          >
            This button has been clicked {count} times.
          </button>
        </label>
      </span>
    )
  }
  ```

  ## Vue 3 binding

  To use a Vue 3 component for a markview, you can use the `@tiptap/vue-3` package:

  ```ts
  import { Mark } from '@tiptap/core'
  import { VueMarkViewRenderer } from '@tiptap/vue-3'

  import Component from './Component.vue'

  export default Mark.create({
    name: 'vueComponent',

    parseHTML() {
      return [
        {
          tag: 'vue-component',
        },
      ]
    },

    renderHTML({ HTMLAttributes }) {
      return ['vue-component', HTMLAttributes]
    },

    addMarkView() {
      return VueMarkViewRenderer(Component)
    },
  })
  ```

  And here is an example of a Vue 3 component:

  ```vue
  <template>
    <span className="content" data-test-id="mark-view">
      <mark-view-content />
      <label contenteditable="false"
        >Vue Component::
        <button @click="increase" class="primary">This button has been clicked {{ count }} times.</button>
      </label>
    </span>
  </template>

  <script>
  import { MarkViewContent, markViewProps } from '@tiptap/vue-3'
  export default {
    components: {
      MarkViewContent,
    },
    data() {
      return {
        count: 0,
      }
    },
    props: markViewProps,
    methods: {
      increase() {
        this.count += 1
      },
    },
  }
  </script>
  ```

## 3.0.0-next.4

## 3.0.0-next.3

### Patch Changes

- @tiptap/extension-bubble-menu@3.0.0-next.3
- @tiptap/extension-floating-menu@3.0.0-next.3

## 3.0.0-next.2

### Patch Changes

- Updated dependencies [d9b6ef5]
  - @tiptap/extension-floating-menu@3.0.0-next.2
  - @tiptap/extension-bubble-menu@3.0.0-next.2

## 3.0.0-next.1

### Major Changes

- a92f4a6: We are now building packages with tsup which does not support UMD builds, please repackage if you require UMD builds

### Minor Changes

- 08593a2: Throw an error in development mode if immediatelyRender is not set in SSR mode

### Patch Changes

- Updated dependencies [a92f4a6]
- Updated dependencies [da76972]
  - @tiptap/extension-floating-menu@3.0.0-next.1
  - @tiptap/extension-bubble-menu@3.0.0-next.1
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

- Updated dependencies [7eaa34d]
- Updated dependencies [0ec0af6]
  - @tiptap/extension-floating-menu@3.0.0-next.0
  - @tiptap/extension-bubble-menu@3.0.0-next.0
  - @tiptap/core@3.0.0-next.0
  - @tiptap/pm@3.0.0-next.0

## 2.12.0

### Patch Changes

- @tiptap/extension-bubble-menu@2.12.0
- @tiptap/extension-floating-menu@2.12.0

## 2.11.9

### Patch Changes

- @tiptap/extension-bubble-menu@2.11.9
- @tiptap/extension-floating-menu@2.11.9

## 2.11.8

### Patch Changes

- @tiptap/extension-bubble-menu@2.11.8
- @tiptap/extension-floating-menu@2.11.8

## 2.11.7

### Patch Changes

- @tiptap/extension-bubble-menu@2.11.7
- @tiptap/extension-floating-menu@2.11.7

## 2.11.6

### Patch Changes

- @tiptap/extension-bubble-menu@2.11.6
- @tiptap/extension-floating-menu@2.11.6

## 2.11.5

### Patch Changes

- @tiptap/extension-bubble-menu@2.11.5
- @tiptap/extension-floating-menu@2.11.5

## 2.11.4

### Patch Changes

- @tiptap/extension-bubble-menu@2.11.4
- @tiptap/extension-floating-menu@2.11.4

## 2.11.3

### Patch Changes

- @tiptap/extension-bubble-menu@3.0.0-next.4
- @tiptap/extension-floating-menu@3.0.0-next.4

## 2.5.8

### Patch Changes

- 99d7820: Resolve a bug an editor could be instantiated but not destroyed. This was causing issues with multiple instances of plugins still being active and interfering with each other
- Updated dependencies [a08bf85]
  - @tiptap/core@2.5.8
  - @tiptap/extension-bubble-menu@2.5.8
  - @tiptap/extension-floating-menu@2.5.8
  - @tiptap/pm@2.5.8

## 2.5.7

### Patch Changes

- 42dc27a: Fix, if using a deps array destroy the previous instance to avoid ghost instances
- Updated dependencies [b012471]
- Updated dependencies [cc3497e]
  - @tiptap/core@2.5.7
  - @tiptap/extension-bubble-menu@2.5.7
  - @tiptap/extension-floating-menu@2.5.7
  - @tiptap/pm@2.5.7

## 2.5.6

### Patch Changes

- Updated dependencies [b5c1b32]
- Updated dependencies [618bca9]
- Updated dependencies [35682d1]
- Updated dependencies [2104f0f]
  - @tiptap/pm@2.5.6
  - @tiptap/core@2.5.6
  - @tiptap/extension-bubble-menu@2.5.6
  - @tiptap/extension-floating-menu@2.5.6

## 2.5.5

### Patch Changes

- Updated dependencies [4cca382]
- Updated dependencies [3b67e8a]
  - @tiptap/core@2.5.5
  - @tiptap/extension-bubble-menu@2.5.5
  - @tiptap/extension-floating-menu@2.5.5
  - @tiptap/pm@2.5.5

## 2.5.4

### Patch Changes

- dd7f9ac: There was an issue with the cjs bundling of packages and default exports, now we resolve default exports in legacy compatible way
- Updated dependencies [dd7f9ac]
  - @tiptap/extension-floating-menu@2.5.4
  - @tiptap/extension-bubble-menu@2.5.4
  - @tiptap/core@2.5.4
  - @tiptap/pm@2.5.4

## 2.5.3

### Patch Changes

- 70eebfd: The optional deps argument to useEditor was not being respected for performance optimizations, now if deps are declared a new editor instance is created
  - @tiptap/core@2.5.3
  - @tiptap/extension-bubble-menu@2.5.3
  - @tiptap/extension-floating-menu@2.5.3
  - @tiptap/pm@2.5.3

## 2.5.2

### Patch Changes

- Updated dependencies [07f4c03]
  - @tiptap/core@2.5.2
  - @tiptap/extension-bubble-menu@2.5.2
  - @tiptap/extension-floating-menu@2.5.2
  - @tiptap/pm@2.5.2

## 2.5.1

### Patch Changes

- @tiptap/core@2.5.1
- @tiptap/extension-bubble-menu@2.5.1
- @tiptap/extension-floating-menu@2.5.1
- @tiptap/pm@2.5.1

## 2.5.0

### Patch Changes

- fb45149: Fixes strict mode accidentally destroying the editor instance
- fb45149: Fix the typings
- fb45149: We've heard a number of complaints around the performance of our React integration, and we finally have a solution that we believe will satisfy everyone. We've made a number of optimizations to how the editor is rendered, as well give you more control over the rendering process.

  Here is a summary of the changes and how you can take advantage of them:

  - SSR rendering was holding back our ability to have an editor instance on first render of `useEditor`. We've now made the default behavior to render the editor immediately on the client. This behavior can be controlled with the new `immediatelyRender` option which when set to `false` will defer rendering until the second render (via a useEffect), this should only be used when server-side rendering.
  - The default behavior of the useEditor hook is to re-render the editor on every editor transaction. Now with the `shouldRerenderOnTransaction` option, you can disable this behavior to optimize performance. Instead, to access the new editor state, you can use the `useEditorState` hook.
  - `useEditorState` this new hook allows you to select from the editor instance any state you need to render your UI. This is useful when you want to optimize performance by only re-rendering the parts of your UI that need to be updated.

  Here is a usage example:

  ```jsx
  const editor = useEditor({
    /**
     * This option gives us the control to enable the default behavior of rendering the editor immediately.
     */
    immediatelyRender: true,
    /**
     * This option gives us the control to disable the default behavior of re-rendering the editor on every transaction.
     */
    shouldRerenderOnTransaction: false,
    extensions: [StarterKit],
    content: `
      <p>
        A highly optimized editor that only re-renders when it’s necessary.
      </p>
      `,
  })

  /**
   * This hook allows us to select the editor state we want to use in our component.
   */
  const currentEditorState = useEditorState({
    /**
     * The editor instance we want to use.
     */
    editor,
    /**
     * This selector allows us to select the data we want to use in our component.
     * It is evaluated on every editor transaction and compared to it's previously returned value.
     * You can return any data shape you want.
     */
    selector: ctx => ({
      isBold: ctx.editor.isActive('bold'),
      isItalic: ctx.editor.isActive('italic'),
      isStrike: ctx.editor.isActive('strike'),
    }),
    /**
     * This function allows us to customize the equality check for the selector.
     * By default it is a `===` check.
     */
    equalityFn: (prev, next) => {
      // A deep-equal function would probably be more maintainable here, but, we use a shallow one to show that it can be customized.
      if (!next) {
        return false
      }
      return prev.isBold === next.isBold && prev.isItalic === next.isItalic && prev.isStrike === next.isStrike
    },
  })
  ```

- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
- Updated dependencies [fb45149]
  - @tiptap/core@2.5.0
  - @tiptap/extension-bubble-menu@2.5.0
  - @tiptap/extension-floating-menu@2.5.0
  - @tiptap/pm@2.5.0

## 2.5.0-pre.16

### Patch Changes

- 1110280: Fixes strict mode accidentally destroying the editor instance
  - @tiptap/core@2.5.0-pre.16
  - @tiptap/extension-bubble-menu@2.5.0-pre.16
  - @tiptap/extension-floating-menu@2.5.0-pre.16
  - @tiptap/pm@2.5.0-pre.16

## 2.5.0-pre.15

### Patch Changes

- 3a67a5b: Fix the typings
  - @tiptap/core@2.5.0-pre.15
  - @tiptap/extension-bubble-menu@2.5.0-pre.15
  - @tiptap/extension-floating-menu@2.5.0-pre.15
  - @tiptap/pm@2.5.0-pre.15

## 2.5.0-pre.14

### Patch Changes

- df5609c: We've heard a number of complaints around the performance of our React integration, and we finally have a solution that we believe will satisfy everyone. We've made a number of optimizations to how the editor is rendered, as well give you more control over the rendering process.

  Here is a summary of the changes and how you can take advantage of them:

  - SSR rendering was holding back our ability to have an editor instance on first render of `useEditor`. We've now made the default behavior to render the editor immediately on the client. This behavior can be controlled with the new `immediatelyRender` option which when set to `false` will defer rendering until the second render (via a useEffect), this should only be used when server-side rendering.
  - The default behavior of the useEditor hook is to re-render the editor on every editor transaction. Now with the `shouldRerenderOnTransaction` option, you can disable this behavior to optimize performance. Instead, to access the new editor state, you can use the `useEditorState` hook.
  - `useEditorState` this new hook allows you to select from the editor instance any state you need to render your UI. This is useful when you want to optimize performance by only re-rendering the parts of your UI that need to be updated.

  Here is a usage example:

  ```jsx
  const editor = useEditor({
    /**
     * This option gives us the control to enable the default behavior of rendering the editor immediately.
     */
    immediatelyRender: true,
    /**
     * This option gives us the control to disable the default behavior of re-rendering the editor on every transaction.
     */
    shouldRerenderOnTransaction: false,
    extensions: [StarterKit],
    content: `
      <p>
        A highly optimized editor that only re-renders when it’s necessary.
      </p>
      `,
  })

  /**
   * This hook allows us to select the editor state we want to use in our component.
   */
  const currentEditorState = useEditorState({
    /**
     * The editor instance we want to use.
     */
    editor,
    /**
     * This selector allows us to select the data we want to use in our component.
     * It is evaluated on every editor transaction and compared to it's previously returned value.
     * You can return any data shape you want.
     */
    selector: ctx => ({
      isBold: ctx.editor.isActive('bold'),
      isItalic: ctx.editor.isActive('italic'),
      isStrike: ctx.editor.isActive('strike'),
    }),
    /**
     * This function allows us to customize the equality check for the selector.
     * By default it is a `===` check.
     */
    equalityFn: (prev, next) => {
      // A deep-equal function would probably be more maintainable here, but, we use a shallow one to show that it can be customized.
      if (!next) {
        return false
      }
      return prev.isBold === next.isBold && prev.isItalic === next.isItalic && prev.isStrike === next.isStrike
    },
  })
  ```

  - @tiptap/core@2.5.0-pre.14
  - @tiptap/extension-bubble-menu@2.5.0-pre.14
  - @tiptap/extension-floating-menu@2.5.0-pre.14
  - @tiptap/pm@2.5.0-pre.14

## 2.5.0-pre.13

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.13
  - @tiptap/extension-bubble-menu@2.5.0-pre.13
  - @tiptap/extension-floating-menu@2.5.0-pre.13
  - @tiptap/pm@2.5.0-pre.13

## 2.5.0-pre.12

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.12
  - @tiptap/extension-bubble-menu@2.5.0-pre.12
  - @tiptap/extension-floating-menu@2.5.0-pre.12
  - @tiptap/pm@2.5.0-pre.12

## 2.5.0-pre.11

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.11
  - @tiptap/extension-bubble-menu@2.5.0-pre.11
  - @tiptap/extension-floating-menu@2.5.0-pre.11
  - @tiptap/pm@2.5.0-pre.11

## 2.5.0-pre.10

### Patch Changes

- Updated dependencies [74a37ff]
  - @tiptap/core@2.5.0-pre.10
  - @tiptap/extension-bubble-menu@2.5.0-pre.10
  - @tiptap/extension-floating-menu@2.5.0-pre.10
  - @tiptap/pm@2.5.0-pre.10

## 2.5.0-pre.9

### Patch Changes

- Updated dependencies [14a00f4]
  - @tiptap/core@2.5.0-pre.9
  - @tiptap/extension-bubble-menu@2.5.0-pre.9
  - @tiptap/extension-floating-menu@2.5.0-pre.9
  - @tiptap/pm@2.5.0-pre.9

## 2.5.0-pre.8

### Patch Changes

- Updated dependencies [509676e]
  - @tiptap/core@2.5.0-pre.8
  - @tiptap/extension-bubble-menu@2.5.0-pre.8
  - @tiptap/extension-floating-menu@2.5.0-pre.8
  - @tiptap/pm@2.5.0-pre.8

## 2.5.0-pre.7

### Patch Changes

- @tiptap/core@2.5.0-pre.7
- @tiptap/extension-bubble-menu@2.5.0-pre.7
- @tiptap/extension-floating-menu@2.5.0-pre.7
- @tiptap/pm@2.5.0-pre.7

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.

# [2.4.0](https://github.com/ueberdosis/tiptap/compare/v2.3.2...v2.4.0) (2024-05-14)

### Bug Fixes

- fix ts error for BubbleMenu and FloatingMenu in @tiptap/react ([#5126](https://github.com/ueberdosis/tiptap/issues/5126)) ([baff4af](https://github.com/ueberdosis/tiptap/commit/baff4af39e2b8970d7cab99859ece41228643f9d))

### Features

- added jsdocs ([#4356](https://github.com/ueberdosis/tiptap/issues/4356)) ([b941eea](https://github.com/ueberdosis/tiptap/commit/b941eea6daba09d48a5d18ccc1b9a1d84b2249dd))

## [2.3.2](https://github.com/ueberdosis/tiptap/compare/v2.3.1...v2.3.2) (2024-05-08)

**Note:** Version bump only for package @tiptap/react

## [2.3.1](https://github.com/ueberdosis/tiptap/compare/v2.3.0...v2.3.1) (2024-04-30)

**Note:** Version bump only for package @tiptap/react

# [2.3.0](https://github.com/ueberdosis/tiptap/compare/v2.2.6...v2.3.0) (2024-04-09)

**Note:** Version bump only for package @tiptap/react

## [2.2.6](https://github.com/ueberdosis/tiptap/compare/v2.2.5...v2.2.6) (2024-04-06)

**Note:** Version bump only for package @tiptap/react

## [2.2.5](https://github.com/ueberdosis/tiptap/compare/v2.2.4...v2.2.5) (2024-04-05)

**Note:** Version bump only for package @tiptap/react

## [2.2.4](https://github.com/ueberdosis/tiptap/compare/v2.2.3...v2.2.4) (2024-02-23)

**Note:** Version bump only for package @tiptap/react

## [2.2.3](https://github.com/ueberdosis/tiptap/compare/v2.2.2...v2.2.3) (2024-02-15)

**Note:** Version bump only for package @tiptap/react

## [2.2.2](https://github.com/ueberdosis/tiptap/compare/v2.2.1...v2.2.2) (2024-02-07)

### Bug Fixes

- **react:** use ref instead of state in useEditor to prevent rerenders ([#4856](https://github.com/ueberdosis/tiptap/issues/4856)) ([56a5737](https://github.com/ueberdosis/tiptap/commit/56a5737ed102ee75ec72f9cc2847e3c977f431bd))

## [2.2.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0...v2.2.1) (2024-01-31)

**Note:** Version bump only for package @tiptap/react

# [2.2.0](https://github.com/ueberdosis/tiptap/compare/v2.1.16...v2.2.0) (2024-01-29)

# [2.2.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.2.0-rc.8) (2024-01-08)

# [2.2.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.6...v2.2.0-rc.7) (2023-11-27)

# [2.2.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.5...v2.2.0-rc.6) (2023-11-23)

### Reverts

- Revert "fix/react-renderer-node-attrs (#4321)" ([a4af83c](https://github.com/ueberdosis/tiptap/commit/a4af83ca52c8e020f88990af53981591559205a9)), closes [#4321](https://github.com/ueberdosis/tiptap/issues/4321)

# [2.2.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.2.0-rc.4) (2023-10-10)

# [2.2.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.2...v2.2.0-rc.3) (2023-08-18)

# [2.2.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.0...v2.2.0-rc.1) (2023-08-18)

# [2.2.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.2.0-rc.0) (2023-08-18)

## [2.1.16](https://github.com/ueberdosis/tiptap/compare/v2.1.15...v2.1.16) (2024-01-10)

**Note:** Version bump only for package @tiptap/react

## [2.1.15](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.1.15) (2024-01-08)

**Note:** Version bump only for package @tiptap/react

## [2.1.14](https://github.com/ueberdosis/tiptap/compare/v2.1.13...v2.1.14) (2024-01-08)

**Note:** Version bump only for package @tiptap/react

## [2.1.13](https://github.com/ueberdosis/tiptap/compare/v2.1.12...v2.1.13) (2023-11-30)

### Bug Fixes

- **react:** fix performance regression because of select/deselect ([#4661](https://github.com/ueberdosis/tiptap/issues/4661)) ([ad7f659](https://github.com/ueberdosis/tiptap/commit/ad7f659ed08a6a7c57056b78edbded014549f2dc))

## [2.1.12](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.1.12) (2023-10-11)

**Note:** Version bump only for package @tiptap/react

## [2.1.11](https://github.com/ueberdosis/tiptap/compare/v2.1.10...v2.1.11) (2023-09-20)

### Reverts

- Revert "v2.2.11" ([6aa755a](https://github.com/ueberdosis/tiptap/commit/6aa755a04b9955fc175c7ab33dee527d0d5deef0))

## [2.1.10](https://github.com/ueberdosis/tiptap/compare/v2.1.9...v2.1.10) (2023-09-15)

**Note:** Version bump only for package @tiptap/react

## [2.1.9](https://github.com/ueberdosis/tiptap/compare/v2.1.8...v2.1.9) (2023-09-14)

**Note:** Version bump only for package @tiptap/react

## [2.1.8](https://github.com/ueberdosis/tiptap/compare/v2.1.7...v2.1.8) (2023-09-04)

**Note:** Version bump only for package @tiptap/react

## [2.1.7](https://github.com/ueberdosis/tiptap/compare/v2.1.6...v2.1.7) (2023-09-04)

**Note:** Version bump only for package @tiptap/react

## [2.1.6](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.1.6) (2023-08-18)

**Note:** Version bump only for package @tiptap/react

## [2.1.5](https://github.com/ueberdosis/tiptap/compare/v2.1.4...v2.1.5) (2023-08-18)

**Note:** Version bump only for package @tiptap/react

## [2.1.4](https://github.com/ueberdosis/tiptap/compare/v2.1.3...v2.1.4) (2023-08-18)

**Note:** Version bump only for package @tiptap/react

## [2.1.3](https://github.com/ueberdosis/tiptap/compare/v2.1.2...v2.1.3) (2023-08-18)

**Note:** Version bump only for package @tiptap/react

## [2.1.2](https://github.com/ueberdosis/tiptap/compare/v2.1.1...v2.1.2) (2023-08-17)

**Note:** Version bump only for package @tiptap/react

## [2.1.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0...v2.1.1) (2023-08-16)

**Note:** Version bump only for package @tiptap/react

# [2.1.0](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.14...v2.1.0) (2023-08-16)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.14](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.13...v2.1.0-rc.14) (2023-08-11)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.13](https://github.com/ueberdosis/tiptap/compare/v2.0.4...v2.1.0-rc.13) (2023-08-11)

# [2.1.0-rc.12](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.11...v2.1.0-rc.12) (2023-07-14)

# [2.1.0-rc.11](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.10...v2.1.0-rc.11) (2023-07-07)

# [2.1.0-rc.10](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.9...v2.1.0-rc.10) (2023-07-07)

### Bug Fixes

- **react:** update select state when text selection is around node ([#4148](https://github.com/ueberdosis/tiptap/issues/4148)) ([5bd5bd4](https://github.com/ueberdosis/tiptap/commit/5bd5bd4ecdbe1f952b23d5f5efad16b6ed5cc44f))

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

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.11](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.10...v2.1.0-rc.11) (2023-07-07)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.10](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.9...v2.1.0-rc.10) (2023-07-07)

### Bug Fixes

- **react:** update select state when text selection is around node ([#4148](https://github.com/ueberdosis/tiptap/issues/4148)) ([5bd5bd4](https://github.com/ueberdosis/tiptap/commit/5bd5bd4ecdbe1f952b23d5f5efad16b6ed5cc44f))

# [2.1.0-rc.9](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.8...v2.1.0-rc.9) (2023-06-15)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.7...v2.1.0-rc.8) (2023-05-25)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.6...v2.1.0-rc.7) (2023-05-25)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.5...v2.1.0-rc.6) (2023-05-25)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.5](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.4...v2.1.0-rc.5) (2023-05-25)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.3...v2.1.0-rc.4) (2023-04-27)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.2...v2.1.0-rc.3) (2023-04-26)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.2](https://github.com/ueberdosis/tiptap/compare/v2.0.3...v2.1.0-rc.2) (2023-04-26)

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0c1bba3](https://github.com/ueberdosis/tiptap/commit/0c1bba3137b535776bcef95ff3c55e13f5a2db46))

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

**Note:** Version bump only for package @tiptap/react

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

**Note:** Version bump only for package @tiptap/react

## [2.0.3](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.0.3) (2023-04-13)

**Note:** Version bump only for package @tiptap/react

## [2.0.2](https://github.com/ueberdosis/tiptap/compare/v2.0.1...v2.0.2) (2023-04-03)

### Bug Fixes

- **react:** fix rebinding events not overwriting editor.on ([#3935](https://github.com/ueberdosis/tiptap/issues/3935)) ([64ab357](https://github.com/ueberdosis/tiptap/commit/64ab3570c1e86a65f5022793acb0292d8972dcd7))

## [2.0.1](https://github.com/ueberdosis/tiptap/compare/v2.0.0...v2.0.1) (2023-03-30)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0534f76](https://github.com/ueberdosis/tiptap/commit/0534f76401bf5399c01ca7f39d87f7221d91b4f7))

# [2.0.0-beta.220](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.219...v2.0.0-beta.220) (2023-02-28)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.219](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.218...v2.0.0-beta.219) (2023-02-27)

### Bug Fixes

- [#3773](https://github.com/ueberdosis/tiptap/issues/3773) - Array for content breaks editor ([#3786](https://github.com/ueberdosis/tiptap/issues/3786)) ([89cc59a](https://github.com/ueberdosis/tiptap/commit/89cc59a8372467feee7c70948d4395b95b13ed55))
- **react:** reset initialized when editorcontent is unmounting ([#3781](https://github.com/ueberdosis/tiptap/issues/3781)) ([38b7e41](https://github.com/ueberdosis/tiptap/commit/38b7e412bbcc1e36031bc6ec5b73bc46b1c9edea))
- update typings for node view decorations ([#3783](https://github.com/ueberdosis/tiptap/issues/3783)) ([f869507](https://github.com/ueberdosis/tiptap/commit/f8695073968c5c6865ad8faf05351020abb2a3cc))

# [2.0.0-beta.218](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.217...v2.0.0-beta.218) (2023-02-18)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.217](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.216...v2.0.0-beta.217) (2023-02-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.216](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.215...v2.0.0-beta.216) (2023-02-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.215](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.214...v2.0.0-beta.215) (2023-02-08)

### Bug Fixes

- fix builds including prosemirror ([a380ec4](https://github.com/ueberdosis/tiptap/commit/a380ec41d198ebacc80cea9e79b0a8aa3092618a))

# [2.0.0-beta.214](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.213...v2.0.0-beta.214) (2023-02-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.213](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.212...v2.0.0-beta.213) (2023-02-07)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.212](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.211...v2.0.0-beta.212) (2023-02-03)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.211](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.210...v2.0.0-beta.211) (2023-02-02)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.210](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.209...v2.0.0-beta.210) (2023-02-02)

### Features

- **pm:** new prosemirror package for dependency resolving ([f387ad3](https://github.com/ueberdosis/tiptap/commit/f387ad3dd4c2b30eaea33fb0ba0b42e0cd39263b))

# [2.0.0-beta.209](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.208...v2.0.0-beta.209) (2022-12-16)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.208](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.207...v2.0.0-beta.208) (2022-12-16)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.207](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.206...v2.0.0-beta.207) (2022-12-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.206](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.205...v2.0.0-beta.206) (2022-12-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.205](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.204...v2.0.0-beta.205) (2022-12-05)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.204](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.203...v2.0.0-beta.204) (2022-11-25)

### Bug Fixes

- **core:** rename esm modules to esm.js ([c1a0c3a](https://github.com/ueberdosis/tiptap/commit/c1a0c3ae43baac9dd5ed90903d3a0d4eaeea7702))

# [2.0.0-beta.203](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.202...v2.0.0-beta.203) (2022-11-24)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.202](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.201...v2.0.0-beta.202) (2022-11-04)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.201](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.200...v2.0.0-beta.201) (2022-11-04)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.200](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.199...v2.0.0-beta.200) (2022-11-04)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.199](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.198...v2.0.0-beta.199) (2022-09-30)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.198](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.197...v2.0.0-beta.198) (2022-09-29)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.197](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.196...v2.0.0-beta.197) (2022-09-26)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.196](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.195...v2.0.0-beta.196) (2022-09-20)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.195](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.194...v2.0.0-beta.195) (2022-09-14)

### Bug Fixes

- move React `flushSync` to microtask ([#3188](https://github.com/ueberdosis/tiptap/issues/3188)) ([9093cdf](https://github.com/ueberdosis/tiptap/commit/9093cdfcf52cbc5297b9b678073636103dfecb3f)), closes [#2985](https://github.com/ueberdosis/tiptap/issues/2985)

# [2.0.0-beta.194](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.193...v2.0.0-beta.194) (2022-09-11)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.115](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.114...@tiptap/react@2.0.0-beta.115) (2022-09-03)

### Bug Fixes

- fix React Node View render problem in React 18 ([#2985](https://github.com/ueberdosis/tiptap/issues/2985)) ([f32293b](https://github.com/ueberdosis/tiptap/commit/f32293b0d5d36ffb546a3d1e3dfab1580ee5080a))

# [2.0.0-beta.114](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.113...@tiptap/react@2.0.0-beta.114) (2022-06-27)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.113](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.112...@tiptap/react@2.0.0-beta.113) (2022-06-20)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.112](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.110...@tiptap/react@2.0.0-beta.112) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.110](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.110...@tiptap/react@2.0.0-beta.110) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.109](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.108...@tiptap/react@2.0.0-beta.109) (2022-04-27)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.108](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.107...@tiptap/react@2.0.0-beta.108) (2022-02-07)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.107](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.106...@tiptap/react@2.0.0-beta.107) (2022-01-25)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.106](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.105...@tiptap/react@2.0.0-beta.106) (2022-01-20)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.105](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.104...@tiptap/react@2.0.0-beta.105) (2022-01-11)

### Bug Fixes

- Mark `@tiptap/react` and `@tiptap/core` as side effect free ([#2361](https://github.com/ueberdosis/tiptap/issues/2361)) ([e609b2d](https://github.com/ueberdosis/tiptap/commit/e609b2d11615dd85fd219731d1b73deaeccccd69))

# [2.0.0-beta.104](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.103...@tiptap/react@2.0.0-beta.104) (2022-01-04)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.103](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.102...@tiptap/react@2.0.0-beta.103) (2022-01-03)

### Bug Fixes

- change reactrenderer component type definition ([#2327](https://github.com/ueberdosis/tiptap/issues/2327)) ([64dfae8](https://github.com/ueberdosis/tiptap/commit/64dfae85118d2b9dc525a8bfa31f00688a56f049))

# [2.0.0-beta.102](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.101...@tiptap/react@2.0.0-beta.102) (2021-12-22)

### Bug Fixes

- Remove `element.current` from `useEffect` in `BubbleMenu` and `FloatingMenu` ([#2297](https://github.com/ueberdosis/tiptap/issues/2297)) ([561941d](https://github.com/ueberdosis/tiptap/commit/561941d5e0d8c0bed852156e06820780e65f0656))

# [2.0.0-beta.101](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.100...@tiptap/react@2.0.0-beta.101) (2021-12-17)

### Reverts

- Revert "fix: Make sure editor is available on first render (#2282), fix #2040, fix #2182" ([629f4d2](https://github.com/ueberdosis/tiptap/commit/629f4d2a76c62e82c104598bf42a53a6d32015a8)), closes [#2040](https://github.com/ueberdosis/tiptap/issues/2040) [#2182](https://github.com/ueberdosis/tiptap/issues/2182)

# [2.0.0-beta.100](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.99...@tiptap/react@2.0.0-beta.100) (2021-12-16)

### Bug Fixes

- Make sure editor is available on first render ([#2282](https://github.com/ueberdosis/tiptap/issues/2282)), fix [#2040](https://github.com/ueberdosis/tiptap/issues/2040), fix [#2182](https://github.com/ueberdosis/tiptap/issues/2182) ([2436e2c](https://github.com/ueberdosis/tiptap/commit/2436e2c8fe88cdce6685ae3d712e5f2d3e70851d))

# [2.0.0-beta.99](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.98...@tiptap/react@2.0.0-beta.99) (2021-12-15)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.98](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.97...@tiptap/react@2.0.0-beta.98) (2021-12-03)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.97](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.96...@tiptap/react@2.0.0-beta.97) (2021-12-02)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.96](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.95...@tiptap/react@2.0.0-beta.96) (2021-12-02)

### Features

- Add `as` option and pass through to ReactRenderer ([#2213](https://github.com/ueberdosis/tiptap/issues/2213)) ([dedcf17](https://github.com/ueberdosis/tiptap/commit/dedcf17d533aab0c5641b842877e42440883d5d8))

# [2.0.0-beta.95](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.94...@tiptap/react@2.0.0-beta.95) (2021-11-18)

### Features

- add className option to ReactRenderer, see [#2166](https://github.com/ueberdosis/tiptap/issues/2166) ([c9dc1e1](https://github.com/ueberdosis/tiptap/commit/c9dc1e1ec3295fe3dce7ed7d314c5a7e4140af83))

# [2.0.0-beta.94](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.93...@tiptap/react@2.0.0-beta.94) (2021-11-17)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.93](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.92...@tiptap/react@2.0.0-beta.93) (2021-11-10)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.92](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.91...@tiptap/react@2.0.0-beta.92) (2021-11-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.91](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.90...@tiptap/react@2.0.0-beta.91) (2021-11-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.90](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.89...@tiptap/react@2.0.0-beta.90) (2021-11-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.89](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.88...@tiptap/react@2.0.0-beta.89) (2021-11-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.88](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.87...@tiptap/react@2.0.0-beta.88) (2021-11-05)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.87](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.86...@tiptap/react@2.0.0-beta.87) (2021-10-31)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.86](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.85...@tiptap/react@2.0.0-beta.86) (2021-10-26)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.85](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.84...@tiptap/react@2.0.0-beta.85) (2021-10-25)

### Bug Fixes

- Check node type above custom update function for node views ([#2081](https://github.com/ueberdosis/tiptap/issues/2081)) ([ddc9ca8](https://github.com/ueberdosis/tiptap/commit/ddc9ca8d4f347566f83513a386922afe52f26da1))

# [2.0.0-beta.84](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.83...@tiptap/react@2.0.0-beta.84) (2021-10-22)

### Features

- Add extension storage ([#2069](https://github.com/ueberdosis/tiptap/issues/2069)) ([7ffabf2](https://github.com/ueberdosis/tiptap/commit/7ffabf251c408a652eec1931cc78a8bd43cccb67))

# [2.0.0-beta.83](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.82...@tiptap/react@2.0.0-beta.83) (2021-10-14)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.82](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.81...@tiptap/react@2.0.0-beta.82) (2021-10-14)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.81](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.80...@tiptap/react@2.0.0-beta.81) (2021-10-12)

### Bug Fixes

- Add `editor` dependency when registering `BubbleMenuPlugin` and `FloatingMenuPlugin` ([#2018](https://github.com/ueberdosis/tiptap/issues/2018)) ([e9465ec](https://github.com/ueberdosis/tiptap/commit/e9465ec0f6921abd428ed27b50596d20edc05b77))

# [2.0.0-beta.80](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.79...@tiptap/react@2.0.0-beta.80) (2021-10-11)

### Bug Fixes

- fix editor type for ReactRenderer ([2af1870](https://github.com/ueberdosis/tiptap/commit/2af187023ddbc85edee086cdb898c5139f7668de))
- Improve ReactRenderer types ([#2011](https://github.com/ueberdosis/tiptap/issues/2011)) ([31d8ab3](https://github.com/ueberdosis/tiptap/commit/31d8ab3593f18f8fec49b7e5ab22a7d979165ae6))

# [2.0.0-beta.79](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.78...@tiptap/react@2.0.0-beta.79) (2021-10-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.78](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.77...@tiptap/react@2.0.0-beta.78) (2021-10-02)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.77](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.76...@tiptap/react@2.0.0-beta.77) (2021-09-30)

### Bug Fixes

- use ref to move contentDOM ([#1960](https://github.com/ueberdosis/tiptap/issues/1960)), fix [#1942](https://github.com/ueberdosis/tiptap/issues/1942) ([dead826](https://github.com/ueberdosis/tiptap/commit/dead82625095031bc4d32b47b205044bf75769bd))

# [2.0.0-beta.76](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.75...@tiptap/react@2.0.0-beta.76) (2021-09-30)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.75](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.74...@tiptap/react@2.0.0-beta.75) (2021-09-29)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.74](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.73...@tiptap/react@2.0.0-beta.74) (2021-09-28)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.73](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.72...@tiptap/react@2.0.0-beta.73) (2021-09-27)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.72](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.71...@tiptap/react@2.0.0-beta.72) (2021-09-23)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.71](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.70...@tiptap/react@2.0.0-beta.71) (2021-09-22)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.70](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.69...@tiptap/react@2.0.0-beta.70) (2021-09-21)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.69](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.68...@tiptap/react@2.0.0-beta.69) (2021-09-20)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.68](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.67...@tiptap/react@2.0.0-beta.68) (2021-09-18)

### Bug Fixes

- set correct component type for ReactRenderer, fix [#1904](https://github.com/ueberdosis/tiptap/issues/1904) ([fe47c38](https://github.com/ueberdosis/tiptap/commit/fe47c388ce5ef49c286302a7b771a680c2f0c239))

# [2.0.0-beta.67](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.66...@tiptap/react@2.0.0-beta.67) (2021-09-15)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.66](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.65...@tiptap/react@2.0.0-beta.66) (2021-09-07)

### Features

- add support for forwardRef component in reactRenderer ([#1690](https://github.com/ueberdosis/tiptap/issues/1690), fix [#1040](https://github.com/ueberdosis/tiptap/issues/1040)) ([d1f2ad2](https://github.com/ueberdosis/tiptap/commit/d1f2ad293f9df4004ee3fea5550a3921a03162f5))

# [2.0.0-beta.65](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.64...@tiptap/react@2.0.0-beta.65) (2021-09-07)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.64](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.63...@tiptap/react@2.0.0-beta.64) (2021-09-06)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.63](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.62...@tiptap/react@2.0.0-beta.63) (2021-08-24)

### Bug Fixes

- fix a bug when using nested node views in react, fix [#1747](https://github.com/ueberdosis/tiptap/issues/1747) ([b15a8a8](https://github.com/ueberdosis/tiptap/commit/b15a8a8683bafbc9fd57dc64d60329f9ab08ecfd))

# [2.0.0-beta.62](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.61...@tiptap/react@2.0.0-beta.62) (2021-08-23)

### Bug Fixes

- make shouldShow and pluginKey option for menus, fix [#1779](https://github.com/ueberdosis/tiptap/issues/1779) ([70a328b](https://github.com/ueberdosis/tiptap/commit/70a328bd3dea174170ad8e92db4c4f7f9368fd1b))

# [2.0.0-beta.61](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.60...@tiptap/react@2.0.0-beta.61) (2021-08-20)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.60](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.59...@tiptap/react@2.0.0-beta.60) (2021-08-13)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.59](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.58...@tiptap/react@2.0.0-beta.59) (2021-08-13)

### Bug Fixes

- rename key to pluginKey for menus ([89d26f7](https://github.com/ueberdosis/tiptap/commit/89d26f7cba2a115aa342f0ee621f0b65c840dfb8))

# [2.0.0-beta.58](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.57...@tiptap/react@2.0.0-beta.58) (2021-08-12)

### Bug Fixes

- fix some react focus issues ([#1724](https://github.com/ueberdosis/tiptap/issues/1724)), fix [#1716](https://github.com/ueberdosis/tiptap/issues/1716), fix [#1608](https://github.com/ueberdosis/tiptap/issues/1608), fix [#1520](https://github.com/ueberdosis/tiptap/issues/1520) ([956566e](https://github.com/ueberdosis/tiptap/commit/956566eaad0a522d6bc27d44594aa36d6c33f8b3))

# [2.0.0-beta.57](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.56...@tiptap/react@2.0.0-beta.57) (2021-08-11)

### Features

- add key option and shouldShow option to menus (fix [#1480](https://github.com/ueberdosis/tiptap/issues/1480), fix [#1043](https://github.com/ueberdosis/tiptap/issues/1043), fix [#1268](https://github.com/ueberdosis/tiptap/issues/1268), fix [#1503](https://github.com/ueberdosis/tiptap/issues/1503)) ([9ba61c1](https://github.com/ueberdosis/tiptap/commit/9ba61c1582cee838f2214d00285773ace2fb229e))

# [2.0.0-beta.56](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.55...@tiptap/react@2.0.0-beta.56) (2021-08-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.55](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.54...@tiptap/react@2.0.0-beta.55) (2021-07-28)

### Bug Fixes

- fix updating node views, fix [#1656](https://github.com/ueberdosis/tiptap/issues/1656) ([d7f6e0c](https://github.com/ueberdosis/tiptap/commit/d7f6e0ce3f99381d3822cde5ab1c484ed13a4c20))

# [2.0.0-beta.54](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.53...@tiptap/react@2.0.0-beta.54) (2021-07-27)

### Features

- add ignoreMutation option to NodeViewRenderer, fix [#1538](https://github.com/ueberdosis/tiptap/issues/1538) ([651e691](https://github.com/ueberdosis/tiptap/commit/651e6911e3ea5407df6a48783ee16733e0a4f474))

# [2.0.0-beta.53](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.52...@tiptap/react@2.0.0-beta.53) (2021-07-26)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.52](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.51...@tiptap/react@2.0.0-beta.52) (2021-06-24)

### Bug Fixes

- check for destroyed editor before creating node views in react ([44e4722](https://github.com/ueberdosis/tiptap/commit/44e47222a03be60835d5058d01bc510e4cf31d60))

# [2.0.0-beta.51](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.50...@tiptap/react@2.0.0-beta.51) (2021-06-23)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.50](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.49...@tiptap/react@2.0.0-beta.50) (2021-06-15)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.49](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.48...@tiptap/react@2.0.0-beta.49) (2021-06-15)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.48](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.47...@tiptap/react@2.0.0-beta.48) (2021-06-14)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.47](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.46...@tiptap/react@2.0.0-beta.47) (2021-06-14)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.46](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.45...@tiptap/react@2.0.0-beta.46) (2021-06-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.45](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.44...@tiptap/react@2.0.0-beta.45) (2021-05-29)

### Bug Fixes

- maybe move content dom on update, fix [#1370](https://github.com/ueberdosis/tiptap/issues/1370) ([78f75c3](https://github.com/ueberdosis/tiptap/commit/78f75c3e0e287abac18bf87f32a1bd586300da14))

# [2.0.0-beta.44](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.43...@tiptap/react@2.0.0-beta.44) (2021-05-28)

### Bug Fixes

- maybe move content dom on update, see [#1370](https://github.com/ueberdosis/tiptap/issues/1370) ([60708a7](https://github.com/ueberdosis/tiptap/commit/60708a781770d745f0d9135c225f56d3d2f1b31d))

# [2.0.0-beta.43](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.42...@tiptap/react@2.0.0-beta.43) (2021-05-27)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.42](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.41...@tiptap/react@2.0.0-beta.42) (2021-05-24)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.41](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.40...@tiptap/react@2.0.0-beta.41) (2021-05-18)

### Bug Fixes

- move all child nodes within EditorContent ([0f299d2](https://github.com/ueberdosis/tiptap/commit/0f299d228eb4075d24e1c0fb5b39febc6bc77de6))

### Features

- add deleteNode method to node views ([fcee5f8](https://github.com/ueberdosis/tiptap/commit/fcee5f82c6a282191afe5c2cb83b9f5820af28dd))

# [2.0.0-beta.40](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.39...@tiptap/react@2.0.0-beta.40) (2021-05-18)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.39](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.38...@tiptap/react@2.0.0-beta.39) (2021-05-18)

### Bug Fixes

- add prop support for EditorContent, fix [#1332](https://github.com/ueberdosis/tiptap/issues/1332) ([8979143](https://github.com/ueberdosis/tiptap/commit/8979143c37679af21e71b37b72ac91bea989746c))

# [2.0.0-beta.38](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.37...@tiptap/react@2.0.0-beta.38) (2021-05-17)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.37](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.35...@tiptap/react@2.0.0-beta.37) (2021-05-13)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.35](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.34...@tiptap/react@2.0.0-beta.35) (2021-05-13)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.35](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.34...@tiptap/react@2.0.0-beta.35) (2021-05-13)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.34](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.33...@tiptap/react@2.0.0-beta.34) (2021-05-13)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.33](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.32...@tiptap/react@2.0.0-beta.33) (2021-05-07)

### Bug Fixes

- revert adding exports ([bc320d0](https://github.com/ueberdosis/tiptap/commit/bc320d0b4b80b0e37a7e47a56e0f6daec6e65d98))

# [2.0.0-beta.32](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.31...@tiptap/react@2.0.0-beta.32) (2021-05-06)

### Bug Fixes

- revert adding type: module ([f8d6475](https://github.com/ueberdosis/tiptap/commit/f8d6475e2151faea6f96baecdd6bd75880d50d2c))

# [2.0.0-beta.31](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.30...@tiptap/react@2.0.0-beta.31) (2021-05-06)

### Bug Fixes

- add exports to package.json ([1277fa4](https://github.com/ueberdosis/tiptap/commit/1277fa47151e9c039508cdb219bdd0ffe647f4ee))

# [2.0.0-beta.30](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.29...@tiptap/react@2.0.0-beta.30) (2021-05-06)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.29](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.28...@tiptap/react@2.0.0-beta.29) (2021-05-05)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.28](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.27...@tiptap/react@2.0.0-beta.28) (2021-05-05)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.27](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.26...@tiptap/react@2.0.0-beta.27) (2021-05-04)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.26](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.25...@tiptap/react@2.0.0-beta.26) (2021-04-27)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.25](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.24...@tiptap/react@2.0.0-beta.25) (2021-04-23)

### Bug Fixes

- allow passing props to NodeViewWrapper and NodeViewContent ([cfb3b80](https://github.com/ueberdosis/tiptap/commit/cfb3b80f63a5d38ea7aa4b69a895afd8b09cb5ab))

# [2.0.0-beta.24](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.23...@tiptap/react@2.0.0-beta.24) (2021-04-23)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.23](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.22...@tiptap/react@2.0.0-beta.23) (2021-04-22)

### Bug Fixes

- prevents a bug where a line break was incorrectly added at enter in react node views, fix [#1197](https://github.com/ueberdosis/tiptap/issues/1197) ([e885ffa](https://github.com/ueberdosis/tiptap/commit/e885ffa15b590b0c1f895f5c32f4852cc483c222))

# [2.0.0-beta.22](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.21...@tiptap/react@2.0.0-beta.22) (2021-04-21)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.21](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.20...@tiptap/react@2.0.0-beta.21) (2021-04-16)

### Features

- add tippyOptions prop ([9a56f66](https://github.com/ueberdosis/tiptap/commit/9a56f666a118ca7c59a6f1f67f40e6490e20d3b8))
- remove keepInBounds ([d7282f1](https://github.com/ueberdosis/tiptap/commit/d7282f168bc6cfae4e1630d14bb8462bc135b254))

# [2.0.0-beta.20](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.19...@tiptap/react@2.0.0-beta.20) (2021-04-15)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.19](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.18...@tiptap/react@2.0.0-beta.19) (2021-04-11)

### Bug Fixes

- fix using react node views with insertContent ([ea0992f](https://github.com/ueberdosis/tiptap/commit/ea0992f66e9942c590e75c0ab2f5705640764f4d))

# [2.0.0-beta.18](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.17...@tiptap/react@2.0.0-beta.18) (2021-04-08)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.17](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.16...@tiptap/react@2.0.0-beta.17) (2021-04-08)

### Bug Fixes

- improve node view error message ([536663f](https://github.com/ueberdosis/tiptap/commit/536663f816039df6e3d8de23989f343d78e5d08e))
- make `as` prop optional ([f8dec5f](https://github.com/ueberdosis/tiptap/commit/f8dec5f905baf5692dd257b3dddec3de2bcad1a1))

# [2.0.0-beta.16](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.15...@tiptap/react@2.0.0-beta.16) (2021-04-07)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.15](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.14...@tiptap/react@2.0.0-beta.15) (2021-04-07)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.14](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.13...@tiptap/react@2.0.0-beta.14) (2021-04-04)

### Features

- render wrapper element for inline node views as span, fix [#242](https://github.com/ueberdosis/tiptap/issues/242) ([bdb5d72](https://github.com/ueberdosis/tiptap/commit/bdb5d724956c0c757e29be38fb2c9dd85d8fd36b))

# [2.0.0-beta.13](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.12...@tiptap/react@2.0.0-beta.13) (2021-04-01)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.12](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.11...@tiptap/react@2.0.0-beta.12) (2021-04-01)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.11](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.10...@tiptap/react@2.0.0-beta.11) (2021-04-01)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.10](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.9...@tiptap/react@2.0.0-beta.10) (2021-04-01)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.9](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.8...@tiptap/react@2.0.0-beta.9) (2021-03-31)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.8](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.7...@tiptap/react@2.0.0-beta.8) (2021-03-31)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.7](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.6...@tiptap/react@2.0.0-beta.7) (2021-03-31)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.6](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.5...@tiptap/react@2.0.0-beta.6) (2021-03-28)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.5](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.4...@tiptap/react@2.0.0-beta.5) (2021-03-24)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.4](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.3...@tiptap/react@2.0.0-beta.4) (2021-03-18)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.3](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.2...@tiptap/react@2.0.0-beta.3) (2021-03-16)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.2](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-beta.1...@tiptap/react@2.0.0-beta.2) (2021-03-09)

**Note:** Version bump only for package @tiptap/react

# [2.0.0-beta.1](https://github.com/ueberdosis/tiptap/compare/@tiptap/react@2.0.0-alpha.2...@tiptap/react@2.0.0-beta.1) (2021-03-05)

**Note:** Version bump only for package @tiptap/react

# 2.0.0-alpha.2 (2021-02-26)

**Note:** Version bump only for package @tiptap/react
