<template>
  <div id="app">
    <div class="container">
      <header>
        <div class="header">My personal costs</div>
    </header>
    <main>
      <ButtonClicked @clicked="clickedButtonAdd" :showAddForm="showAddForm"/>
      <AddPaymentForm v-if="showAddForm" @add-payment="addPayment"/>
      <PaymentsDisplay
        :paymentsList="paymentsList"
        :paymentsList_Short="paymentsList_Short"
        :paymentsListLenght="paymentsListLenght"
        :indexStart="indexStart"
        :indexEnd="indexEnd"
        test="test"
        show
      />
      <PagiNation
      @clickpage="createPaymentsList"
      :pageCount="pageCount"
      />
    </main>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import PaymentsDisplay from './components/PaymentsDisplay.vue'
import AddPaymentForm from './components/AddPaymentForm.vue'
import ButtonClicked from './components/ButtonClicked.vue'
import PagiNation from './components/Pagination.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    PaymentsDisplay,
    AddPaymentForm,
    ButtonClicked,
    PagiNation
  },
  data: () => ({
    paymentsList: [],
    paymentsListLenght: 0,
    showAddForm: false,
    indexStart: 1,
    indexEnd: 5,
    paymentsList_Short: [],
    pageCount: 0,
    currentPage: 1
  }),
  methods: {
    fetchPaymentsData () {
      return [
        {
          date: '28.03.2020',
          category: 'Food',
          value: 1
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 2
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 3
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 4
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 5
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 6
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 7
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 8
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 9
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 10
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 11
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 12
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 13
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 14
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 15
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 16
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 17
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 18
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 19
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 20
        },
        {
          date: '28.03.2020',
          category: 'Food',
          value: 21
        }]
    },
    addPayment (data) {
      console.log('App.vue: ', data)
      this.paymentsList.push(data)
      this.createPaymentsList(this.currentPage)
      console.log('Количество страниц: ' + this.pageCount)
    },
    clickedButtonAdd () {
      this.showAddForm = !this.showAddForm
    },
    createPaymentsList (n) {
      this.paymentsListLenght = this.paymentsList.length
      console.log('createPaymentsList: ' + n)
      this.indexEnd = n * 5
      this.indexStart = 5 * (n - 1) + 1
      console.log('indexStart: ' + this.indexStart)
      console.log('indexEnd: ' + this.indexEnd)
      this.paymentsList_Short = this.paymentsList.slice((this.indexStart - 1), this.indexEnd)
      this.paymentsList_Short.forEach((i) => {
        console.log(i.value)
      })
      this.pageCount = Math.trunc(this.paymentsListLenght / 5)
      if ((this.paymentsListLenght % 5) > 0) {
        this.pageCount += 1
      }
      this.currentPage = n
    }
  },
  created () {
    setTimeout(() => {
      this.paymentsList = this.fetchPaymentsData()
      this.createPaymentsList(this.currentPage)
    }, 2000)
  }

}
</script>

<style lang="scss" module>

</style>
