<template>
  <div
    v-if="valid"
    class="form-item-wrapper"
  >
    <div :class="{ 'title-space': titleSpace }">
      <div
        v-if="title"
        class="title-wrapper"
      >
        <span class="title">
          {{ title }}
        </span>
        <i
          v-if="icon"
          :class="['icon', icon]"
        />
      </div>
    </div>
    <input
      :type="type"
      class="form-input"
    />
    <div
      v-if="error"
      class="form-item-error"
    >
      <!-- sustituir por icono de error -->
      <span>x </span>
      <!-- sustituir por icono de error -->
      <span>
        {{ error }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormUiInput',

  props: {
    title: { type: String, default: null },
    titleSpace: { type: Boolean, default: false },
    icon: { type: String, default: null },
    type: { type: String, default: 'text' },
    error: { type: String, default: null },
  },

  data() {
    return {
      valid: true,
    };
  },

  beforeCreate() {
    if (!['text', 'number'].includes(this.type)) {
      throw new Error(`Invalid prop: type "${this.type}" is not supported.`);
    }
  },
};
</script>

<style scoped>
.form-item-wrapper {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.title-space {
  height: 20px;
}

.title-wrapper {
  display: flex;
  gap: 4px;
}

.title {
  line-height: 18px;
  font-size: 16px;
  font-weight: 700;
}

.icon {
  font-size: 16px;
}

.form-input {
  padding: 4px 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.form-item-error {
  color: red;
  font-size: 12px;
}
</style>
