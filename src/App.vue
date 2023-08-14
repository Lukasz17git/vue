<template>
   <h1 ref="myheader">Lukasz Reaction Timer</h1>
   <button @click="start">{{ text }}</button>
   <p>{{ delay }}</p>
   <Block v-if="isPlaying" />
   <Results />
   <div><b>{{ number }}</b></div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
   name: 'App',
   data() {
      return {
         text: "play",
         isPlaying: false,
         delay: null,
         stopGameCallback: undefined,
         number: 0
      }
   },
   components: {
      Block,
      Results
   },
   methods: {
      start() {
         this.isPlaying = true
         this.delay = 2000 + Math.trunc(Math.random() * 5000)
         if (this.stopGameCallback) {
            clearTimeout(this.stopGameCallback)
         }
         const stopCurrentGame = setTimeout(function () {
            this.isPlaying = false
         }.bind(this), this.delay);
         this.stopGameCallback = stopCurrentGame
      }
   },
   mounted() {
      console.log('component mounted', this.$refs, this.$data)
      this.text = 'not play'
      setTimeout(() => {
         console.log('this', this.isPlaying)
      }, 1000);
      setInterval(() => {
         this.number++
      }, 400)
   },
   beforeMount() {
      console.log('before mounted', this.$refs, this.$data)
   },
   created() {
      console.log('component created', this.$refs, this.$data)
   },
   beforeCreate() {
      console.log('before created', this.$refs, this.$data)
   },
   beforeUpdate() {
      console.log('before update', this.$refs, this.$data)
   },
   updated() {
      console.log('component updated', this)
   }


}
</script>

<style lang="scss" scoped></style>