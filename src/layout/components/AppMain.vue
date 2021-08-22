<template>
    <v-container>
        <v-fade-transition>
            <router-view :key="key" />
        </v-fade-transition>
    </v-container>
</template>

<script>
export default {
  name: 'AppMain',
  computed: {
    key() {
      return this.$route.path
    }
  }
}
</script>