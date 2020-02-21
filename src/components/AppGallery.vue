<template lang="pug">
div.flex.flex-col.mt-4.w-full
  //- hero
  div.mb-4.relative.w-full
    div.flex.flex-col.w-full
      div.relative
        img.w-full(:src='selectedItem.url')
        button.absolute.bg-blue-700.h-8.left-0.text-white.w-12.vert-center(@click.prevent='prev') <
        button.absolute.bg-blue-700.h-8.right-0.text-white.w-12.vert-center(@click.prevent='next') >
      div.bg-white.p-4(v-if='selectedItem.title')
        h1.font-bold.leading-tight.text-lg {{ selectedItem.title }}
        p {{ selectedItem.desc }}

  //- thumbnails
  div.flex.-mx-2
    a.cursor-pointer.flex.flex-col.px-2(v-for='(item, key) in items', @click.prevent='select(key)', class='w-1/4')
      img.flex.w-full(:src='item.url')
      h2.bg-white.font-bold.leading-tight.p-2.text-center(v-if='item.title') {{ item.title }}
</template>
<script>
export default {
  data() {
    return {
      selectedItem: '',
      selectedKey: 0,
    }
  },
  props: {
    items: {
      type: Array,
      default: () => { return [] }
    }
  },
  created() {
    this.selectedItem = this.items[this.selectedKey]
  },
  watch: {
    selectedKey(val) {
      if( val < 0 || val === this.items.length ) return

      this.selectedItem = this.items[val]
    }
  },
  methods: {
    next() {
      if ( this.selectedKey < this.items.length - 1 ) this.selectedKey++
    },
    prev() {
      if ( this.selectedKey > 0 ) this.selectedKey--
    },
    select(key) {
      this.selectedKey = key
    }
  }
}
</script>
<style scoped>
.vert-center {
  top: 50%;
  transform: translateY(-50%)
}
</style>
