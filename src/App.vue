<template>
<div id="app">
  <validate-component
    ref="validator"
  >
    <some-component>
      <div>
        <validate-component />
      </div>
    </some-component>
    <some-component>
      <validate-component>
        <validate-component />
      </validate-component>
    </some-component>
    <validate-component />
  </validate-component>
  <p>
    <button type="button" @click.prevent="validate">
      Validate
    </button>
  </p>
</div>
</template>

<script>
import ValidateComponent from './components/ValidateComponent.vue';
import SomeComponent from './components/SomeComponent.vue';

export default {
  name: 'App',
  components: {
    ValidateComponent,
    SomeComponent,
  },
  methods: {
    validate() {
      // eslint-disable-next-line no-unused-expressions
      this.$refs.validator?.validate?.();
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 1024px;
  margin: 60px auto;
}
#app .header {
  margin: 8px 0 16px;
  font-size: 1.2em;
  font-weight: bold;
}
</style>
