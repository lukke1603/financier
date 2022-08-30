<script setup lang="ts">
import Table from "primevue/datatable";
import Column from "primevue/column";
import Card from "primevue/card";
import Dialog from "primevue/dialog";
import Button from "primevue/button";
import { reactive, ref } from "vue";

enum Period {
  MONTHLY,
  YEARLY,
  DAILY,
}

enum Category {
  TELECOMMUNICATION,
  HOME,
}

interface Expense {
  id: number;
  title: string;
  cost: number;
  period: Period;
  category: Category;
}

const expenses = reactive<Array<Expense>>([
  {
    id: 1,
    title: "Telekom Mobilfunk",
    cost: 24.99,
    period: Period.MONTHLY,
    category: Category.TELECOMMUNICATION,
  },
  {
    id: 2,
    title: "Telekom Festnetz",
    cost: 54.99,
    period: Period.MONTHLY,
    category: Category.TELECOMMUNICATION,
  },
  {
    id: 3,
    title: "Miete (Kalt)",
    cost: 300,
    period: Period.MONTHLY,
    category: Category.HOME,
  },
]);

const showAddExpenseDialog = ref(false);
</script>

<template>
  <div class="container mx-auto">
    <Card>
      <template #content>
        <Dialog v-model:visible="showAddExpenseDialog" modal>Content</Dialog>

        <Button
          @click="showAddExpenseDialog = !showAddExpenseDialog"
          class="p-button-text"
          label="Ausgabe hinzufügen"
        ></Button>

        <Table class="mt-4" :value="expenses" responsiveLayout="scroll">
          <template #empty> No customers found. </template>
          <template #loading> Loading customers data. Please wait. </template>
          <Column field="id" header="ID" />
          <Column field="title" header="Ausgabe" />
          <Column field="cost" header="Kosten" />
          <Column field="period" header="Abrechnungsperiode" />
        </Table>
      </template>
    </Card>
  </div>
</template>

<style>
.p-card-body {
  @apply py-0 !important;
}
</style>
