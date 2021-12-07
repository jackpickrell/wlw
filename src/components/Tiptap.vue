<template>
  <div class="border rounded divide-y">
    <div
      v-if="editor"
      class="overflow-x-scroll whitespace-nowrap flex py-1 space-x-1"
    >
      <button
        type="button"
        @click="editor.chain().focus().toggleBold().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('bold') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/bold-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleItalic().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('italic') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/italic-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleStrike().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('strike') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/strikethrough-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleCode().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('code') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/code-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleHeading({ level: 1 }).run()"
        :class="[
          { 'bg-gray-100': editor.isActive('heading', { level: 1 }) },
          'px-3 py-2 rounded pr-5 relative',
        ]"
      >
        <img class="w-4 h-4" src="/icons/heading-solid.svg" alt="" />
        <span class="absolute bottom-0 right-2 font-bold"> 1 </span>
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleHeading({ level: 2 }).run()"
        :class="[
          { 'bg-gray-100': editor.isActive('heading', { level: 2 }) },
          'px-3 py-2 rounded pr-5 relative',
        ]"
      >
        <img class="w-4 h-4" src="/icons/heading-solid.svg" alt="" />
        <span class="absolute bottom-0 right-2 font-bold"> 2 </span>
      </button>
      <button
        type="button"
        @click="editor.chain().focus().setParagraph().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('paragraph') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/paragraph-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleBulletList().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('bulletList') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/list-ul-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().toggleOrderedList().run()"
        :class="[
          { 'bg-gray-100': editor.isActive('orderedList') },
          'px-3 py-2 rounded',
        ]"
      >
        <img class="w-4 h-4" src="/icons/list-ol-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().setHorizontalRule().run()"
        class="px-3 py-2 rounded"
      >
        <img class="w-4 h-4" src="/icons/grip-lines-solid.svg" alt="" />
      </button>

      <button
        type="button"
        @click="editor.chain().focus().undo().run()"
        class="px-3 py-2 rounded"
      >
        <img class="w-4 h-4" src="/icons/undo-solid.svg" alt="" />
      </button>
      <button
        type="button"
        @click="editor.chain().focus().redo().run()"
        class="px-3 py-2 rounded"
      >
        <img class="w-4 h-4" src="/icons/redo-solid.svg" alt="" />
      </button>
    </div>
    <editor-content :editor="editor" />
  </div>
</template>

<script>
import { Editor, EditorContent } from '@tiptap/vue-3';
import Placeholder from '@tiptap/extension-placeholder';
import StarterKit from '@tiptap/starter-kit';
import { BellIcon } from '@heroicons/vue/outline';

export default {
  components: {
    BellIcon,
    EditorContent,
  },

  data() {
    return {
      editor: null,
    };
  },

  props: ['defaultValue'],

  mounted() {
    this.editor = new Editor({
      content: this.defaultValue || '',
      extensions: [
        StarterKit,
        Placeholder.configure({
          placeholder: 'Start writing...',
        }),
      ],
    });
  },

  beforeUnmount() {
    this.editor.destroy();
  },
};
</script>

<style>
/* Add placeholder when empty */
.ProseMirror p.is-editor-empty:first-child::before {
  content: attr(data-placeholder);
  float: left;
  color: #adb5bd;
  pointer-events: none;
  height: 0;
}
.ProseMirror {
  @apply p-5 min-h-[200px];
}
.ProseMirror h1 {
  @apply text-3xl font-bold;
}
.ProseMirror h2 {
  @apply text-2xl font-bold;
}
.ProseMirror h3 {
  @apply text-xl font-bold;
}
.ProseMirror ul {
  @apply list-disc pl-5;
}
.ProseMirror ol {
  @apply list-decimal pl-5;
}
.ProseMirror hr {
  @apply my-5;
}
</style>
