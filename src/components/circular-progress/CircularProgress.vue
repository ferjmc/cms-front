<template>
    <v-progress-circular
        :rotate="-90"
        :size="100"
        :width="15"
        :value="progress"
        color="primary"
    >
        {{ progress }}
    </v-progress-circular>
</template>
<script>
export default {
    name: "CircularProgress",
    data () {
      return {
        interval: {},
        progress: 0,
      }
    },
    beforeDestroy () {
      clearInterval(this.interval)
    },
    mounted () {
      this.interval = setInterval(() => {
        if (this.progress === 100) {
          return (this.progress = 0)
        }
        this.progress += 10
      }, 1000)
    },
}
</script>
<style scoped>
.v-progress-circular {
  margin: 1rem;
}
</style>
