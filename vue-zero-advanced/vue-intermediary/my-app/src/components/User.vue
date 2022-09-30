<template>
 <div id="user">
  <h2>Author: <span>{{name}} {{lastname.split('')}}</span></h2>
 </div>
</template>

<script>
export default {
 name: 'User',
 props: {
  lastname: {
   type: String,
   required: true
  }
 },
 //without validation → props: ['lastname'],
 data() {
  return {
   name: 'Izabela'
  }
 },
}
</script>

<style scoped>
span {
 font-weight: 600;
 color: hotpink;
}
</style>