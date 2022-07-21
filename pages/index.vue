<template>
  <div class="body">
    <h1>Component name and page name conflicts break Nuxt</h1>

    <p>
      If you navigate to <code>/MyComponent</code>, which is created in <code>pages/MyComponent.vue</code> and tries to render <code>components/MyComponent.vue</code>, Nuxt breaks with the following error:
    </p>

    <pre><code>[nitro] [dev] [unhandledRejection] RangeError: Maximum call stack size exceeded
at Object.shallowReadonly (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/reactivity/dist/reactivity.cjs.js:924:12)
at setupStatefulComponent (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/runtime-core/dist/runtime-core.cjs.js:7084:104)
at setupComponent (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/runtime-core/dist/runtime-core.cjs.js:7039:11)
at renderComponentVNode (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/server-renderer/dist/server-renderer.cjs.js:172:17)
at Module.ssrRenderComponent (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/server-renderer/dist/server-renderer.cjs.js:608:12)
at _sfc_ssrRender (file:///Users/jerryjappinen/Developer/page-name-conflict/.nuxt/dist/server/server.mjs:2970:31)
at renderComponentSubTree (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/server-renderer/dist/server-renderer.cjs.js:253:13)
at renderComponentVNode (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/server-renderer/dist/server-renderer.cjs.js:188:16)
at Module.ssrRenderComponent (/Users/jerryjappinen/Developer/page-name-conflict/node_modules/@vue/server-renderer/dist/server-renderer.cjs.js:608:12)
at _sfc_ssrRender (file:///Users/jerryjappinen/Developer/page-name-conflict/.nuxt/dist/server/server.mjs:2970:31)</code></pre>

    <p>
      This might not happen often because of casing, but this should nevertheless work.
    </p>

    <ul>
      <li>
        <a href="/MyComponent">/MyComponent</a>
      </li>
      <li>
        <a href="/MyComponentX">/MyComponentX</a> (renders the same element without error)
      </li>
    </ul>
  </div>
</template>

<style scoped>
.body {
  border: 1px solid grey;
  padding: 1em;
}

pre {
  border: 1px solid grey;
  padding: 0.5em;
  font-size: 0.75em;
}
</style>
