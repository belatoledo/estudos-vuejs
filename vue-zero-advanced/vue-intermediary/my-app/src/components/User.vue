<template>
 <div id="user">
  <h3>Component user: <span>{{name}}</span></h3>
 <button @click="changeName">CHANGE NAME</button>
 </div>
</template>

<script>
export default {
name: 'User',
props: {
  name: {
    type: String,
    required: false
  }
},
 methods: {
   changeName() {
    this.name = 'Izabela'
		this.$emit('nameUser', this.name)
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