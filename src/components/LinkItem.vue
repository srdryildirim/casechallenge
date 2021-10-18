<template>
  <div class="md:flex mt-4 border-b py-4 px-4 relative cursor-pointer hover:bg-gray-200" @mouseover="isMouseOver = true" @mouseleave="isMouseOver = false">
    <button v-if="isMouseOver" class="absolute bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-2 rounded text-xs right-0 mr-4 z-50 -mt-8">Delete</button>
    <div class="md:flex flex-row w-full">
      <div class="md:flex border px-4 flex-col items-center bg-gray-400 py-4">
        <p class="uppercase text-indigo-600 text-4xl font-bold">{{ link.points }}</p>
        <p class="uppercase">Points</p>
      </div>
      <div class="md:flex px-4 py-4 flex-col justify-between w-full">
        <p class="text-indigo-600 font-bold">{{ link.name }}</p>
        <a :href="link.url" target="_blank" class="text-gray-600 font-bold">{{ link.url }}</a>
        <div class="md:flex flex-row justify-between">
          <span class="text-gray-600 cursor-pointer text-green-600" @click="upVote(link)">Up vote</span>
          <span class="text-gray-600 cursor-pointer text-red-600" @click="downVote(link)">Down vote</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapMutations, mapState } from 'vuex'
export default {
  name: 'LinkItem',
  props: {
    link: {
      required: true,
      type: Object
    }
  },
  data () {
    return {
      isMouseOver: false
    }
  },
  computed:
    mapState([
      "links"
    ]),
  methods: {
    ...mapMutations([
      "upVote",
      "downVote"
    ])
  }
}
</script>

<style>

</style>
