<template>
  <div>
      <h2>ADD LEDGER</h2>
      <div>
            <label for="date">Date :</label>
            <input type="text" v-model="form.date">
        </div>

        <div>
            <label for="explantation">Explantation :</label>
            <input type="text" v-model="form.explantation">
        </div>

        <div>
            <label for="amount">Amount :</label>
            <input type="text" v-model="form.amount">
        </div>

        <div>
            <button @click="addLedger(1)">Income</button>
            <button @click="addLedger(-1)">Expense</button>
        </div>
  </div>
</template>

<script>
import LedgerStore from '@/store/Ledger.js'
export default {
    data() {
    return {
      form: {
        date: "",
        explantation: "",
        amount: "",
      },
      expenses: "",
      income: "",
      balance: 445
    }
  },
  methods:{
      clearForm(){
          this.form = {
              date: "",
              explantation: "",
              amount: "",
          }
      },
      addLedger(type){
            if(type === -1){
                this.form.amount = (-1)*this.form.amount;
                this.form.expenses = this.form.explantation;
                this.form.income = "-"
            }
            else{
                this.form.income = this.form.explantation;
                this.form.expenses = "-"
            }

            this.form.amount = Number(this.form.amount)
            this.balance = this.balance + this.form.amount

            let payload = {
                date: this.form.date,
                income: this.form.income,
                expenses: this.form.expenses,
                amount: this.form.amount,
                balance: this.balance
            }
            LedgerStore.dispatch("addLedger", payload)
            this.clearForm()
      }
  }
}
</script>

<style>

</style>