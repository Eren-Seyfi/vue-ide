<template>
  <div id="editor"></div>
</template>

<script setup>
import { onMounted } from "vue";
import ace from "ace-builds";

onMounted(() => {

  const editor = ace.edit('editor', {
    maxLines: "100%",
    minLines: 4,
    fontSize: 14,
    theme: 'ace/theme/monokai',
    mode: 'ace/mode/javascript',
    tabSize: 4,
    showPrintMargin: false,
  });

  editor.setOptions({
    enableBasicAutocompletion: true,
    enableLiveAutocompletion: true
  });

  editor.getSession().setValue('function foo(items) { var x = "All this is syntax highlighted"; return x; }');

  editor.getSession().on('change', () => {
    console.log(editor.getValue());
  });
});
</script>

<style>
#editor {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
</style>
