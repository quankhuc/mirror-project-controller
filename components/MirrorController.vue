<template>
  <section>
    <div class="flex flex-col items-center mt-12">
      <div class="rounded bg-sky-400 mb-5">
        <span class="text-lg flex justify-center mx-4 my-2 p-2">
          {{ labelText }}
        </span>
      </div>
      <div class="d-pad-wrapper flex flex-col items-center rounded-xl bg-teal-300">
        <div class="mirror-coordinate flex flex-row w-100 bg-gray-300 p-2 mx-4 mt-4 rounded">
          <b-field label="X-Coordinate">
            <b-input v-model="xCoordinate" type="number" rounded/>
          </b-field>
          <b-field label="Y-Coordinate">
            <b-input v-model="yCoordinate" type="number" rounded/>
          </b-field>
        </div>
        <!-- add a reset button within this mirror controller -->
        <div class="flex flex-row w-100 p-2 mx-4 mt-4 rounded">
          <b-button @click="resetCoordinates" type="is-danger" rounded>
            Reset
          </b-button>
        </div>
        <dpad-controller />
      </div>
    </div>
  </section>
</template>
<script>
import DpadController from '@/components/DpadController.vue'
export default {
  name: 'MirrorController',
  components: { DpadController },
  props: {
    labelText: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      xCoordinate: 0,
      yCoordinate: 0
    }
  },
  methods: {
    resetCoordinates() {
      this.popUpConfirm()
    },
    popUpConfirm() {
      this.$buefy.dialog.confirm({
        title: 'Reset Coordinates',
        message: `Are you sure you want to reset the coordinates of ${this.labelText}?`,
        confirmText: 'Yes',
        type: 'is-danger',
        hasIcon: true,
        onConfirm: () => {
          this.xCoordinate = 0
          this.yCoordinate = 0
        }
      })
    },
  }
}
</script>
<style lang="scss" scoped>
.d-pad-wrapper {
  * {
    margin: auto;
  }
}
.mirror-coordinate {
  :first-child {
    margin-right: 1rem;
  }
}

</style>
