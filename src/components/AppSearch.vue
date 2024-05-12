<script>
import { store } from "../store"

export default {
    props: {
        counter: Number,
    },

    data() {
        return {
            store,
            optionsArray: ["All", "Alive", "Dead", "Unknown"]
        }
    }

}
</script>

<template>
    <div class="form-floating px-1 mb-2">
        <select @change="$emit('filter')" class="form-select" id="selectStatus" aria-label="select-status"
            v-model="store.selectedStatus">
            <option v-for="curStatus in optionsArray" :value="curStatus">{{ curStatus }}</option>
        </select>
        <label for="selectStatus">Select the status</label>
    </div>
    <span class="mb-2 p-2" v-if="store.selectedStatus === 'All'">There's a total of <strong>{{ counter }}</strong>
        characters in Rick and Morty.</span>
    <span class="mb-2 p-2" v-else>There's a total of <strong>{{ counter }}</strong> characters with this status.</span>
</template>

<style>

</style>
