<script setup>
import { ref, defineProps, computed } from 'vue'
import { records } from '@/data/allRecords'
import AlbumCard from '@/components/AlbumCard.vue'

const props = defineProps({
    sortOption: {
        type: String,
        required: true
    },
    filterOption: {
        type: Boolean,
        required: true
    }
})

const bruteRecords = ref(records);
const allRecords = computed(() => {
    let computedRecords = bruteRecords.value
    if(props.sortOption === "year") computedRecords = computedRecords.sort((a, b) => b.year-a.year)
    else if (props.sortOption === "ranking") computedRecords = computedRecords.sort((a,b) => a.pitchforkPos - b.pitchforkPos)
    if(props.filterOption) computedRecords = computedRecords.filter((item) => item.stock > 0)
    return computedRecords    
})
const totalStock = computed(() => {
    return bruteRecords.value.reduce(
        (accumulator, currentValue) => accumulator + currentValue.stock,
        0
    )
})

</script>

<template>
    {{ totalStock }}
    <section class="text-gray-600 body-font">
        <div v-for="record in allRecords" :key="record.id">
            <album-card :record="record"/>
        </div>
    </section>
</template>