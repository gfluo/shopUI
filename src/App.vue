<template>
  <v-app>
    <v-system-bar> </v-system-bar>

    <v-app-bar app color="blue-grey lighten-5" dark>
      <div class="d-flex align-center">
        <!--v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        /-->
        <h2 style="color:black">{{ide}} 永久激活方案</h2>
      </div>
      <v-spacer></v-spacer>

      <v-btn
        href="https://www.789zhao.com/blog/JBZYO72PA98J.html"
        target="_blank"
        text
      >
        <span class="mr-2" style="color:black">最新版本<span style="color:red">{{lastVersion}}</span>激活教程链接</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <HelloWorld :ide="ide" :amount="amount" :version="lastVersion" />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import axios from 'axios';

export default {
  name: "App",

  components: {
    HelloWorld,
  },
  created() {
    axios.post('http://localhost/api/getVersionInfo', {
      ide: this.ide,
    }).then((res) => {
      let resData = res.data.data;
      this.lastVersion = resData.version;
      this.amount = resData.amount;
    })
  },
  data: () => ({
    //
    ide: 'webstorm',
    lastVersion: '2021.3.3',
    amount: 5.99,
  }),
};
</script>
