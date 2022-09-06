<template>
  <div>
    <form class="inputBox" action="#">
      <input class="payment_input" type="text" placeholder="Value" v-model="value">
      <input class="payment_input" type="text" placeholder="Category" v-model="category">
      <input class="payment_input" type="text" placeholder="Date" v-model="date">
      <button class="button" @click="addPayment">Add</button>
    </form>

  </div>
</template>

<script>
export default {
  name: 'AddPaymentForm',
  data: () => ({
    value: '',
    category: '',
    date: ''
  }),
  methods: {
    addPayment () {
      console.log('add', this.currentDate)
      const { value, category, date, currentDate } = this
      const data = {
        value,
        category,
        // date ? date : currentDate
        date: date || currentDate
      }
      console.log(data)

      this.$emit('add-payment', data)
    }
  },
  computed: {
    currentDate () {
      const currentDate = new Date()
      const day = currentDate.getDate()
      const month = currentDate.getMonth() + 1
      const year = currentDate.getFullYear()

      return `${day}.${month}.${year}`
    }
  }
}
</script>

<style scoped>

</style>
