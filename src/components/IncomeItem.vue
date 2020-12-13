<!-- =========================== Template ===================================== -->
<template>
  <div class="income-item">
    <div class="remove-item">❌</div>
    <div class="desc">{{ income.desc }}</div>
    <div class="price">${{ income.value }}</div>
    <div class="date">{{ fromtedDate }}</div>
  </div>
</template>

<!-- =========================== Script ===================================== -->
<script>
export default {
  props: {
    income: Object,
  },

  setup(props) {
    let date = new Date(props.income.date)
    let day = date.getDate()
    let month = date.getMonth()
    let year = date.getFullYear()

    let fromtedDate = day + '/' + month + '/' + year

    return { fromtedDate }
  },
}
</script>

<!-- =========================== Style ===================================== -->
<style lang="scss" scoped>
.income-item {
  position: relative;
  display: flex;
  align-items: center;
  padding: 2.5rem 2rem;
  background-color: #fff;
  border-radius: 2px;
  max-width: 600px;
  margin: 0 auto 30px;
}

.remove-item {
  color: #ef2d2d;
  font-weight: 600;
  font-size: 20px;
  line-height: 1;
  text-align: center;
  margin: 0 15px;
  margin-right: 3rem;
}

.desc {
  color: #666;
  flex: 1 1 100%;
  font-size: 20px;
}

.price {
  color: #666;
  min-width: 100px;
  font-size: 20px;
  margin-right: 7rem;
}

.date {
  color: #666;
  text-align: right;
  font-size: 20px;
}
</style>
