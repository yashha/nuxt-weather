<template>
  <section class="row">

    <div class="col">
      <h2>Select Your City 🌍</h2>
      <ul class="cities">
        <li v-for="city in cities">
          <nuxt-link :to="'/weather/' + city.code">{{ city.label }}</nuxt-link>
        </li>
      </ul>
    </div>

    <div class="col">
      <nuxt-child/>
    </div>

  </section>
</template>

<script>
  export default {
    asyncData ({ store }) {
      return {
        cities: store.state.cities.map((city) => ({
          code: city.toLowerCase(),
          label: city
        }))
      }
    },
    head: {
      title: 'Weather',
      meta: [
        { hid: 'description', name: 'description', content: 'Weather of your city' }
      ]
    }
  }
</script>

<style lang="scss" scoped>
  .row {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;

    .col {
      flex: 1 1 auto;
    }
  }
</style>

