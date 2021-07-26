<template>
    <div>
        <ledger-create-form></ledger-create-form>
        <ledger-table></ledger-table>
    </div>
</template>

<script>
import LedgerCreateForm from '@/components/LedgerCreateForm.vue'
import LedgerTable from '@/components/LedgerTable.vue'
export default {
    components:{
        LedgerCreateForm,
        LedgerTable
    }
}
</script>

<style scoped>

</style>