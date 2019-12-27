<template>
  <section class="container">
    <div>
      <ul class="resultItems">
        <li class="resultItem" v-for="item in results" :key="item.id">
          <img :src="item['im:image'][0].label" class="imgStyle">
          <dl class="dataStyle">
            <dt>
              <a :href="item.link.attributes.href">
                Name: {{ item.title.label.slice(0,48) + "..." }}
              </a>
            </dt>
          </dl>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import techRank from '~/static/json/techRank.json'

export default {
  components: {
    Logo,
  },
  data() {
    return {
      results: []
    }
  },
  asyncData ({ params }) {
    return { results: techRank.feed.entry }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
