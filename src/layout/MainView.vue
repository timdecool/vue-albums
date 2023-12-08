<script setup>
import AlbumList from '@/components/AlbumList.vue'
import FilterPanel from '@/components/FilterPanel.vue'

import { ref } from 'vue'

// Handle sorting option
const sort = ref("year")
function handleSortChange(newSort) {
    sort.value = newSort.value
}

// Handle filter
const filter = ref(false)
function handleFilterChange(newFilter) {
    console.log(newFilter.value)
    filter.value = newFilter.value
}
</script>

<template>
    <div class="flex flex-row ">
        <filter-panel @sortChange="handleSortChange" @filterStock="handleFilterChange"/>
        <main class="bg-white py-5 ml-6 basis-auto">
            <album-list :sortOption="sort" :filterOption="filter" />
        </main>
    </div>


</template>