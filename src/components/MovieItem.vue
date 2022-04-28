<template>
  <div class="flex flex-col items-center justify-center rounded-2xl pt-5 pb-8 px-4 h-[400px] w-[350px] shadow-2xl mb-8 mx-auto">
      <h1 class="text-2xl font-bold text-center">{{ title }}</h1>
      <hr class="w-[75px] mt-2">
      <p class="text-sm text-center text-gray-600 my-4">{{ description }}</p>
      <img :src="image" :alt="title" class="w-full max-h-36 object-contain mb-3">
      <p class="text-sm ">
          <span class="font-semibold">Published:</span> {{ theDate }}
      </p>
  </div>
</template>

<script>

import moment from 'moment';

export default {
    props: ['title', 'link', 'description', 'image', 'date'],
    computed: {
        theDate() {
            return  moment(this.date).format('MMM Do YYYY');
        }
    }

}
</script>

<style>

</style>