<template>
  <h2>Задача 1</h2>
  <first-task
    title="Введіть Ваш вік:"
    v-model:ageVal.check.setColor="myValue"
  />
  <hr />
  <h2>Задача 2</h2>
  <second-task
    title="Введіть шлях до файлу js "
    v-model.checkPath="pathValue"
  />
  <hr />
  <h2>Задача 3</h2>
  <third-task title="Введіть e-mail:" v-model.check="emailVal" />
  <hr />
  <h2>Задача 4</h2>
  <fourth-task
    v-model:age.checkAge="ageVal"
    v-model:name.checkInput="nameVal"
  />
  <div>{{ ageVal }}</div>
  <hr />
</template>

<script>
import FirstTask from "./components/task1/FirstTask.vue";
import SecondTask from "./components/task2/SecondTask.vue";
import ThirdTask from "./components/task3/ThirdTask.vue";
import FourthTask from "./components/task4/FourthTask.vue";

export default {
  name: "App",
  components: {
    FirstTask,
    SecondTask,
    ThirdTask,
    FourthTask,
  },
  data() {
    return {
      myValue: null,
      pathValue: null,
      emailVal: null,
      ageVal: null,
      nanameValme: null,
    };
  },
};
</script>

<style lang="scss">
@import "./assets/style/";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
