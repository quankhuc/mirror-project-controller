<template>
  <section class="px-5 pb-6 xs:flex xs:flex-col-reverse">
    <div class="grid grid-cols-2 xs:grid xs:grid-cols-1 gap-4">
      <mirror-controller v-for="mirror in totalNumMirror" :key="mirror" :labelText="`Mirror ` + mirror" />
    </div>
    <mirror-controller labelText="Entire System" />
  </section>
</template>
<script>
import MirrorController from '@/components/MirrorController.vue'
export default {
    name: "IndexPage",
    components: { MirrorController },
    data() {
      return {
        totalNumMirror: 4
      }
    },
}
</script>
