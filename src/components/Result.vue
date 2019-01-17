<template>
    <tr>
      <td> {{wordDef.title}} </td>
      <td> {{wordDef.desc}} </td>
    </tr>
</template>

<script>
export default {
    name: 'Result',
    props: ['wordDef']
}
</script>

<style scoped>

</style>
