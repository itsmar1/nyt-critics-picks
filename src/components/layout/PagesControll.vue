<template>
    <div class="w-[80vw] mx-auto mb-8">
        <div class="flex items-center">
            <button v-show="offsetNum !== 0" class="w-[150px] px-3 py-2 bg-gray-900 text-white font-semibold shadow-lg rounded-md" @click="prevPage"><span
                    class="fa fa-chevron-left"></span> Previous
                Page</button>
            <button class="w-[150px] px-3 py-2 bg-gray-900 text-white font-semibold shadow-lg rounded-md ml-auto" @click="nextPage">Next Page
                <span class="fa fa-chevron-right ml-4"></span></button>
        </div>
    </div>
</template>

<script>
export default {
    emits: ['page-control'],
    data() {
        return {
            offsetNum: 0
        }
    },
    methods: {
        nextPage() {
            this.offsetNum += 20;
            this.$emit('page-control', this.offsetNum);
        },
        prevPage() {
            if(this.offsetNum !== 0){
                this.offsetNum -= 20;
                this.$emit('page-control', this.offsetNum);
            }
        },
    }

}
</script>

<style>
</style>