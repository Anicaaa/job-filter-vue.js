<template>
    <img class="flex items-center" :src="job.logo">
    <div class="left-item">
        <h1 class="font-bold text-teal-700">{{ job.company }}</h1>
        <h2> {{ job.position }}</h2>
        <div class="flex gap-6 text-gray-400">
            <p>{{ job.postedAt }}</p>
            <p>{{ job.contract }}</p>
            <p>{{ job.location }}</p>
        </div>
    </div>

    <div class="flex flex-wrap justify-around gap-4">
        <button class="list-of-skills rounded-md border-none p-1 font-bold text-teal-700" @click="addToFilterBox(language)"
            v-for="language in job.languages" :key="language">
            {{ language }}
        </button>
        <button class="list-of-skills rounded-md border-none p-1 font-bold text-teal-700" @click="addToFilterBox(job.role)">
            {{ job.role }}
        </button>
        <button class="list-of-skills rounded-md border-none p-1 font-bold text-teal-700"
            @click="addToFilterBox(job.level)">
            {{ job.level }}
        </button>
    </div>
</template>

<script>
export default {
    props: ['job'],
    emits: ['addToFilter'],
    methods: {
        addToFilterBox(language) {
            this.$emit("addToFilter", language);
        },
        addToFilterBox(role) {
            this.$emit("addToFilter", role);
        },
        addToFilterBox(level) {
            this.$emit("addToFilter", level);
        }
    }
}
</script>