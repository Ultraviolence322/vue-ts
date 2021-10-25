<template>
  <div class="job-list">
    <ul>
      <li v-for="job in jobs" :key="job.id">
        <h2>{{job.title}}</h2>
        <p class="job-list__location">{{job.location}}</p>
        <p class="job-list__salary">{{job.salary}}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Job from '@/types/Job'
import { defineComponent, PropType } from 'vue'

export default defineComponent({
  props: {
    jobs: {
      require: true,
      type: Array as PropType<Job[]>
    }
  },

  setup() {
    
  },
})
</script>
