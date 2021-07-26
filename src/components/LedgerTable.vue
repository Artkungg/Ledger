<template>
  <div>
      <table>
          <thead>
              <tr>
                  <th>DATE</th>
                  <th>INCOME</th>
                  <th>EXPENSES</th>
                  <th>AMOUNT</th>
                  <th>BALANCE</th>
              </tr>
          </thead>
          <tbody>
            <tr v-for="(led, index) in ledgers" :key="index">
                <td>{{ led.date }}</td>
                <td>
                    {{ led.income }}
                </td>
                <td>{{ led.expenses }}</td>
                <td>{{ led.amount }}</td>
                <td>{{ led.balance }}</td>
            </tr>
          </tbody>
      </table>
  </div>
</template>

<script>
import LedgerStore from '@/store/Ledger.js'
export default {
  data() {
    return{
      ledgers: [],
      form: {
        date: '',
        income: '',
        expenses: '',
        amount: '',
        balance: '',
      },
    } 
  },
  created() {
    this.fetchLedger()
  },
  methods:{
    fetchLedger(){
      LedgerStore.dispatch('fetchData')
      this.ledgers = LedgerStore.getters.ledgers
    },
  },
}
</script>

<style>

</style>