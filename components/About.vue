<template>
  <div>
    <h1>G-kalkulator</h1>
    <p>Grunnbeløpet i folketrygden (G) brukes til å beregne størrelsen på de fleste offentlige støtteordninger i Norge, og brukes derfor ofte også som beregningsgrunnlag i politiske diskusjoner. Verdien oppdateres første mai hvert år basert på trygdeoppgjøret.</p>
    <br>
    <a href="https://www.nav.no/no/nav-og-samfunn/kontakt-nav/utbetalinger/grunnbelopet-i-folketrygden">Grunnbeløpet per {{date}} er {{value}} kroner.</a>
    <br>
  </div>
</template>

<script>
export default {
    props: ["value", "date"]
}
</script>

<style>
p {
    max-width: 500px;
    margin: 0 auto;
}
</style>