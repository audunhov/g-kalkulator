<template>
  <div class="content">
    <Calculator :value="g"></Calculator>
    <About :value="g" :date="date"></About>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Calculator from '~/components/Calculator.vue'

export default Vue.extend({
    name: "IndexPage",
    components: { Calculator },
    data() {
      return {
        g: null,
        date: null,
      }
    },
    methods: {
      async load() {
        let response = await fetch("https://g.nav.no/api/v1/historikk")
        let data = await response.json()
        this.g = data[0]["grunnbeløp"]
        this.date = data[0]["dato"]
      }
    },
    created() {
      this.load()
    }
})
</script>

<style>

* {
  box-sizing: border-box;
}

:root {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.content {
  text-align: center;
  position: absolute;
  display: flex;
  flex-direction: column;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
}

</style>
