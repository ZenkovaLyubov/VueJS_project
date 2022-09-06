<template>
   <div>
    <button v-on:click="showAddPaymentForm" class="button">{{buttonAddName}}</button>
  </div>
</template>

<script>
export default {
  name: 'ButtonClicked',
  data: () => ({
    buttonAddName: 'ADD NEW COST  +'
  }),
  props: {
    showAddForm: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    showAddPaymentForm () {
      this.$emit('clicked')
      if (this.showAddForm) {
        this.buttonAddName = 'ADD NEW COST  +'
      } else if (!this.showAddForm) {
        this.buttonAddName = 'HIDE FORM  -'
      }
    }

  }
}
</script>

<style scoped>

</style>
