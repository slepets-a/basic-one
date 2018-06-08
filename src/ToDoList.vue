<template>
  <div id="app">
    <Scheduler />
  </div>
</template>

<script>
import Scheduler from './components/Scheduler.vue';

export default {
  name: 'ToDoList',
  components: {
      Scheduler,
  },
};
</script>

<style>
  :root {
    --cubic1: cubic-bezier(0.55,0.085,0.68,0.53);
    --cubic2: cubic-bezier(0.6,-0.28,0.735,0.045);
    --paletteColor1: #000;
    --paletteColor10: #f25a41;
    --paletteColor11: #136bd6;
    --paletteColor12: #2e3540;
    --paletteColor13: #6d7a8e;
    --paletteColor14: #00b8fb;
    --paletteColor15: #475162;
    --paletteColor16: #56d26c;
    --paletteColor2: #fff;
    --paletteColor3: #3f4d5c;
    --paletteColor4: #f5f5f5;
    --paletteColor5: #8898af;
    --paletteColor6: #23292f;
    --paletteColor7: #363636;
    --paletteColor8: #e4e4e4;
    --paletteColor9: #656565;
    --rgbaColor1: rgba(0,0,0,0.1);
    --rgbaColor2: rgba(0,0,0,0.2);
  }
  body {
    margin: 0;
    padding: 0;
    background-color: var(--paletteColor3);
    font-variant-ligatures: none;
    min-width: 37.5rem;
  }
  input {
    -webkit-appearance: none;
    background-color: var(--paletteColor3);
    border: 1px solid var(--paletteColor6);
    border-radius: 5px;
    caret-color: var(--paletteColor6);
    color: var(--paletteColor13);
    font-size: 20px;
    min-width: 215px;
    outline: none;
    padding: 0 14px;
    transition: border-color .1s ease-in-out;
    box-shadow: 6px 6px 14px var(--rgbaColor2);

    &::placeholder {
      font-size: 20px;
      transition: color .1s ease-in-out;
      color: var(--paletteColor6);
    }

    &:focus {
      border-color: var(--paletteColor3);

      &::placeholder {
        color: transparent;
      }
    }
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>
