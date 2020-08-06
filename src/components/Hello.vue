<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model="msg"/>
  </div>
</template>

<script>
export default {
  name: 'helloio',
  data () {
    return {
      msg: 'Welcome to iCenter'
    }
  }
}
</script>
