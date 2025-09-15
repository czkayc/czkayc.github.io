<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title> 神秘组织 </q-toolbar-title>

<!--        <div>Quasar v{{ $q.version }}</div>-->
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> 版块列表 </q-item-label>

        <EssentialLink v-for="link in linksList" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: '神秘高光',
    caption: '会有什么高光呢',
    icon: 'sunny',
    link: 'https://quasar.dev',
  },
  {
    title: '神秘角色',
    caption: '会有什么角色呢',
    icon: 'sunny',
    link: 'https://github.com/quasarframework',
  },
  {
    title: '神奇玉辰',
    caption: '好神奇的玉辰啊',
    icon: 'sunny',
    link: 'https://chat.quasar.dev',
  },
  {
    title: '福利收集',
    caption: '整合福利',
    icon: 'sunny',
    link: 'https://forum.quasar.dev',
  },
  {
    title: '神奇游戏',
    caption: '好奇嘛 那就好奇着吧',
    icon: 'sunny',
    link: 'https://twitter.quasar.dev',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
