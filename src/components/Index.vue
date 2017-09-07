<template>
  <q-layout>
    <div slot="header" class="toolbar">
      <button class="hide-on-drawer-visible" @click="$refs.menu.open()">
        <i>menu</i>
      </button>
      <q-toolbar-title :padding="0">
        Hackernews
      </q-toolbar-title>
    </div>
    <q-drawer ref="menu">
      <div class="toolbar light">
        <q-toolbar-title :padding="1">
            Drawer
        </q-toolbar-title>
      </div>

      <div class="list no-border platform-delimiter">
        <q-drawer-link icon="view_quilt" to="/showcase/layout" exact>
          About Layout
        </q-drawer-link>
        <hr>
        <div class="list-label">Layout Components</div>
        <q-drawer-link icon="build" to="/showcase/layout/toolbar">
          Toolbar
        </q-drawer-link>
        <q-drawer-link icon="tab" to="/showcase/layout/tabs">
          Tabs
        </q-drawer-link>
        <q-drawer-link icon="compare_arrows" to="/showcase/layout/drawer">
          Layout Drawer
        </q-drawer-link>
      </div>
    </q-drawer>
    <page></page>
  </q-layout>
</template>
<script>
import Page from './Page'

export default {
  data () {
    return {
      index: 1
    }
  },
  components: {
    Page
  }
}
</script>
<style>


</style>
