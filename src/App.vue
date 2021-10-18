<template>
  <div id="app" class="App min-w-screen min-h-screen flex flex-col bg-grey-lightest font-sans">
    <Header />
    <div class="container mx-auto px-4">
      <SubmitLink />
      <Links v-if="!submitClicked" />
      <CreateLink v-else />
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import Header from '@/components/Header.vue'
import SubmitLink from '@/components/SubmitLink.vue'
import CreateLink from '@/components/CreateLink.vue'
import Links from '@/components/Links.vue'

export default {
  name: 'App',
  components: {
    Header,
    SubmitLink,
    Links,
    CreateLink
  },
  computed:{
    ...mapState([
      "submitClicked",
      "links"
    ])
  }
}
</script>
