<script>
import { ref, provide, inject } from 'vue'

const TABS_SYMBOL = Symbol('TABS')
export const useTabs = () => inject(TABS_SYMBOL)

export default {
  props: {
    initialActiveTab: {
      type: String,
      required: true,
    },
  },
  setup(props, { slots }) {
    const activeTab = ref(props.initialActiveTab)

    const activateTab = (id) => (activeTab.value = id)

    provide(TABS_SYMBOL, {
      activeTab,
      activateTab,
    })

    return () => slots.default()
  },
}
</script>

<style module></style>
