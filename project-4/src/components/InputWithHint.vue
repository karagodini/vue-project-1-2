<template>
  <div class="hint-wrapper">
    <div class="hint-overlay">
      <span>{{ suggestedWord }}</span>
    </div>
    <v-text-field
      v-model="input"
      :label="label"
      :rules="rules"
      @keydown.tab.prevent="applySuggestion"
      class="hint-input"
    />
  </div>
</template>

<script>
export default {
  name: 'InputWithHint',
  props: {
    words: {
      type: Array,
      required: true,
    },
    label: {
      type: String,
      default: 'Введите слово',
    },
    rules: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      input: '',
    }
  },
  computed: {
    suggestedWord() {
      if (!this.input) return ''
      const match = this.words.find(w => w.toLowerCase().startsWith(this.input.toLowerCase()))
      return match || ''
    },
  },
  methods: {
    applySuggestion() {
      if (this.suggestedWord) {
        this.input = this.suggestedWord
      }
    },
  },
}
</script>

<style scoped>
.hint-wrapper {
  position: relative;
}

.hint-overlay {
  position: absolute;
  top: 20px;
  left: 16px;
  color: rgba(0, 0, 0, 0.3);
  font-size: 16px;
  pointer-events: none;
  white-space: nowrap;
  overflow: hidden;
}

.hint-input input {
  background-color: transparent;
  position: relative;
  z-index: 1;
}
</style>
