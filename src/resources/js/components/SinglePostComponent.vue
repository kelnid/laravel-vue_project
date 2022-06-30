<template>
  <div>
     <div>Color: {{ obj.color }} </div>
     <div>Number: {{ obj.number > 10 ? 'more 10' : 'less 10' }}</div>
     <div>Is published: {{ obj.isPublished ? 'Published' : 'not published'}}</div>
  </div>
</template>

<script>
export default {
    name: "SinglePostComponent",

    props: [
        'obj'
    ],

}
</script>

<style scoped>

</style>
