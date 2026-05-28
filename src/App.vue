<script setup lang="ts">
import {
  NConfigProvider,
  NNotificationProvider,
  NDialogProvider,
  NMessageProvider,
  NH1,
  darkTheme,
  useOsTheme
} from 'naive-ui'
import { MyLayout, MyHeader, MyFooter } from '@libreservice/my-widget'
import MyPwa from './components/MyPwa.vue'
import { homepage, appName } from '../package.json'

const osThemeRef = useOsTheme()
</script>

<template>
  <my-pwa />
  <n-config-provider :theme="osThemeRef === 'dark' ? darkTheme : null">
    <my-layout>
      <template>
      </template>
      <template #content>
        <div style="display: flex; justify-content: flex-end;">
          <a  href="https://github.com/akani2984/rime_ice_wasm">项目源码</a>
        </div>
        <div style="cursor: pointer; text-align: center; margin-top: 16px">
          <n-h1>Rime Ice WASM</n-h1>
        </div>
        <n-notification-provider :max="1">
          <n-dialog-provider>
            <n-message-provider>
              <router-view v-slot="{ Component }">
                <keep-alive>
                  <component :is="Component" />
                </keep-alive>
              </router-view>
            </n-message-provider>
          </n-dialog-provider>
        </n-notification-provider>
      </template>
      <template #footer>
      </template>
    </my-layout>
  </n-config-provider>
</template>
