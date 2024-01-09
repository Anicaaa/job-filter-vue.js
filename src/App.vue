<script>
import JobList from './components/JobList.vue'
import JobFilter from './components/JobFilter.vue'
import Attribution from './components/Attribution.vue';

export default {
  data() {
    return {
      tagSelected: []
    };
  },
  mounted() {
  },
  components: { JobList, JobFilter, Attribution }
}
</script>

<template>
  <JobFilter v-model:tag-selected="tagSelected">{{ tagSelected }}</JobFilter>
  <JobList v-model:tag-selected="tagSelected"></JobList>
  <Attribution></Attribution>
</template>
