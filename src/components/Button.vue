<template>
  <button @click="onClick()" style="background: rgba(255,255,255,0.15)" class="btn">{{text}}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      // console.log('click')
      this.$emit('btn-click')
    }
  }
}
</script>