<template>
  <div class="meme-generator">
    <div class="image-container">
      <img :src="imageUrl" alt="Meme" />
      <text-editor v-model="upperText" transform="upper-text" />
      <text-editor v-model="lowerText" transform="lower-text" />
    </div>
    <div class="controls">
      <input type="file" @change="handleFileUpload" accept="image/*" />
      <button @click="downloadMeme">Download Meme</button>
    </div>
  </div>
</template>

<script>
import TextEditor from './TextEditor.vue';

export default {
  name: 'MemeGenerator',
  components: {
    TextEditor,
  },
  data() {
    return {
      imageUrl: '',
      upperText: '',
      lowerText: '',
    };
  },
  methods: {
    handleFileUpload(event) {
      const file = event.target.files[0];
      this.imageUrl = URL.createObjectURL(file);
    },
    downloadMeme() {
      // Code to generate and download the meme
      // You can use a library like html2canvas to capture the image with text overlays
    },
  },
};
</script>
