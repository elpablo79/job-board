<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Job Board</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "Java developer",
        location: "Berlin",
        salary: 65000,
        id: "1",
      },
      {
        title: "Python developer",
        location: "Amsterdam",
        salary: 70000,
        id: "2",
      },
      {
        title: "Flutter developer",
        location: "Paris",
        salary: 60000,
        id: "3",
      },
      { title: "C++ developer", 
        location: "Eindhoven",
        salary: 62000, 
        id: "4" },
      {
        title: "React developer",
        location: "Mannheim",
        salary: 67000,
        id: "5",
      },
    ]);
    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header h1 {
  font-size: 3em;
  color: #241e7a;
}
</style>
