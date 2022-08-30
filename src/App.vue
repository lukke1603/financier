<script setup lang="ts">
import { RouterLink, RouterView, type RouteLocationRaw } from "vue-router";
import MegaMenu from "primevue/megamenu";
import Button from "primevue/button";

import { reactive } from "vue";
import type { MenuItemLabelType } from "primevue/menuitem";

interface NavigationItem {
  label: MenuItemLabelType;
  icon?: string;
  to: RouteLocationRaw;
  items?: Array<NavigationItem>;
}

const navigationItems = reactive<Array<NavigationItem>>([
  {
    label: "Home",
    icon: "pi pi-home",
    to: "/",
  },
]);
</script>

<template>
  <div class="bg-slate-50 py-4 h-screen">
    <header class="mb-4">
      <div class="wrapper">
        <nav class="container mx-auto">
          <MegaMenu :model="navigationItems" class="bg-white">
            <template #item="{ item }">
              <router-link
                :to="item.to"
                custom
                v-slot="{ href, navigate, isActive, isExactActive }"
              >
                <Button
                  icon="pi pi-home"
                  :label="item.label"
                  :class="{
                    'p-button-text': true,
                    'p-button-secondary': true,
                    'active-link': isActive,
                    'active-link-exact': isExactActive,
                  }"
                  @click="navigate"
                  :href="href"
                />
              </router-link> </template
          ></MegaMenu>
        </nav>
      </div>
    </header>

    <main>
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
.p-megamenu {
  @apply bg-white;
}
</style>
