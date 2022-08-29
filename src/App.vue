<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import MegaMenu from "primevue/megamenu";
import { reactive } from "vue";

interface NavigationItem {
  label: string;
  icon: string;
  url: string;
}

const navigationItems = reactive<Array<NavigationItem>>([
  { label: "Home", icon: "pi pi-fw pi-users", url: "/" },
]);
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="container mx-auto">
        <MegaMenu :model="navigationItems">
          <template #item="{ item }">
            <RouterLink :to="item.url">{{ item.label }}</RouterLink>
          </template>
        </MegaMenu>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
