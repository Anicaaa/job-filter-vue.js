<template>
    <div class="wrapper mx-auto">
        <div class="item-box flex flex-wrap items-center mt-5 px-7 py-5 rounded-xl gap-12" v-for="job in jobs" :key="job.id"
            v-show="shouldShowJobCard(job)">
            <job-card :job="job" @add-to-filter="handleAddToFilter"></job-card>
        </div>
    </div>
</template>

<script>
import JobCard from './JobCard.vue'

export default {
    props: ['tagSelected'],
    emits: ['update:tagSelected'],
    components: {
        JobCard
    },
    data() {
        return {
            jobs: []
        }
    },
    methods: {
        fetchJobListing() {
            fetch("../../data.json")
                .then(response => response.json())
                .then((data) => {
                    this.jobs = data
                })
        },
        handleAddToFilter(tag) {
            if (!this.tagSelected.includes(tag)) {
                this.tagSelected.push(tag)
            }
            this.$emit('update:tagSelected', this.tagSelected)
        },
        shouldShowJobCard(job) {
            if (this.tagSelected.length === 0) return true
            if (this.tagSelected.every(item => job.languages.includes(item))) return true
            if (this.tagSelected.includes(job.role)) return true
            if (this.tagSelected.includes(job.level)) return true
            return false
        },
    },
    mounted() {
        this.fetchJobListing()
    }
}
</script>