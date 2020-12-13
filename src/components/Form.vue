<!-- =========================== Template ===================================== -->
<template>
  <form @submit.prevent="FormHandler">
    <input type="text" placeholder="Description" v-model="formData.desc" />
    <input type="number" placeholder="Value" v-model="formData.value" />
    <input type="date" v-model="formData.date" />
    <input type="submit" placeholder="SUBMIT" />
  </form>
</template>

<!-- =========================== Script ===================================== -->
<script>
import { reactive } from 'vue'

export default {
  props: { state: Object },

  setup(props, { emit }) {
    const formData = reactive({
      desc: null,
      value: null,
      date: null,
    })

    function FormHandler() {
      emit('add-income', {
        desc: formData.desc,
        value: formData.value,
        date: formData.date,
      })

      formData.desc = null
      formData.value = null
      formData.date = null
    }

    return { formData, FormHandler }
  },
}
</script>

<!-- =========================== Style ===================================== -->
<style lang="scss" scoped>
form {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 5rem;
  margin-bottom: 3rem;

  // lg 992px
  @media (max-width: 992px) {
    flex-direction: column;
  }

  // Input
  input {
    all: unset;
    border: 3px solid black;
    padding: 1.5rem 3rem;
    margin: 1rem;
    font: bold 1.5rem 'Fira Sans', sans-serif;
    letter-spacing: 0.3px;
    font-family: monospace;

    &::placeholder {
      color: #444;
    }
  }

  input[type='submit'] {
    cursor: pointer;
    box-shadow: 5px 5px 2px black;

    transition: 0.1s;

    &:active {
      transform: scale(0.85);
    }
  }
}
</style>
