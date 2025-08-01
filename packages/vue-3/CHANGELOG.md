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

### Patch Changes

- 1b4c82b: We are now using pnpm package aliases for versions to enable better version pinning for the monorepository
- 89bd9c7: Enforce type imports so that the bundler ignores TypeScript type imports when generating the index.js file of the dist directory
- 00693b8: Fixed a bug where table cell selections would not position the bubble menu accordingly
- 73d1888: Fixed a bug where the global resize handler of the BubbleMenu plugin would not be unregistered on destroy
- 8c69002: Synced beta with stable features
- 0f14cc5: Added missing `onShow`, `onUpdate`, `onHide` and `onDestroy` options
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

- @tiptap/core@3.0.0-beta.28
- @tiptap/pm@3.0.0-beta.28

## 3.0.0-beta.27

### Patch Changes

- Updated dependencies [412e1bd]
  - @tiptap/core@3.0.0-beta.27
  - @tiptap/pm@3.0.0-beta.27

## 3.0.0-beta.26

### Patch Changes

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

### Patch Changes

- @tiptap/extension-bubble-menu@3.0.0-next.4
- @tiptap/extension-floating-menu@3.0.0-next.4

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

- @tiptap/extension-bubble-menu@2.11.3
- @tiptap/extension-floating-menu@2.11.3

## 2.5.8

### Patch Changes

- f7f644f: Correctly set editor's appContext.provide to forward full inject chain
- Updated dependencies [a08bf85]
  - @tiptap/core@2.5.8
  - @tiptap/extension-bubble-menu@2.5.8
  - @tiptap/extension-floating-menu@2.5.8
  - @tiptap/pm@2.5.8

## 2.5.7

### Patch Changes

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

- ab8389a: VueNodeViewRenderer should return `null` for `contentDOM` for a non-leaf node with no `NodeViewContent`
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

- 85d21ca: Updated demos and reverted vue specific performance enhancements until we know they work

  > in commit ff04353b3ee0e6fc63733a673e2b27d2272a3355 revert: "fix(vue-3): faster component rendering (#5206)"
  > This reverts commit 31f37464912b7b21f3a565ca63222b9f5b6cce00.

  and

  > in commit dbab8e42eac893a0237566fb30c14b4ed0f3674a revert: "fix(vue-3): fix editor.state updating too late during a transaction due to reactiveState fixes #4870 (#5252)"
  > This reverts commit 509676ed4a63b84b904a98c1e34d18449d25c2a7.

  - @tiptap/core@2.5.1
  - @tiptap/extension-bubble-menu@2.5.1
  - @tiptap/extension-floating-menu@2.5.1
  - @tiptap/pm@2.5.1

## 2.5.0

### Patch Changes

- fb45149: Vue 3 bubble menus are properly synchronized with state transitions with the new beforeTransaction hook which is fired before the transaction is applied to the view
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

- @tiptap/core@2.5.0-pre.16
- @tiptap/extension-bubble-menu@2.5.0-pre.16
- @tiptap/extension-floating-menu@2.5.0-pre.16
- @tiptap/pm@2.5.0-pre.16

## 2.5.0-pre.15

### Patch Changes

- @tiptap/core@2.5.0-pre.15
- @tiptap/extension-bubble-menu@2.5.0-pre.15
- @tiptap/extension-floating-menu@2.5.0-pre.15
- @tiptap/pm@2.5.0-pre.15

## 2.5.0-pre.14

### Patch Changes

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

- 509676e: Vue 3 bubble menus are properly synchronized with state transitions with the new beforeTransaction hook which is fired before the transaction is applied to the view
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

### Features

