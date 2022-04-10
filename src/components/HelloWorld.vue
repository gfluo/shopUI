<template>
  <v-container >
    <p>1.现在只需要<span> {{amount}} </span>元即可轻松拥有 html, css, js三件套 前端最专业的生产力工具 <span>{{ide}}</span> ，为您的升职加薪助力！</p>
    <v-img
      :src="src"
      lazy-src="https://picsum.photos/id/11/100/60"
      aspect-ratio="1"
      class="grey lighten-2"
      max-width="460"
      max-height="335"
    >
      <template v-slot:placeholder>
        <v-row
          class="fill-height ma-0"
          align="center"
          justify="center"
        >
          <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
        </v-row>
      </template>
    </v-img>
  </v-container>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'HelloWorld',
    props: ['ide', "amount", "version"],
    data: () => ({
      src: '',
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader',
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify',
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify',
        },
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com',
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com',
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuejs.com/vuetify',
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs',
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify',
        },
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
    }),
    created() {
      axios.post('http://localhost/api/getImgInfo', {
      ide: this.ide,
    }).then((res) => {
      let resData = res.data.data;
      let successVersion = this.version.replaceAll(".", "_");
      this.src = `http://${resData.addr}/${this.ide}${successVersion}.png`

    })
    }
  }
</script>
