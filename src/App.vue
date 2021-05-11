<template>
  <div class="input-display">
    <app-input />
    <app-input label="Error" error />
    <app-input label="Disabled" disabled />
    <app-input label="Helper Text" helperText="Some interesting text" />
    <app-input
      label="Helper Text w/ Error"
      helperText="Some interesting text"
      error
    />
    <app-input label="Start Icon" startIcon
      ><svg class="start-icon icons-fa"><use href="#phone"></use></svg
    ></app-input>
    <app-input label="End Icon" endIcon
      ><svg class="icons-fa"><use href="#lock"></use></svg
    ></app-input>
    <app-input label="Input w/ Value" value="TEST" />
    <app-input label="Size Medium" size="md" />
    <app-input label="Size Small" size="sm" />
    <app-input label="Full Width" fullWidth />
    <app-input label="Multiline" multiline />

    <!-- SVG ASSETS -->
    <i data-fa-symbol="phone" class="fas fa-phone-square-alt"></i>
    <i data-fa-symbol="lock" class="fas fa-lock"></i>
  </div>
</template>

<script>
import AppInput from "./components/AppInput.vue";

export default {
  name: "App",
  components: {
    AppInput,
  },
};
</script>

<style>
*,
*:before,
*:after {
  margin: 0;
  padding: 0;
  box-sizing: inherit; /*? Inherit from body */
}

html {
  /*? This defines what 1rem is */
  /*? 1rem = 10px; 10px/16px = 62.5% */
  font-size: 62.5%;
}

body {
  box-sizing: border-box;
  font-family: "Noto Sans JP", sans-serif;
  line-height: 1.3rem;
}

#app {
  margin: 60px auto;
  max-width: 58rem;
}

.input-display {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: flex-start;
}
</style>
