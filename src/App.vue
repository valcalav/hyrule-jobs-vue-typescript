<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>


    <JobList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">

import { defineComponent, reactive, toRefs, ref } from 'vue';
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'
import JobList from './components/JobsList.vue'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1'},
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2'},
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3'},
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4'},
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5'}
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return {jobs, handleClick, order}
  }
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
  color: #11c96d;
  border: 3px solid #11c96d;
  background: #c9eedb;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
