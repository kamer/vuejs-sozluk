<template>
    
    <table class="table table-striped">
  <thead>
    <tr>
      <th scope="col">Word</th>
      <th scope="col">Definition</th>
    </tr>
  </thead>
  <tbody>
      <Result v-for="(wordDef, index) in wordDefList" v-bind:wordDef="wordDef" :key="index" />
  </tbody>
</table>

</template>

<script>

import Result from './Result.vue'

export default {
    name: 'ResultList',
    props: ['wordDefList'],
    components: {
        Result
    }
}
</script>


<style scoped>

</style>
