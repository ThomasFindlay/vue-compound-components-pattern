<template>
  <div>
    <slot />
  </div>
</template>
<script>
export default {
  props: {
    initialActiveTab: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      activeTab: this.initialActiveTab,
    }
  },
  provide() {
    let tabState = {}
    Object.defineProperty(tabState, 'activeTab', {
      enumerable: true,
      get: () => this.activeTab,
    })
    return {
      tabState,
      activateTab: this.activateTab,
    }
  },
  methods: {
    activateTab(id) {
      this.activeTab = id
    },
  },
}
</script>

<style module></style>
