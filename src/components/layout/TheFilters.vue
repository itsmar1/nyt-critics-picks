<template>
    <div class="container mx-auto">
        <div>
            <div class="flex justify-around">
                <div class="flex items-center p-4 space-x-2">
                    <span class="fa fa-search"></span>
                    <input type="search" name="search" id="search" placeholder="Search" 
                        class="bg-gray-100 p-2 rounded-md"
                        @change="handleFilters"
                        v-model.trim="search">
                </div>
                <div class="flex items-center p-4 space-x-2">
                    <label for="sortBy">Sort By: </label>
                    <select name="sortBy" id="sortBy" v-model="movieOrder" @change="handleFilters" class="rounded-md bg-gray-100 p-2 cursor-pointer">
                        <option value="by-opening-date">Opening Date</option>
                        <option value="by-publication-date">Publication Date</option>
                        <option value="by-title">Title</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>




<script>


export default {
    emits: ['fetch-movies'],
    data() {
        return {
            search: "",
            movieOrder: "by-opening-date"
        }
    },
    methods: {
        handleFilters(event) {
            const name = event.target.name;
            const value = event.target.value;
            if (name === 'search') {
                this.search = value;
            }
            if (name === 'sortBy') {
                this.movieOrder = value;
            }
            console.log('Name: ', name);
            console.log('Value: ', value);
            this.$emit('fetch-movies', this.movieOrder, this.search);
        }
    }

}
</script>


