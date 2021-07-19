<template>
  <div class="total-income">
    <h2>TOTAL INCOME</h2>
    <h1>${{ totalIncome }}</h1>
  </div>
</template>

<script>
export default {
  props: {
    totalIncome: Number,
  },
};
</script>

<style scoped>
.total-income {
  display: flex;
  flex-direction: column;
  position: relative;
  width: 100%;
  flex-wrap: wrap;
  text-align: center;
  font-family: "Inter", sans-serif;
  padding: 2rem;
}

.total-income h1 {
  color: black;
  font-family: "Inter", sans-serif;
  font-size: 4rem;
}

.total-income h2 {
  color: #9096a6;
  font-family: "Inter", sans-serif;
  font-size: 1.5rem;
}
</style>
