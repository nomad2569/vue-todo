<template>
  <div>
      <button @click="removeAll">Remove all</button>
  </div>
</template>

<script>
export default {
  methods:{
    removeAll(){
      this.$emit('clearAll')
    }
  }
}
</script>

<style>

</style>