<template>
  <div class="app container mx-auto p-4">
    <OrderTerms @selectedTerm="newTerm"/>
    <JobList :jobs="jobs" :term="term" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm';
import JobList from '@/components/JobList.vue'
import OrderTerms from '@/components/OrderTerms.vue'

export default defineComponent({
  name: 'App',
  components: {
    JobList,
    OrderTerms
  },

  setup() {
    const jobs = ref<Job[]>([
      {
        id: 0,
        title: 'IT',
        location: 'World',
        salary: 35000,
      },
      {
        id: 1,
        title: 'Driver',
        location: 'World',
        salary: 10000
      },
      {
        id: 2,
        title: 'Cook',
        location: 'Kitchen',
        salary: 15000
      }
    ])

    const term = ref<OrderTerm>('salary')

    const newTerm = (newTerm: OrderTerm) => {
      term.value = newTerm
    }

    return {
      jobs,
      term,
      newTerm
    }
  }
});
</script>

<style lang="scss">
</style>
