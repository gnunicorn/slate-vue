<template>
  <Slate :value="JSON.stringify(initialValue)">
    <Editable placeholder="Enter some plain text..." :renderElement="renderElement" :renderLeaf="renderLeaf"></Editable>
  </Slate>
</template>

<script>
  import {Slate, Editable} from 'slate-vue'
  import {withHtml, renderElement, renderLeaf} from './render';

  // this value is for editor
  const initialValue = [
    {
      children: [
        {
          text:
            "By default, pasting content into a Slate editor will use the clipboard's ",
        },
        { text: "'text/plain'", code: true },
        {
          text:
            " data. That's okay for some use cases, but sometimes you want users to be able to paste in content and have it maintaing its formatting. To do this, your editor needs to handle ",
        },
        { text: "'text/html'", code: true },
        { text: ' data. ' },
      ],
    },
    {
      children: [{ text: 'This is an example of doing exactly that!' }],
    },
    {
      children: [
        {
          text:
            "Try it out for yourself! Copy and paste some rendered HTML rich text content (not the source code) from another site into this editor and it's formatting should be preserved.",
        },
      ],
    },
  ]

  export default {
    name: 'paste-html',
    components: {
      Slate,
      Editable
    },
    data() {
      return {
        initialValue,
        renderElement,
        renderLeaf
      }
    },
    created() {
      withHtml(this.$editor)
    }
  };
</script>

<style scoped>

</style>
