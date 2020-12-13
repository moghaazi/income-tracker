<!-- =========================== Template ===================================== -->
<template>
  <div class="income-list">
    <IncomeItem
      v-for="data in state.sortedIncome"
      :key="data.id"
      :income="data"
    />
  </div>
</template>

<!-- =========================== Script ===================================== -->
<script>
import IncomeItem from './IncomeItem'

export default {
  props: {
    state: Object,
  },

  components: {
    IncomeItem,
  },
}
</script>

<!-- =========================== Style ===================================== -->
<style lang="scss" scoped>
income-list {
  margin-top: 3rem;
  padding: 1.5rem;
}
</style>
