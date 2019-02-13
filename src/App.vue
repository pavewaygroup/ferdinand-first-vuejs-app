<template>
  <v-app>
    <v-content>
      <v-layout row wrap justify-center align-center>
           <v-btn color="success" :to="{name:'home'}">Todo-list</v-btn>
           <v-btn color="success" :to="{name:'calculator'}">Calculator</v-btn>
      </v-layout>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data () {
    return {
      //
    }
  }
}
</script>
