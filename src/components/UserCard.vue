<template>
<q-list class="text-blue-grey-7 ">
  <q-item class="text-center q-mt-sm " dense>
    <q-item-section class="text-blue-grey-5" >
      Account
    </q-item-section>
    <q-item-section side >
      <q-icon name="close" class="cursor-pointer" id="userIcon"   v-close-popup ></q-icon>
    </q-item-section>
  </q-item>
  <q-separator inset class="q-my-sm"></q-separator>
  <q-item dense>
    <q-item-section avatar>
      <user-avatar color="blue-grey-10" text-color="yellow-1"></user-avatar>
    </q-item-section>
    <q-item-section>
      <q-item-label>Mehmet Ilhan</q-item-label>
      <q-item-label caption>Mankurt_Archer3@hotmail.com</q-item-label>
    </q-item-section>
  </q-item>
  <q-separator inset="" class="q-my-sm"></q-separator>
  <q-item clickable v-ripple dense>
    <q-item-section>Profile and Visibility</q-item-section>
  </q-item>
    <q-item clickable v-ripple dense>
    <q-item-section>Event</q-item-section>
  </q-item>
    <q-item clickable v-ripple dense>
    <q-item-section>Settings</q-item-section>
  </q-item>
    <q-item clickable v-ripple dense>
    <q-item-section>Cards</q-item-section>
  </q-item>
  <q-separator inset class="q-my-sm"></q-separator>
    <q-item clickable v-ripple dense>
    <q-item-section>Help</q-item-section>
  </q-item>
    <q-item clickable v-ripple dense>
    <q-item-section>Shortcuts</q-item-section>
  </q-item>
  <q-separator inset class="q-my-sm"></q-separator>
  <q-item>    <q-btn flat  dense label="Out" v-close-popup class="full-width" align="left"></q-btn></q-item>
</q-list>
</template>

<script>
import userAvatar from './userAvatar.vue'
export default {
  components: { userAvatar },
  // name: 'ComponentName',
  setup () {
    return {}
  }
}
</script>

<style lang="scss">
#userIcon:hover{
  color:$grey-9;
}
</style>