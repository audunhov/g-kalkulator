<template>
  <form class="form">
    <div class="field">
      <input
        type="number"
        name="g"
        id="g"
        :value="g"
        @input="calculateNok"
        step="0.5"
      />
      <label for="g">G </label>
    </div>
    <div class="field">
      <input
        type="number"
        name="nok"
        id="nok"
        :value="nok"
        @input="calculateG"
      />
      <label for="nok">NOK</label>
    </div>
  </form>
</template>

<script>
export default {
  props: ["value"],
  data() {
    return {
      nok: null,
      g: null,
    };
  },
  methods: {
    calculateG(event) {
      this.nok = event.target.value;
      this.g = (this.nok / this.value).toFixed(2);
    },
    calculateNok(event) {
      this.g = event.target.value;
      this.nok = this.g * this.value;
    },
  },
};
</script>

<style>
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 0.5em;
}

.field {
  justify-content: center;
  display: flex;
}

.field > label {
  width: 40px;
  display: block;
}
</style>
