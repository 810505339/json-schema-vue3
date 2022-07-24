<script setup lang="ts">
import * as monaco from 'monaco-editor'
const codeBox = $ref<HTMLHtmlElement | null>(null)
const option: monaco.editor.IStandaloneEditorConstructionOptions = {
  value: '',
  language: 'json',
  theme: 'vs-dark',
  automaticLayout: false,
  minimap: {
    enabled: false,
  },
}

const init = () => {
  nextTick(() => {
    monaco.editor.create(codeBox!, option)
    console.log(1)
  })
}
init()
</script>

<template>
  <div ref="codeBox" h-xl />
</template>
