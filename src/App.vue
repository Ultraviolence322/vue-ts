<template>
  <div class="app p-2">
    <JobList :jobs="jobs" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from '@/types/Job'
import JobList from '@/components/JobList.vue'

export default defineComponent({
  name: 'App',
  components: {
    JobList
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
        title: 'Cook',
        location: 'Kitchen',
        salary: 15000
      }
    ])

    return {
      jobs
    }
  }
});
</script>

<style lang="scss">
</style>
