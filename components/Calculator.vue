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
    <div class="field">Det tilsvarer {{ monthly }} kroner hver måned</div>
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
  computed: {
    monthly() {
      return Math.ceil((this.nok ? this.nok : 0) / 12);
    },
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

.field > input {
  width: min(100%, 400px);
  padding: 0.5em;
  border: 1px solid rgba(0, 0, 0, 0.6);
  border-radius: 0.5em;
}

.field > label {
  width: 40px;
  display: block;
  height: 1em;
  line-height: 2em;
  margin-left: 0.25em;
  text-align: left;
}
</style>
