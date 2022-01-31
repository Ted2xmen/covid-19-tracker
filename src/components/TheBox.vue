<template>
  <div class="shadow-xl text-center pt-5 bg-blue-600 hover:bg-blue-400">
    <h2>
      {{ countryName }} 
    </h2>
    <p>
      {{ capital }}
    </p>
    <p>
      {{ population }}
    </p>
  </div>
</template>
<script>
export default {
  name: "TheBox",
  props: ["countryName", "faker", "capital", "population",],
};
</script>
