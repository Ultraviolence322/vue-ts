<template>
  <div class="job-list">
    <p class="mt-8 mb-4">
      Order by - <span class="font-bold">{{term}}</span>
    </p>
    <ul>
      <li 
        v-for="job in sortedJobs" :key="job.id"
        class="p-2 border-4 border-blue-500 mb-4 rounded"
      >
        <h2 class="text-2xl font-bold pb-2"><span class="text-sm font-normal">Title: </span>{{job.title}}</h2>
        <p class="job-list__location"><span class="text-sm">Location: </span> {{job.location}}</p>
        <p class="job-list__salary text-green-500"><span class="text-sm text-black">Salary:</span> ${{job.salary}}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
import { computed, defineComponent, PropType } from 'vue'

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    term: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },

  setup(props) {
    const sortedJobs = computed(()=> {
      return props.jobs.sort((a: Job, b: Job) => {
        return a[props.term] < b[props.term] ? 1 : -1
      })

    })

    return {
      sortedJobs
    }
  },
})
</script>
