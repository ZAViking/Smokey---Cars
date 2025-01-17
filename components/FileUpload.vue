// index.vue (Landing Page)
<template>
  <div>
    <h1>FiveM Handling File Editor</h1>
    <FileUpload @fileUploaded="onFileUploaded" />

    <div v-if="fileContent">
      <h2>Uploaded File Preview</h2>
      <pre>{{ fileContent }}</pre>
      <nuxt-link :to="'/edit'">Edit File</nuxt-link>
    </div>
  </div>
</template>

<script>
import FileUpload from '@/components/FileUpload.vue';

export default {
  components: {
    FileUpload,
  },
  data() {
    return {
      fileContent: null,
    };
  },
  methods: {
    onFileUploaded(content) {
      this.fileContent = content;
    },
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
}
pre {
  background: #f4f4f4;
  padding: 1rem;
  border-radius: 5px;
}
</style>
