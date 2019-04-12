<template>
  <div id="app">
    <mark-display
      :markdown="markdown"
      @title="setTitle"
      keyboard-ctrl
      url-hash-ctrl
      auto-font-size
      auto-blank-target
    ></mark-display>
  </div>
</template>

<script>

import MarkDisplay from 'vue-mark-display';

export default {
  name: 'app',
  components: {
    MarkDisplay
  },
  computed: {
    markdown() {
      const {pathname} = location;
      return require(`./md${pathname}.md`).default;
    }
  },
  methods: {
    setTitle({ title }) {
      document.title = title;
    }
  }
}
</script>

<style>
body {
  margin: 0;
  overflow: hidden;
}
</style>
