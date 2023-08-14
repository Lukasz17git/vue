<template>
   <div class="block">
      click me
   </div>
</template>

<script>
export default {
   name: "MyButton",
   data() {
      return {
         clicks: 0
      }
   },
   props: ["text"]
}
</script>

<style lang="scss" scoped></style>