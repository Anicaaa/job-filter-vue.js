<template>
    <div class="wrapper mt-5 mx-auto">
        <div class="filter-section h-12 rounded-xl grid grid-flow-col auto-cols-auto">
            <div class="flex text-left m-auto" @add-to-filter="handleAddedFilter">
                <div class="tag-btn pl-1 ml-5 rounded" v-for="language in tagSelected" :key="language">{{ language }}<button
                        class="delete-btn font-bolder p-1 border-none rounded-r"
                        @click="handleRemoveFromFilter(language)">X</button></div>
            </div>
            <div class="text-right mr-5 mt-3">
                <p class="clear-btn font-bold" @click="handleRemoveAllFromFilter()">Clear</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['tagSelected'],
    emits: ['update:tagSelected'],
    data() {
        return {
        }
    },
    methods: {
        handleRemoveFromFilter(language) {
            const index = this.tagSelected.indexOf(language)
            return this.tagSelected.splice(index, 1)
        },
        handleRemoveAllFromFilter() {
            this.tagSelected.splice(0, this.tagSelected.length)
        }
    }
}
</script>

   