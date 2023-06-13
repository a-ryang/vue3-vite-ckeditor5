<script setup lang="ts">
import CKEditor from '@ckeditor/ckeditor5-vue'

import { ClassicEditor } from '@ckeditor/ckeditor5-editor-classic'
import { Essentials } from '@ckeditor/ckeditor5-essentials'
import { Autoformat } from '@ckeditor/ckeditor5-autoformat'
import { Bold, Italic } from '@ckeditor/ckeditor5-basic-styles'
import { BlockQuote } from '@ckeditor/ckeditor5-block-quote'
import { Heading } from '@ckeditor/ckeditor5-heading'
import { Link } from '@ckeditor/ckeditor5-link'
import { List } from '@ckeditor/ckeditor5-list'
import { Paragraph } from '@ckeditor/ckeditor5-paragraph'
import { Alignment } from '@ckeditor/ckeditor5-alignment'
import {
  Image,
  ImageCaption,
  ImageResize,
  ImageResizeEditing,
  ImageResizeHandles,
  ImageStyle,
  ImageToolbar,
} from '@ckeditor/ckeditor5-image'
import type { EditorConfig } from '@ckeditor/ckeditor5-core/src/editor/editorconfig'

withDefaults(defineProps<{ modelValue?: string }>(), { modelValue: '' })

defineEmits<{
  update: [value: string]
}>()

const ckeditor = CKEditor.component

const editorConfig: EditorConfig = {
  language: 'en',
  plugins: [
    Essentials,
    Autoformat,
    Bold,
    Italic,
    BlockQuote,
    Heading,
    Link,
    List,
    Paragraph,
    Image,
    ImageToolbar,
    ImageCaption,
    ImageStyle,
    ImageResize,
    ImageResizeEditing,
    ImageResizeHandles,
    Alignment
  ],
  toolbar: {
    items: [
      'undo',
      'redo',
      '|',
      'heading',
      '|',
      'bold',
      'italic',
      'alignment',
      '|',
      'link',
      'bulletedList',
      'numberedList',
      'blockQuote'
    ]
  },
  image: {
    styles: {
        options: [
            'inline', 'alignLeft', 'alignRight',
            'alignCenter', 'alignBlockLeft', 'alignBlockRight',
            'block', 'side'
        ]
    },
    toolbar: ['imageStyle:inline', 'imageStyle:wrapText', 'imageStyle:breakText', 'imageStyle:side']
  }
}
</script>

<template>
  <ckeditor
    :editor="ClassicEditor"
    :config="editorConfig"
    :model-value="modelValue"
    @update:modelValue="$emit('update', $event)"
  ></ckeditor>
</template>

<style scoped></style>
