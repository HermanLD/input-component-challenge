<template>
  <label
    class="text-input"
    :data-error="error"
    :data-size="size"
    :data-width="fullWidth"
    :disabled="disabled"
  >
    <div class="text-input-label">{{ label }}</div>

    <slot v-if="startIcon"></slot>
    <textarea
      class="real-input"
      v-if="multiline"
      :value="value"
      :cols="col"
      :rows="row"
      :disabled="disabled"
      :placeholder="placeholder"
    ></textarea>
    <input
      class="real-input"
      type="text"
      v-else
      :value="value"
      :disabled="disabled"
      :placeholder="placeholder"
    />
    <slot v-if="endIcon"></slot>
    <p class="text-input-helper" v-if="helperText">{{ helperText }}</p>
  </label>
</template>

<script>
export default {
  name: "AppInput",
  props: {
    error: Boolean,
    disabled: Boolean,
    multiline: Boolean,
    startIcon: Boolean,
    endIcon: Boolean,
    fullWidth: Boolean,
    helperText: String,
    value: String,
    size: {
      type: String,
      default: "md",
    },
    placeholder: {
      type: String,
      default: "Placeholder",
    },
    label: {
      type: String,
      default: "Label",
    },
    row: {
      type: Number,
      default: 10,
    },
    col: {
      type: Number,
      default: 20,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
input,
textarea {
  border: none;
}

input:focus,
textarea:focus {
  outline: none;
}

.text-input {
  position: relative;
  display: flex;
  align-items: center;
  margin: 2.4rem 1rem;
  border: 1px solid #828282;
  border-radius: 8px;
  letter-spacing: 1px;
}

.real-input {
  width: auto;
  line-height: 20px;
}

.real-input::placeholder {
  font-size: 1.4rem;
  font-weight: 500;
}

.icons-fa {
  --svg-sizing: 1.6rem;
  width: var(--svg-sizing);
  height: var(--svg-sizing);

  vertical-align: middle;
  flex-basis: auto;
}

.start-icon {
  margin-right: 1.5rem;
}

.text-input .icons-fa {
  /* Gray 3 */
  color: #828282;
}

/** When the real input el inside is focused*/
.text-input:focus-within {
  --clr-primary: #2962ff;
  color: var(--clr-primary);
  border-color: var(--clr-primary);
}

[data-error="true"].text-input {
  --clr-danger: #d32f2f;
  color: var(--clr-danger);
  border-color: var(--clr-danger);
}

.text-input:hover,
[data-error="true"].text-input:hover {
  --gray-1: #333333;
  color: var(--gray-1);
  border-color: var(--gray-1);
}

[data-size="md"].text-input,
[data-size="sm"].text-input {
  display: inline-block;
}

[data-size="md"].text-input {
  padding: 1.8rem 1.2rem;
}

[data-size="sm"].text-input {
  padding: 1rem 1.2rem;
}

[data-width="true"].text-input {
  width: 100%;
}

[disabled="true"].text-input {
  border: 1px solid #e0e0e0;
}

[disabled="true"].text-input,
[disabled="true"].text-input:hover,
[disabled="true"].text-input > .real-input:disabled {
  --gray-1: #333333;
  color: var(--gray-1);
  background-color: #f2f2f2;
}

.text-input-label,
.text-input-helper {
  position: absolute;
}

.text-input-label {
  font-size: 1.2rem;
  top: -2rem;
  left: 0;
}

.text-input-helper {
  bottom: -2rem;
  left: 0;
}
</style>
