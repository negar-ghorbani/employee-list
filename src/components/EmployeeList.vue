<template>
  <div class="container">
    <div class="employee_list">
      <ul>
        <li v-for="employee in employees" :key="employee.id">
          <img :src="employee.avatar" :alt="employee.first_name" class="employee_img" />
          <div>
            <p class="employee_name">{{ employee.first_name }} {{ employee.last_name }}</p>
            <a :href="'mailto:' + employee.email" class="employee_contact">Contact</a>
          </div>
        </li>
      </ul>
    </div>
    <div class="pagination">
      <button v-for="page in totalPages" :key="page" @click="goToPage(page)">
        <div v-if="this.currentPage === page" class="active"> {{ page }} </div>
        <div v-else> {{ page }}</div>
      </button>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const employees = ref([]);
    const currentPage = ref(1);
    const perPage = 6;
    const totalPages = ref(0);

    const fetchEmployees = () => {
      fetch(`https://reqres.in/api/users?page=${currentPage.value}`)
        .then((response) => response.json())
        .then((data) => {
          employees.value = [...data.data];
          currentPage.value = data.page;
          totalPages.value = data.total_pages;
        })
        .catch((error) => {
          console.error(error);
        });
    };

    const goToPage = (page) => {
      currentPage.value = page;
      fetchEmployees();
    };

    onMounted(fetchEmployees);

    return {
      employees,
      currentPage,
      totalPages,
      goToPage,
    };
  },
};
</script>

<style>
.employee_list ul {
  list-style: none;
  display: flex;
  flex-direction: row;
  margin-bottom: 20px;
  flex-wrap: wrap;
  justify-content: center;
}

.employee_list li {
  width: 15%;
  max-width: 160px;
  min-height: 250px;
  margin: 10px;
  background-color: #F2F1F2;
  border-radius: 5%;
  box-sizing: border-box;
  flex: 1 1 160px;
  padding: 10px;
}

.employee_img {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  margin-right: 10px;
}

.employee_contact {
  text-decoration: none;
  color: gray;
}

.employee_name {
  font-weight: bold;
}

.pagination button {
  background-color: white;
  border: 1px solid #595959;
  border-radius: 10%;
  margin: 5px;
  color: black;
  padding: 0;
}

.pagination button:hover {
  background-color: #595959;
  color: white;
}

.pagination .active {
  background-color: #595959;
  color: white;
}

.pagination button div {
  padding: 5px 10px;
}
</style>
