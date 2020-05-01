<template>
    <div class="home">      
        <v-app>
            <v-content>
                <HelloWorld msg="Welcome to Your Vue.js App" />
            </v-content>
        </v-app>
    </div>
</template>

<script>// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}</script>
