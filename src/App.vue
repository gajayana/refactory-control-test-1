<template lang="pug">
div#app
  div.w-full.max-w-2xl.mx-auto
    app-gallery(v-if='items.length', :items='items')
    app-form(@submit='submit')
</template>

<script>
import AppForm from './components/AppForm.vue'
import AppGallery from './components/AppGallery.vue'

export default {
  name: 'app',
  data() {
    return {
      items: []
    }
  },
  components: {
    AppForm,
    AppGallery,
  },
  methods: {
    submit(payload) {
      if (!payload || this.items.length === 4) return
      this.items.push(payload)
    }
  }
}
</script>
