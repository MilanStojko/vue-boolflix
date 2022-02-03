<template>
  <div>
    <div>Boolfix</div>
    <div>
      <input type="text" placeholder="Cerca film" v-model="search" />
      <button type="submit" @click="$emit('research', search)">Cerca!</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data(){
      return{
          search:""
      }
  }
};
</script>

<style lang="scss" scoped>
</style>