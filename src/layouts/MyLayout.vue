<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar class="bg-grey-4 text-blue-grey text-bold">
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title class="text-bold">
         Quasar Layout
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      content-class="bg-drawer-custom text-white"
    >
      <q-list cla>
        <q-item-label header>Menu</q-item-label>
         <q-item clickable to="/" exact active-class="text-secondary">
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Início</q-item-label>
            <!-- <q-item-label caption>Categorias de Grupos</q-item-label> -->
          </q-item-section>
        </q-item>
        <q-item clickable to="/grupos-consolidados" exact>
          <q-item-section avatar>
            <q-icon name="group_work" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Grupos Consolidados</q-item-label>
            <q-item-label caption class="text-grey-6">Categorias de Grupos</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container class="bg-grey-2">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: false
    }
  },
  methods: {
    openURL
  }
}
</script>

<style>
.bg-drawer-custom {
  background: #2A3F54 !important;
}
</style>
