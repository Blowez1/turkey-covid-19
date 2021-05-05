<template>
  <div class="container mt-5">
    <div class="d-flex justify-content-center mb-5">
      <h1 class="title">TÜRKİYE COVID-19 HASTA TABLOSU</h1>
    </div>
    <table-tr></table-tr>
  </div>
</template>

<script>
import tableTR from "./components/tableTR";
export default {
  name: "app",
  components: {
    "table-tr": tableTR,
  },
};
</script>

<style lang="scss">
$blue: #0465d8;
$orange: #f57a00;
$red: #740400;
$green: #076400;

body {
  font-family: "Work Sans", sans-serif;
}

.title {
  color: $blue;
  font-weight: 800;
}
</style>
