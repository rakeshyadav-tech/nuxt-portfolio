<template>
  <div>
    <Header/>
     <h1 ref="test" class="test">
    Works!
  </h1>
  </div>
</template>

<script>
import Header from '~/components/Header';
export default {
  components:{
    Header
  },
  mounted () {
    this.$nextTick(() => { // When using $refs, must wait for nextTick
      const tl = this.$gsap.timeline({ repeat: -1, ease: this.$gsap.Linear.easeInOut(2) })
      tl.to('.test', 2, { x: 200 }) // With css selector
      tl.to(this.$refs.test, 0.5, { x: 0 }) // With refs
    })
  }
}
</script>

<style scoped>
.test {
    color: red;
    display: inline-block;
  }
</style>
