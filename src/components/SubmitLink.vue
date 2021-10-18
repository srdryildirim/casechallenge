<template>
  <div>
    <div class="max-w-lg rounded overflow-hidden shadow-md mx-auto">
      <div class="px-6 py-4 text-center">
        <button
          v-if="!submitClicked"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded inline-flex items-center outline-none"
          @click="submitClick()"
        >
          <span>Submit a link</span>
        </button>
        <button
          v-else
          class="bg-gray-500 hover:bg-gray-600 text-white font-bold py-2 px-4 rounded inline-flex items-center outline-none"
          @click="returnToLinksClick()"
        >
          <span>Return to links</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "SubmitLink",
  methods: {
    submitClick() {
      this.$store.commit("submitClicked", true);
    },
    returnToLinksClick() {
      this.$store.commit("submitClicked", false);
    },
  },
  computed: mapState({
    submitClicked: (state) => state.submitClicked,
  }),
};
</script>
