<template>
<div class="component">
  <div class="header">Validate Component</div>
  <div>
    Validated: {{ validated }}
  </div>
  <div class="children">
    <slot />
  </div>
</div>
</template>

<script>
const COMPONENT_NAME = 'ValidateComponent';

export default {
  name: COMPONENT_NAME,
  data: () => ({
    validated: 0,
  }),
  methods: {
    validate() {
      this.validated += 1;
      const validateOrCheckChildren = (node) => {
        if (node.componentInstance?.$options?.name === COMPONENT_NAME) {
          node.componentInstance?.validate?.();
          return;
        }
        node.children?.forEach((nodeChild) => validateOrCheckChildren(nodeChild));
        if (node.componentInstance?.$slots) {
          Object.keys(node.componentInstance?.$slots).forEach((slotName) => {
            node.componentInstance.$slots[slotName]
              ?.forEach((slotNode) => validateOrCheckChildren(slotNode));
          });
        }
      };
      this.$slots.default?.forEach((node) => validateOrCheckChildren(node));
    },
  },
};
</script>

<style scoped>
.component {
  border: 1px solid #0d8;
  padding: 4px;
  margin-bottom: 4px;
}
.children {
  margin: 4px 4px 4px 16px;
  border: 1px solid #084;
  padding: 4px;
}
</style>
