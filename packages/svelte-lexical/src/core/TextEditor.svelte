<script>
  import { createEditor } from 'lexical';
  import { onMount, setContext } from 'svelte';
  import {initializeEditor} from "./initializeEditor.ts";

  export let config = {};
  let contentEditableElement;

  const editor = createEditor(config);
  setContext('editor', editor);

  onMount(() => {
    editor.setRootElement(contentEditableElement);
    initializeEditor(editor);
  });
</script>

<div class="editor-shell">
  <slot name="toolbar" />
  <div class="editor-container">
    <div
      contenteditable="true"
      bind:this={contentEditableElement}
      class="ContentEditable__root"
    />
    <!-- slot for plugins -->
    <slot />    
  </div>
  <slot name="actions" />
  
</div>

<style>
  .ContentEditable__root {
    min-height: 150px;
    border: 0;
    resize: none;
    cursor: text;
    font-size: 15px;
    caret-color: rgb(5, 5, 5);
    display: block;
    position: relative;
    tab-size: 1;
    outline: 0;
    padding: 10px;
    overflow: auto;
    resize: vertical;
  }
</style>
