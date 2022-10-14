<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobLists :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";

import JobLists from "./components/JobList.vue";

export default defineComponent({
  name: "App",
  components: { JobLists },
  setup() {
    const jobs = ref<Job[]>([
      { title: "farm worker", location: "land island", salary: 2000, id: "1" },
      { title: "quarryman", location: "app island", salary: 6000, id: "2" },
      { title: "flute player", location: "bar island", salary: 28000, id: "3" },
      { title: "hostess", location: "cool island", salary: 20000, id: "4" },
    ]);
    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style lang="scss" scoped>
header {
  text-align: center;
  .order {
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
}
</style>
