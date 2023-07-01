<template>
  <div class="text-editor">
    <textarea
      v-model="text"
      @input="handleTextChange"
      :style="textStyle"
    ></textarea>
    <div class="style-controls">
      <input type="color" v-model="fontColor" />
      <select v-model="fontSize">
        <option value="12">12px</option>
        <option value="16">16px</option>
        <option value="20">20px</option>
      </select>
      <select v-model="fontFamily">
        <option value="Arial">Arial</option>
        <option value="Comic Sans MS">Comic Sans</option>
        <option value="Pacifico">Pacifico</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TextEditor',
  props: {
    value: String,
    transform: String,
  },
  data() {
    return {
      text: this.value,
      fontColor: '#000000',
      fontSize: '16',
      fontFamily: 'Arial',
    };
  },
  computed: {
    textStyle() {
      return {
        color: this.fontColor,
        fontSize: `${this.fontSize}px`,
        fontFamily: this.fontFamily,
      };
    },
  },
  watch: {
    text(newValue) {
      this.$emit('input', newValue);
    },
  },
  methods: {
    handleTextChange(event) {
      this.text = event.target.value;
    },
  },
};
</script>
