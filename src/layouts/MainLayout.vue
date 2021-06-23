<template>
  <q-layout view="hHh lpR fff">

    <q-header elevated  >
      <q-toolbar class="bg-dark glossy text-yellow-2">
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title style="font-family: 'Righteous', cursive;">
         Ilex
        </q-toolbar-title>
        <user-avatar class="glossy cursor-pointer"  v-ripple>
                            <q-menu  square anchor="bottom left" self="top left" :offset="[12,6]">
                      <user-card style="width:304px;" />
          </q-menu>
        </user-avatar>

      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
                  <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
        <q-toolbar-title>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer> -->

  </q-layout>
</template>

<script>
import { ref } from 'vue'
import UserCard from "components/UserCard"
import UserAvatar from 'src/components/userAvatar.vue'
export default {
  components:{UserCard,UserAvatar},
  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
}
</script>