# Vue 3 + TypeScript + Vite

Basic chrome extension with *Vue3 + TS + Vite*, that let's you pick a color from the color selector and change the background color of body 
with the selected color, for the :
> Popup that opens when you trigger the extension & the page from where the extension was triggered

## Recommended Setup

- [VS Code](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (previously Volar) and disable Vetur

- Use [vue-tsc](https://github.com/vuejs/language-tools/tree/master/packages/tsc) for performing the same type checking from the command line, or for generating d.ts files for SFCs.

- Install the dependencies
  - ```bun install```

- Run in Development
    - ```bun run dev```
- Run in Production
  - ```bun run build```






> __NOTE:__ We are using a developer dependency called __CRXJS__ that allows HMR while developing the chrome extension which saves a lot of time by omission of the repetitive build step.