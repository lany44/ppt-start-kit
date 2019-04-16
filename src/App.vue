<template>
  <div id="app">
    <mark-display
      :markdown="markdown"
      :base-url="baseUrl"
      keyboard-ctrl
      url-hash-ctrl
      auto-font-size
      auto-blank-target
      support-preview
      @title="setTitle"
    ></mark-display>
  </div>
</template>

<script>

import MarkDisplay from 'vue-mark-display';

import { setHighlighter } from "vue-mark-display";
import hljs from "highlight.js";
import "highlight.js/styles/github.css";

setHighlighter(code => hljs.highlightAuto(code).value);

export default {
  name: 'app',
  components: {
    MarkDisplay
  },
  computed: {
    baseUrl() {
      const {origin, pathname} = location;
      return `${origin}/md${pathname}/`;
    },
    markdown() {
      return require(`../public/md${location.pathname}/index.md`).default;
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
* {
}

body {
  margin: 0;
  overflow: hidden;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: #f5f5f5;
  text-shadow: 0 0 0.25em #ccc;
  line-height: 1.25;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0.25em 0;
  font-weight: 500;
}
p {
  margin: 0.25em 0;
}
li {
  font-size: 0.7em;
  text-align: initial;
}
blockquote {
  font-size: 0.6em;
  text-align: initial;
  background-color: rgba(127, 127, 127, 0.2);
  padding: 0.25em 1em;
  border-radius: 0.25em;
}
pre {
  text-align: initial;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 0.5vw;
  padding: 0 0.125em;
  margin: 0.5em 0;
  font-size: .9em;
}
img {
  height: 200px;
}

small {
  font-size: 0.6em;
}
strong {
  color: red;
}
em {
  color: grey;
  font-size: 0.7em;
}
s,
strike {
  color: gray;
}
code {
  font-size: 0.75em;
}
mark {
  border-radius: 0.5vw;
  padding: 0 0.125em;
}
table {
  border-collapse: collapse;
  margin: 0.25em 0;
  background-color: white;
  font-size: 0.5em;
}
th,
td {
  border: 1px solid gray;
  padding: 0.2em 0.4em;
}
thead {
  background-color: #f0f0f0;
}
tbody > tr:nth-child(2n) {
  background-color: #f0f0f0;
}
hr {
  width: 90%;
  border-width: 2px;
  border-style: dashed;
}

</style>