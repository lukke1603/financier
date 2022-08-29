<script setup lang="ts">
import Table from "primevue/datatable";
import Column from "primevue/column";
import { reactive } from "vue";

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
</script>

<template>
  <main class="container mx-auto">
    <Table :value="expenses" responsiveLayout="scroll">
      <template #empty> No customers found. </template>
      <template #loading> Loading customers data. Please wait. </template>
      <Column field="id" header="ID" />
      <Column field="title" header="Ausgabe" />
      <Column field="cost" header="Kosten" />
      <Column field="period" header="Abrechnungsperiode" />
    </Table>
  </main>
</template>
