<template>
  <Header />
  <TotalIncome :totalIncome="state.totalIncome" />
  <Form @add-income="AddIncome" />
  <IncomeList :state="state" @remove-item="removeItem" />
</template>

<script>
import { reactive, computed } from "vue";
import Header from "./components/Header";
import Form from "./components/Form";
import TotalIncome from "./components/TotalIncome";
import IncomeList from "./components/IncomeList";

export default {
  components: { Header, Form, TotalIncome, IncomeList },
  setup() {
    const state = reactive({
      income: [],
      sortedIncome: computed(() => {
        let temp = [];

        temp = state.income.slice().sort(function(a, b) {
          return b.date - a.date;
        });
        return temp;
      }),
      totalIncome: computed(() => {
        let temp = 0;
        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
          return temp;
        } else {
          return 0;
        }
      }),
    });
    function AddIncome(obj) {
      let d = obj.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);
      state.income = [
        ...state.income,
        {
          id: Date.now(),
          desc: obj.desc,
          value: parseInt(obj.value),
          date: newD.getTime(),
        },
      ];
    }
    function removeItem(id) {
      state.income = state.income.filter((v) => v.id != id);
    }
    // Return template data
    return {
      Header,
      IncomeList,
      Form,
      state,
      AddIncome,
      removeItem,
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&family=Playfair+Display:wght@400;500;600;700;800;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Playfair Display", serif;
}

body {
  background: #eee;
}
</style>