- added jsdocs ([#4356](https://github.com/ueberdosis/tiptap/issues/4356)) ([b941eea](https://github.com/ueberdosis/tiptap/commit/b941eea6daba09d48a5d18ccc1b9a1d84b2249dd))

## [2.3.2](https://github.com/ueberdosis/tiptap/compare/v2.3.1...v2.3.2) (2024-05-08)

**Note:** Version bump only for package @tiptap/vue-3

## [2.3.1](https://github.com/ueberdosis/tiptap/compare/v2.3.0...v2.3.1) (2024-04-30)

**Note:** Version bump only for package @tiptap/vue-3

# [2.3.0](https://github.com/ueberdosis/tiptap/compare/v2.2.6...v2.3.0) (2024-04-09)

**Note:** Version bump only for package @tiptap/vue-3

## [2.2.6](https://github.com/ueberdosis/tiptap/compare/v2.2.5...v2.2.6) (2024-04-06)

**Note:** Version bump only for package @tiptap/vue-3

## [2.2.5](https://github.com/ueberdosis/tiptap/compare/v2.2.4...v2.2.5) (2024-04-05)

**Note:** Version bump only for package @tiptap/vue-3

## [2.2.4](https://github.com/ueberdosis/tiptap/compare/v2.2.3...v2.2.4) (2024-02-23)

**Note:** Version bump only for package @tiptap/vue-3

## [2.2.3](https://github.com/ueberdosis/tiptap/compare/v2.2.2...v2.2.3) (2024-02-15)

**Note:** Version bump only for package @tiptap/vue-3

## [2.2.2](https://github.com/ueberdosis/tiptap/compare/v2.2.1...v2.2.2) (2024-02-07)

**Note:** Version bump only for package @tiptap/vue-3

## [2.2.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0...v2.2.1) (2024-01-31)

**Note:** Version bump only for package @tiptap/vue-3

# [2.2.0](https://github.com/ueberdosis/tiptap/compare/v2.1.16...v2.2.0) (2024-01-29)

# [2.2.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.2.0-rc.8) (2024-01-08)

# [2.2.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.6...v2.2.0-rc.7) (2023-11-27)

# [2.2.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.5...v2.2.0-rc.6) (2023-11-23)

# [2.2.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.2.0-rc.4) (2023-10-10)

# [2.2.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.2...v2.2.0-rc.3) (2023-08-18)

# [2.2.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.2.0-rc.0...v2.2.0-rc.1) (2023-08-18)

# [2.2.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.2.0-rc.0) (2023-08-18)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.16](https://github.com/ueberdosis/tiptap/compare/v2.1.15...v2.1.16) (2024-01-10)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.15](https://github.com/ueberdosis/tiptap/compare/v2.1.14...v2.1.15) (2024-01-08)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.14](https://github.com/ueberdosis/tiptap/compare/v2.1.13...v2.1.14) (2024-01-08)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.13](https://github.com/ueberdosis/tiptap/compare/v2.1.12...v2.1.13) (2023-11-30)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.12](https://github.com/ueberdosis/tiptap/compare/v2.1.11...v2.1.12) (2023-10-11)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.11](https://github.com/ueberdosis/tiptap/compare/v2.1.10...v2.1.11) (2023-09-20)

### Reverts

- Revert "v2.2.11" ([6aa755a](https://github.com/ueberdosis/tiptap/commit/6aa755a04b9955fc175c7ab33dee527d0d5deef0))

## [2.1.10](https://github.com/ueberdosis/tiptap/compare/v2.1.9...v2.1.10) (2023-09-15)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.9](https://github.com/ueberdosis/tiptap/compare/v2.1.8...v2.1.9) (2023-09-14)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.8](https://github.com/ueberdosis/tiptap/compare/v2.1.7...v2.1.8) (2023-09-04)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.7](https://github.com/ueberdosis/tiptap/compare/v2.1.6...v2.1.7) (2023-09-04)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.6](https://github.com/ueberdosis/tiptap/compare/v2.1.5...v2.1.6) (2023-08-18)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.5](https://github.com/ueberdosis/tiptap/compare/v2.1.4...v2.1.5) (2023-08-18)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.4](https://github.com/ueberdosis/tiptap/compare/v2.1.3...v2.1.4) (2023-08-18)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.3](https://github.com/ueberdosis/tiptap/compare/v2.1.2...v2.1.3) (2023-08-18)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.2](https://github.com/ueberdosis/tiptap/compare/v2.1.1...v2.1.2) (2023-08-17)

**Note:** Version bump only for package @tiptap/vue-3

## [2.1.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0...v2.1.1) (2023-08-16)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.14...v2.1.0) (2023-08-16)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.14](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.13...v2.1.0-rc.14) (2023-08-11)

**Note:** Version bump only for package @tiptap/vue-3

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

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.11](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.10...v2.1.0-rc.11) (2023-07-07)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.10](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.9...v2.1.0-rc.10) (2023-07-07)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.9](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.8...v2.1.0-rc.9) (2023-06-15)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.8](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.7...v2.1.0-rc.8) (2023-05-25)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.7](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.6...v2.1.0-rc.7) (2023-05-25)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.6](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.5...v2.1.0-rc.6) (2023-05-25)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.5](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.4...v2.1.0-rc.5) (2023-05-25)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.4](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.3...v2.1.0-rc.4) (2023-04-27)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.3](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.2...v2.1.0-rc.3) (2023-04-26)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.2](https://github.com/ueberdosis/tiptap/compare/v2.0.3...v2.1.0-rc.2) (2023-04-26)

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0c1bba3](https://github.com/ueberdosis/tiptap/commit/0c1bba3137b535776bcef95ff3c55e13f5a2db46))

# [2.1.0-rc.1](https://github.com/ueberdosis/tiptap/compare/v2.1.0-rc.0...v2.1.0-rc.1) (2023-04-12)

**Note:** Version bump only for package @tiptap/vue-3

# [2.1.0-rc.0](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.1.0-rc.0) (2023-04-05)

**Note:** Version bump only for package @tiptap/vue-3

## [2.0.3](https://github.com/ueberdosis/tiptap/compare/v2.0.2...v2.0.3) (2023-04-13)

**Note:** Version bump only for package @tiptap/vue-3

## [2.0.2](https://github.com/ueberdosis/tiptap/compare/v2.0.1...v2.0.2) (2023-04-03)

**Note:** Version bump only for package @tiptap/vue-3

## [2.0.1](https://github.com/ueberdosis/tiptap/compare/v2.0.0...v2.0.1) (2023-03-30)

### Bug Fixes

- Update peerDependencies to fix lerna version tasks ([#3914](https://github.com/ueberdosis/tiptap/issues/3914)) ([0534f76](https://github.com/ueberdosis/tiptap/commit/0534f76401bf5399c01ca7f39d87f7221d91b4f7))

# [2.0.0-beta.220](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.219...v2.0.0-beta.220) (2023-02-28)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.219](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.218...v2.0.0-beta.219) (2023-02-27)

### Bug Fixes

- update typings for node view decorations ([#3783](https://github.com/ueberdosis/tiptap/issues/3783)) ([f869507](https://github.com/ueberdosis/tiptap/commit/f8695073968c5c6865ad8faf05351020abb2a3cc))

# [2.0.0-beta.218](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.217...v2.0.0-beta.218) (2023-02-18)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.217](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.216...v2.0.0-beta.217) (2023-02-09)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.216](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.215...v2.0.0-beta.216) (2023-02-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.215](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.214...v2.0.0-beta.215) (2023-02-08)

### Bug Fixes

- fix builds including prosemirror ([a380ec4](https://github.com/ueberdosis/tiptap/commit/a380ec41d198ebacc80cea9e79b0a8aa3092618a))

# [2.0.0-beta.214](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.213...v2.0.0-beta.214) (2023-02-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.213](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.212...v2.0.0-beta.213) (2023-02-07)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.212](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.211...v2.0.0-beta.212) (2023-02-03)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.211](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.210...v2.0.0-beta.211) (2023-02-02)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.210](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.209...v2.0.0-beta.210) (2023-02-02)

### Features

- **pm:** new prosemirror package for dependency resolving ([f387ad3](https://github.com/ueberdosis/tiptap/commit/f387ad3dd4c2b30eaea33fb0ba0b42e0cd39263b))

# [2.0.0-beta.209](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.208...v2.0.0-beta.209) (2022-12-16)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.208](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.207...v2.0.0-beta.208) (2022-12-16)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.207](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.206...v2.0.0-beta.207) (2022-12-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.206](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.205...v2.0.0-beta.206) (2022-12-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.205](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.204...v2.0.0-beta.205) (2022-12-05)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.204](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.203...v2.0.0-beta.204) (2022-11-25)

### Bug Fixes

- **core:** rename esm modules to esm.js ([c1a0c3a](https://github.com/ueberdosis/tiptap/commit/c1a0c3ae43baac9dd5ed90903d3a0d4eaeea7702))

# [2.0.0-beta.203](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.202...v2.0.0-beta.203) (2022-11-24)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.202](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.201...v2.0.0-beta.202) (2022-11-04)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.201](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.200...v2.0.0-beta.201) (2022-11-04)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.200](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.199...v2.0.0-beta.200) (2022-11-04)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.199](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.198...v2.0.0-beta.199) (2022-09-30)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.198](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.197...v2.0.0-beta.198) (2022-09-29)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.197](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.196...v2.0.0-beta.197) (2022-09-26)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.196](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.195...v2.0.0-beta.196) (2022-09-20)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.195](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.194...v2.0.0-beta.195) (2022-09-14)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.194](https://github.com/ueberdosis/tiptap/compare/v2.0.0-beta.193...v2.0.0-beta.194) (2022-09-11)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.97](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.96...@tiptap/vue-3@2.0.0-beta.97) (2022-09-03)

### Bug Fixes

- vue inject grammar warning ([#3144](https://github.com/ueberdosis/tiptap/issues/3144)) ([c6c5fa6](https://github.com/ueberdosis/tiptap/commit/c6c5fa623a875411b0e72dc3f8f88166f2f8fa1e))

# [2.0.0-beta.96](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.95...@tiptap/vue-3@2.0.0-beta.96) (2022-06-27)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.95](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.94...@tiptap/vue-3@2.0.0-beta.95) (2022-06-20)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.94](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.92...@tiptap/vue-3@2.0.0-beta.94) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.92](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.92...@tiptap/vue-3@2.0.0-beta.92) (2022-06-17)

### Reverts

- Revert "Publish" ([9c38d27](https://github.com/ueberdosis/tiptap/commit/9c38d2713e6feac5645ad9c1bfc57abdbf054576))

# [2.0.0-beta.91](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.90...@tiptap/vue-3@2.0.0-beta.91) (2022-04-27)

### Bug Fixes

- improve Vue nodeViewProps typing ([190a699](https://github.com/ueberdosis/tiptap/commit/190a6993d4d93b4d37b978b33ef22690ed8269b6))

# [2.0.0-beta.90](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.89...@tiptap/vue-3@2.0.0-beta.90) (2022-01-25)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.89](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.88...@tiptap/vue-3@2.0.0-beta.89) (2022-01-20)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.88](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.87...@tiptap/vue-3@2.0.0-beta.88) (2022-01-11)

### Bug Fixes

- Mark `@tiptap/vue-2` and `@tiptap/vue-3` as side effect free ([be8ca68](https://github.com/ueberdosis/tiptap/commit/be8ca68d97c8f169d548e72253d5e6406fcb4c5b))

# [2.0.0-beta.87](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.86...@tiptap/vue-3@2.0.0-beta.87) (2022-01-05)

### Bug Fixes

- revert type changes for useEditor in vue-3 package ([3ba3afb](https://github.com/ueberdosis/tiptap/commit/3ba3afbea38b9b46b5d164e0d6a374ecd0ef63c6))

# [2.0.0-beta.86](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.85...@tiptap/vue-3@2.0.0-beta.86) (2022-01-04)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.85](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.84...@tiptap/vue-3@2.0.0-beta.85) (2021-12-22)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.84](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.83...@tiptap/vue-3@2.0.0-beta.84) (2021-12-15)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.83](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.82...@tiptap/vue-3@2.0.0-beta.83) (2021-12-10)

### Features

- add support for template strings in VueNodeViewRenderer, fix [#1987](https://github.com/ueberdosis/tiptap/issues/1987) ([7c98f80](https://github.com/ueberdosis/tiptap/commit/7c98f80547b8aff9d574732d20f8a3b565b9fdb2))

# [2.0.0-beta.82](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.81...@tiptap/vue-3@2.0.0-beta.82) (2021-12-02)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.81](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.80...@tiptap/vue-3@2.0.0-beta.81) (2021-11-17)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.80](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.79...@tiptap/vue-3@2.0.0-beta.80) (2021-11-10)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.79](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.78...@tiptap/vue-3@2.0.0-beta.79) (2021-11-09)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.78](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.77...@tiptap/vue-3@2.0.0-beta.78) (2021-11-09)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.77](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.76...@tiptap/vue-3@2.0.0-beta.77) (2021-11-09)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.76](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.75...@tiptap/vue-3@2.0.0-beta.76) (2021-11-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.75](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.74...@tiptap/vue-3@2.0.0-beta.75) (2021-11-05)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.74](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.73...@tiptap/vue-3@2.0.0-beta.74) (2021-10-31)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.73](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.72...@tiptap/vue-3@2.0.0-beta.73) (2021-10-26)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.72](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.71...@tiptap/vue-3@2.0.0-beta.72) (2021-10-22)

### Bug Fixes

- fix a bug when using drag handles ([8f8b83a](https://github.com/ueberdosis/tiptap/commit/8f8b83afe47085a86caef00b48ad64c87a64af89))

# [2.0.0-beta.71](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.70...@tiptap/vue-3@2.0.0-beta.71) (2021-10-22)

### Features

- Add extension storage ([#2069](https://github.com/ueberdosis/tiptap/issues/2069)) ([7ffabf2](https://github.com/ueberdosis/tiptap/commit/7ffabf251c408a652eec1931cc78a8bd43cccb67))

# [2.0.0-beta.70](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.69...@tiptap/vue-3@2.0.0-beta.70) (2021-10-14)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.69](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.68...@tiptap/vue-3@2.0.0-beta.69) (2021-10-14)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.68](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.67...@tiptap/vue-3@2.0.0-beta.68) (2021-10-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.67](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.66...@tiptap/vue-3@2.0.0-beta.67) (2021-10-02)

### Bug Fixes

- fix reactive props, see [#1728](https://github.com/ueberdosis/tiptap/issues/1728) ([7f7f93d](https://github.com/ueberdosis/tiptap/commit/7f7f93dc1b4b56c7647de27a792e000b3513c226))

# [2.0.0-beta.66](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.65...@tiptap/vue-3@2.0.0-beta.66) (2021-09-29)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.65](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.64...@tiptap/vue-3@2.0.0-beta.65) (2021-09-28)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.64](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.63...@tiptap/vue-3@2.0.0-beta.64) (2021-09-27)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.63](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.62...@tiptap/vue-3@2.0.0-beta.63) (2021-09-23)

### Bug Fixes

- add support for scoped styles, fix [#1931](https://github.com/ueberdosis/tiptap/issues/1931) ([19840f3](https://github.com/ueberdosis/tiptap/commit/19840f3b258f5dbf8a7edff1a85f297871a5ac66))

# [2.0.0-beta.62](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.61...@tiptap/vue-3@2.0.0-beta.62) (2021-09-22)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.61](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.60...@tiptap/vue-3@2.0.0-beta.61) (2021-09-20)

### Bug Fixes

- fix expose error when using new setup syntax (fix [#1914](https://github.com/ueberdosis/tiptap/issues/1914)) ([60e7755](https://github.com/ueberdosis/tiptap/commit/60e7755b7f7657eec448566580a57db550681ed2))

# [2.0.0-beta.60](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.59...@tiptap/vue-3@2.0.0-beta.60) (2021-09-18)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.59](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.58...@tiptap/vue-3@2.0.0-beta.59) (2021-09-15)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.58](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.57...@tiptap/vue-3@2.0.0-beta.58) (2021-09-07)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.57](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.56...@tiptap/vue-3@2.0.0-beta.57) (2021-09-06)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.56](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.55...@tiptap/vue-3@2.0.0-beta.56) (2021-08-26)

### Bug Fixes

- use shallowRef on Editor ([#1804](https://github.com/ueberdosis/tiptap/issues/1804)) ([46701fd](https://github.com/ueberdosis/tiptap/commit/46701fde666b925e80f6796a45f928e671bee92d))

# [2.0.0-beta.55](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.54...@tiptap/vue-3@2.0.0-beta.55) (2021-08-23)

### Bug Fixes

- fix types for BubbleMenu and FloatingMenu props ([d3242c9](https://github.com/ueberdosis/tiptap/commit/d3242c9a0728ea0d164571a6e1eee20fb528f2d8))

# [2.0.0-beta.54](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.53...@tiptap/vue-3@2.0.0-beta.54) (2021-08-23)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.53](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.52...@tiptap/vue-3@2.0.0-beta.53) (2021-08-20)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.52](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.51...@tiptap/vue-3@2.0.0-beta.52) (2021-08-13)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.51](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.50...@tiptap/vue-3@2.0.0-beta.51) (2021-08-13)

### Bug Fixes

- rename key to pluginKey for menus ([89d26f7](https://github.com/ueberdosis/tiptap/commit/89d26f7cba2a115aa342f0ee621f0b65c840dfb8))

# [2.0.0-beta.50](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.49...@tiptap/vue-3@2.0.0-beta.50) (2021-08-12)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.49](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.48...@tiptap/vue-3@2.0.0-beta.49) (2021-08-11)

### Features

- add key option and shouldShow option to menus (fix [#1480](https://github.com/ueberdosis/tiptap/issues/1480), fix [#1043](https://github.com/ueberdosis/tiptap/issues/1043), fix [#1268](https://github.com/ueberdosis/tiptap/issues/1268), fix [#1503](https://github.com/ueberdosis/tiptap/issues/1503)) ([9ba61c1](https://github.com/ueberdosis/tiptap/commit/9ba61c1582cee838f2214d00285773ace2fb229e))

# [2.0.0-beta.48](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.47...@tiptap/vue-3@2.0.0-beta.48) (2021-07-28)

### Bug Fixes

- fix updating node views, fix [#1656](https://github.com/ueberdosis/tiptap/issues/1656) ([d7f6e0c](https://github.com/ueberdosis/tiptap/commit/d7f6e0ce3f99381d3822cde5ab1c484ed13a4c20))

# [2.0.0-beta.47](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.46...@tiptap/vue-3@2.0.0-beta.47) (2021-07-27)

### Features

- add ignoreMutation option to NodeViewRenderer, fix [#1538](https://github.com/ueberdosis/tiptap/issues/1538) ([651e691](https://github.com/ueberdosis/tiptap/commit/651e6911e3ea5407df6a48783ee16733e0a4f474))

# [2.0.0-beta.46](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.45...@tiptap/vue-3@2.0.0-beta.46) (2021-07-26)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.45](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.44...@tiptap/vue-3@2.0.0-beta.45) (2021-06-23)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.44](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.43...@tiptap/vue-3@2.0.0-beta.44) (2021-06-15)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.43](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.42...@tiptap/vue-3@2.0.0-beta.43) (2021-06-15)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.42](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.41...@tiptap/vue-3@2.0.0-beta.42) (2021-06-14)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.41](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.40...@tiptap/vue-3@2.0.0-beta.41) (2021-06-09)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.40](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.39...@tiptap/vue-3@2.0.0-beta.40) (2021-05-28)

### Bug Fixes

- prevent bug when editor is destroyed very fast ([939fc3d](https://github.com/ueberdosis/tiptap/commit/939fc3d93ab67d54b7fe67b64c423290b3a40df8))

# [2.0.0-beta.39](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.38...@tiptap/vue-3@2.0.0-beta.39) (2021-05-27)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.38](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.37...@tiptap/vue-3@2.0.0-beta.38) (2021-05-24)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.37](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.36...@tiptap/vue-3@2.0.0-beta.37) (2021-05-18)

### Bug Fixes

- move all child nodes within EditorContent ([0f299d2](https://github.com/ueberdosis/tiptap/commit/0f299d228eb4075d24e1c0fb5b39febc6bc77de6))

### Features

- add deleteNode method to node views ([fcee5f8](https://github.com/ueberdosis/tiptap/commit/fcee5f82c6a282191afe5c2cb83b9f5820af28dd))

# [2.0.0-beta.36](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.35...@tiptap/vue-3@2.0.0-beta.36) (2021-05-18)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.35](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.34...@tiptap/vue-3@2.0.0-beta.35) (2021-05-17)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.34](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.33...@tiptap/vue-3@2.0.0-beta.34) (2021-05-13)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.33](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.32...@tiptap/vue-3@2.0.0-beta.33) (2021-05-07)

### Bug Fixes

- revert adding exports ([bc320d0](https://github.com/ueberdosis/tiptap/commit/bc320d0b4b80b0e37a7e47a56e0f6daec6e65d98))

# [2.0.0-beta.32](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.31...@tiptap/vue-3@2.0.0-beta.32) (2021-05-06)

### Bug Fixes

- revert adding type: module ([f8d6475](https://github.com/ueberdosis/tiptap/commit/f8d6475e2151faea6f96baecdd6bd75880d50d2c))

# [2.0.0-beta.31](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.30...@tiptap/vue-3@2.0.0-beta.31) (2021-05-06)

### Bug Fixes

- add exports to package.json ([1277fa4](https://github.com/ueberdosis/tiptap/commit/1277fa47151e9c039508cdb219bdd0ffe647f4ee))

# [2.0.0-beta.30](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.29...@tiptap/vue-3@2.0.0-beta.30) (2021-05-06)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.29](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.28...@tiptap/vue-3@2.0.0-beta.29) (2021-05-05)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.28](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.27...@tiptap/vue-3@2.0.0-beta.28) (2021-05-05)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.27](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.26...@tiptap/vue-3@2.0.0-beta.27) (2021-05-04)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.26](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.25...@tiptap/vue-3@2.0.0-beta.26) (2021-04-23)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.25](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.24...@tiptap/vue-3@2.0.0-beta.25) (2021-04-22)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.24](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.23...@tiptap/vue-3@2.0.0-beta.24) (2021-04-21)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.23](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.22...@tiptap/vue-3@2.0.0-beta.23) (2021-04-16)

### Bug Fixes

- fix editor type for VueRenderer, fix [#281](https://github.com/ueberdosis/tiptap/issues/281) ([f6d8776](https://github.com/ueberdosis/tiptap/commit/f6d8776ca086bf1f2edc6dc099e33a1f00fdd4c7))

# [2.0.0-beta.22](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.21...@tiptap/vue-3@2.0.0-beta.22) (2021-04-16)

### Features

- add tippyOptions prop ([9a56f66](https://github.com/ueberdosis/tiptap/commit/9a56f666a118ca7c59a6f1f67f40e6490e20d3b8))
- remove keepInBounds ([d7282f1](https://github.com/ueberdosis/tiptap/commit/d7282f168bc6cfae4e1630d14bb8462bc135b254))

# [2.0.0-beta.21](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.20...@tiptap/vue-3@2.0.0-beta.21) (2021-04-15)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.20](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.19...@tiptap/vue-3@2.0.0-beta.20) (2021-04-11)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.19](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.18...@tiptap/vue-3@2.0.0-beta.19) (2021-04-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.18](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.17...@tiptap/vue-3@2.0.0-beta.18) (2021-04-08)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.17](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.16...@tiptap/vue-3@2.0.0-beta.17) (2021-04-06)

### Bug Fixes

- fix vue dependency ([73650c1](https://github.com/ueberdosis/tiptap/commit/73650c12e0cc7be13705775a02c031e5e36ee4d1))

# [2.0.0-beta.16](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.15...@tiptap/vue-3@2.0.0-beta.16) (2021-04-06)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.15](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.14...@tiptap/vue-3@2.0.0-beta.15) (2021-04-03)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.14](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.13...@tiptap/vue-3@2.0.0-beta.14) (2021-04-01)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.13](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.12...@tiptap/vue-3@2.0.0-beta.13) (2021-04-01)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.12](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.11...@tiptap/vue-3@2.0.0-beta.12) (2021-04-01)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.11](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.10...@tiptap/vue-3@2.0.0-beta.11) (2021-04-01)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.10](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.9...@tiptap/vue-3@2.0.0-beta.10) (2021-03-31)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.9](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.8...@tiptap/vue-3@2.0.0-beta.9) (2021-03-31)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.8](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.7...@tiptap/vue-3@2.0.0-beta.8) (2021-03-31)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.7](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.6...@tiptap/vue-3@2.0.0-beta.7) (2021-03-28)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.6](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.5...@tiptap/vue-3@2.0.0-beta.6) (2021-03-24)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.5](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.4...@tiptap/vue-3@2.0.0-beta.5) (2021-03-18)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.4](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.3...@tiptap/vue-3@2.0.0-beta.4) (2021-03-17)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.3](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.2...@tiptap/vue-3@2.0.0-beta.3) (2021-03-16)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.2](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-beta.1...@tiptap/vue-3@2.0.0-beta.2) (2021-03-09)

**Note:** Version bump only for package @tiptap/vue-3

# [2.0.0-beta.1](https://github.com/ueberdosis/tiptap/compare/@tiptap/vue-3@2.0.0-alpha.1...@tiptap/vue-3@2.0.0-beta.1) (2021-03-05)

**Note:** Version bump only for package @tiptap/vue-3

# 2.0.0-alpha.1 (2021-02-28)

**Note:** Version bump only for package @tiptap/vue-3
