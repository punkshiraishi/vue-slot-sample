<template>
  <div id="app">
    <DemoPage />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import DemoPage from "./components/DemoPage.vue";

@Component({
  components: {
    DemoPage
  }
})
export default class App extends Vue {}
</script>
