<template lang="pug">
form.flex.flex-col.mt-4
  div.flex.flex-col.mb-4
    label.mb-1(for='url') URL Foto
    input#url.border.border-solid.p-2.w-full(v-model='url', type='url')
  div.flex.flex-col.mb-4
    label.mb-1(for='title') Judul
    input#title.border.border-solid.p-2.w-full(v-model='title', type='text')
  div.flex.flex-col.mb-4
    label.mb-1(for='description') Deskripsi
    input#description.border.border-solid.p-2.w-full(v-model='desc', type='text')
  div.flex.justify-end.mb-4
    button.bg-blue-500.text-white.px-4.py-1(@click.prevent='submit', type='submit') Kirim
</template>
<script>
export default {
  data() {
    return {
      desc: '',
      title: '',
      url: '',
    }
  },
  methods: {
    submit() {

      this.$emit('submit', {
        desc: this.desc,
        title: this.title,
        url: this.url,
      })

      // reset form
      this.desc = ''
      this.title = ''
      this.url = ''

    }
  }
}
</script>
