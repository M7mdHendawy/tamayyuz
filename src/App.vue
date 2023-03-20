<template>
  <div v-for="(ex, key) in excercises" :key="ex">
    <h1>{{ key }}</h1>
    <table class="container--table">
      <tr>
        <td class="lighten-red">الفصل</td>
        <td class="lighten-red">المادة</td>
        <td class="lighten-red">الحفظ</td>
        <td class="lighten-red">الدراسة</td>
      </tr>

      <tr v-for="(items, values) in ex" :key="values">
        <td class="lighten-red">{{ values }}</td>
        <td v-for="name in items" :key="name">
          <table class="inner--table" v-for="value in name" :key="value">
            <td>
              {{ value }}
            </td>
          </table>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      excercises: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/db")
      .then((response) => response.json())
      .then((response) => (this.excercises = response))
      .then((data) => {
        // Convert JSON text to JavaScript object
        console.table(data);

      })
      .catch((error) => console.error(error));
  },
};
</script>

<style>
@import './assets/style.css'
</style>
