<!-- =========================== Template ===================================== -->
<template>
  <div class="container-fluid">
    <Header :totalIncom="state.totalIncom" />
    <Form @add-income="addIncome" />
    <IncomeList :state="state" />
  </div>
</template>

<!-- =========================== Script ===================================== -->
<script>
import { reactive, computed } from 'vue'
import Header from './components/Header'
import Form from './components/Form'
import IncomeList from './components/IncomeList'

export default {
  setup() {
    const state = reactive({
      income: [],

      // Total Income
      totalIncom: computed(() => {
        let temp = 0

        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value
          }
        }

        return temp
      }),

      // Sorted Income
      sortedIncome: computed(() => {
        let temp = []

        temp = state.income.sort(function(a, b) {
          return b.date - a.date
        })

        return temp
      }),
    })

    // Add Income
    function addIncome(data) {
      let d = data.date.split('-')
      let newD = new Date(d[0], d[1], d[2])

      state.income = [
        ...state.income,
        {
          id: Date.now(),
          desc: data.desc,
          value: parseInt(data.value),
          date: newD.getTime(),
        },
      ]

      console.log(state.income)
    }

    return { Header, Form, IncomeList, state, addIncome }
  },
}
</script>

<!-- =========================== Style ===================================== -->
<style lang="scss" scoped></style>
