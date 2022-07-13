<template>
  <div class="content">
    <main>
      <Calculator :value="g"></Calculator>
      <About :value="g" :date="date"></About>
    </main>
    <footer>
      Laget av <a href="https://github.com/audunhov">Audun Hammer Hovda</a>
    </footer>
  </div>
</template>

<script>
import Vue from "vue";
import Calculator from "~/components/Calculator.vue";

export default Vue.extend({
  name: "IndexPage",
  components: { Calculator },
  data() {
    return {
      g: null,
      date: null,
    };
  },
  async created() {
    let response = await fetch("https://g.nav.no/api/v1/historikk");
    let data = await response.json();
    this.g = data[0]["grunnbeløp"];
    this.date = data[0]["dato"];
  },
});
</script>

<style>
* {
  box-sizing: border-box;
}

:root {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f1f1f1;
}

main {
  text-align: center;
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: center;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  width: min(600px, 100%);
  height: min(600px, 100%);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  padding: 3em;
  border-radius: 0.5em;
  background-color: #fff;
}

main:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

footer {
  position: fixed;
  bottom: 0;
  right: 1rem;
}
</style>
