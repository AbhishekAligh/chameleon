<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const theme = ref('#E0E0E0')

const setColor = async (color: any) => {
  theme.value = color
  try {
    let [tab] = await chrome.tabs.query({ active: true });
    // Changes background color in the popup window.
    document.body.style.backgroundColor = color
    chrome.scripting.executeScript<string[], void>({
      target: { tabId: tab.id! },
      args: [color], // Required to pass the color variable from the popup context to the page context that triggered the extension.
      func: (color) => {
        // Changes background color of the current tab/page.
        document.body.style.backgroundColor = color
      }
    });
  } catch (error) {
    console.error('Error changing background color:', error);
  }
}

</script>

<template>
  <h1>{{ msg }}</h1>
  <div class="card">
    <h3>Click on the box below and choose a color to change the background color of the popup and the page</h3>
    <input id="color-selector" :value="theme" type="color" @change="((e: any) => {
      setColor(e.currentTarget.value);
    })" />

    <h2 :style="{ background: theme }"> Hex color -> {{ theme }}</h2>
    <p>
      Edit
      <code>components/ColorSelector.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
    starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

#color-selector {
  height: 100px;
  width: 100px;
}
</style>
