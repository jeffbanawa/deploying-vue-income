<template>
  <header>
    <h1>Income Tracker</h1>
  </header>
</template>

<script>
export default {
  props: {
    totalIncome: Number,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
  background-color: #fff;
  -webkit-box-shadow: 0px 7px 20px -5px rgba(0, 0, 0, 0.05);
  box-shadow: 0px 7px 20px -5px rgba(0, 0, 0, 0.05);
  min-height: 80px;
}

header h1 {
  color: #435af8;
  font-size: 28px;
}
</style>
