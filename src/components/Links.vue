<template>
  <div class="max-w-lg rounded overflow-hidden shadow-md mx-auto my-6">
    <div v-if="links.length > 0" class="px-6 py-4">
      <select
        v-model="sortBy"
        class="block appearance-none w-full bg-white border border-blue-200 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline"
      >
        <option value="most">Most voted first</option>
        <option value="less">Less voted first</option>
      </select>
      <LinkItem v-for="(link, key) in sort(links)" :key="key" :link="link" />
    </div>
    <div
      v-else
      class="bg-red-100 border-t-4 border-red-500 rounded-b text-red-900 px-4 py-3 shadow-md"
      role="alert"
    >
      <div class="flex">
        <div class="py-1">
        </div>
        <div>
          <p class="font-bold">No links found. But don't worry!</p>
          <p class="text-sm">
            You can add new one by clicking on submit a link button above.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import LinkItem from "@/components/LinkItem.vue";
export default {
  name: "Links",
  components: {
    LinkItem,
  },
  computed: {
    ...mapState(["links"]),
    sortBy: {
      get() {
        return this.$store.state.sortBy;
      },
      set(value) {
        this.$store.commit("update_sorting", value);
      },
    },
  },
  methods: {
    sort: function(arr) {
      console.log(this.sortBy);
      return arr.slice().sort((a, b) => {
        if (this.sortBy === "most") {
          return b.points - a.points;
        } else {
          return a.points - b.points;
        }
      });
    },
  },
};
</script>
