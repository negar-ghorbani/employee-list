<template>
  <nav class="navbar">
    <div class="navbar__links">
      <router-link to="/" class="navbar__link">Home</router-link>
      <router-link to="/employees" class="navbar__link">Employees</router-link>
    </div>
    <div class="navbar__logo">
      <router-link to="/" class="navbar__link">
        <img src="./logo.png" alt="Company Logo" class="navbar__logo-img" />
        <span class="navbar__logo-text">Vendre</span>
      </router-link>
    </div>
  </nav>
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
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  text-align: center;
  padding: 20px;
}

.navbar {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #595959;
  padding: 20px;
  color: #ffffff;
}

.navbar__logo {
  display: flex;
  align-items: center;
}

.navbar__logo-img {
  width: 30px;
  height: 30px;
  margin-right: 10px;
  vertical-align: middle;
}

.navbar__logo-text {
  font-weight: bold;
  color: #ffffff;
  text-align: center;
  vertical-align: middle;
}

.navbar__links {
  display: flex;
  justify-content: center;
}

.navbar__link {
  margin-right: 10px;
  text-decoration: none;
  color: #ffffff;
  padding-inline: 20px;
}

.navbar__link:hover {
  color: #888888;
}
</style>
