<script setup>
import { ref } from 'vue'

const sortOption = ref("year")
const filterStock = ref(false)
const emit = defineEmits(['sortChange','filterStock'])

function changeSorting() {
    emit('sortChange', sortOption)
}

function changeFilter() {
    emit('filterStock', filterStock)
}
</script>

<template>
    <div class=" px-8 bg-cyan-100 ">
        <div class="mt-2 basis-1/4">
            <div class="overflow-hidden shadow sm:rounded-md">
                <div class="bg-white p-6 w-64 h-96">
                    <fieldset>
                      <legend class="sr-only">Filtres</legend>
                      <div class="text-base font-medium text-gray-900" aria-hidden="true">Filtres</div>
                        <div class="mt-4 space-y-4">

                          <div class="flex items-start">
                            <div class="flex h-5 items-center">
                              <input 
                                id="comments" 
                                name="comments" 
                                type="checkbox" 
                                class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-500"
                                v-model="filterStock"
                                @change="changeFilter"                                                               
                              >
                            </div>
                            <div class="ml-3 text-sm">
                              <label for="comments" class="font-medium text-cyan-700">In stock only</label>
                            </div>
                           
                          </div>
     
                        </div>
                        <label for="sortBy" class="block text-sm mt-2 font-medium text-cyan-700">Sort by</label>
                        <select 
                            id="sortBy" 
                            name="sortBy" 
                            autocomplete="country-name" 
                            class="mt-1 block w-full rounded-md border border-gray-300 bg-white py-2 px-3 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
                            v-model="sortOption"
                            @change="changeSorting"
                        >
                          <option value="year">Year</option>
                          <option value="ranking">Pitchfork</option>
                        </select>
                    </fieldset>
                    Albums en stock : 
                </div>
            </div>
        </div>
    </div>
</template>