<!-- =========================== Template ===================================== -->
<template>
  <header>
    <h1>Income Tracker</h1>
    <div class="total-income">${{ totalIncom }}</div>
  </header>
</template>

<!-- =========================== Script ===================================== -->
<script>
export default {
  props: {
    totalIncom: Number,
  },
}
</script>

<!-- =========================== Style ===================================== -->
<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
  background-color: #131313;
  border-bottom: 5px solid #ffce00;

  // sm 576px
  @media (max-width: 576px) {
    flex-direction: column;
  }
}

header h1 {
  color: #eee;
  font-size: 28px;

  // sm 576px
  @media (max-width: 576px) {
    margin-bottom: 4rem;
  }
}

header .total-income {
  font-family: 'Fira Code', 'Fira Sans', sans-serif;
  background-color: #ffce00;
  color: #111;
  font-size: 20px;
  font-weight: 900;
  padding: 5px 10px;
  min-width: 100px;
  text-align: center;
  border-radius: 50px;
  box-shadow: inset 0px 0px 6px rgba(0, 0, 0, 0.25);
  text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
}
</style>
