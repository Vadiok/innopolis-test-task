<template>
<div class="component">
  <div class="header">Some Component</div>
  <div class="children">
    <slot />
  </div>
</div>
</template>

<script>
export default {
  name: 'SomeComponent',
};
</script>

<style scoped>
.component {
  border: 1px solid #d80;
  padding: 4px;
  margin-bottom: 4px;
}
.children {
  margin: 4px 4px 4px 16px;
  border: 1px solid #840;
  padding: 4px;
}
</style>
