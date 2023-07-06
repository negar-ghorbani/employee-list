<template>
  <div id="app">
    <EmployeeList />
  </div>
</template>

<script>
import EmployeeList from './components/EmployeeList.vue';

export default {
  name: 'App',
  components: {
    EmployeeList,
  },
};
</script>

<style>
#app {
  text-align: center;
  padding: 20px;
}
</style>
