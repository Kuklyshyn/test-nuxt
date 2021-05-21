<template>
  <div class="container">
    <div>
      <h1>Map</h1>
    </div>
    <Map :locations="locations" v-if="locations.length > 0"></Map>
  </div>
</template>

<script>
import Map from "~/components/Map";
export default {
  name: "about",
  components: {
    Map
  },
  data: () => ({
    locations: []
  }),
  async mounted() {
    const result = await this.$axios.$get('https://experts.sirv.com/backend/wp-json/api/v2/experts');
    this.locations = [... JSON.parse(result).filter(e => e.status === 'publish')];
    console.log(this.locations[0].logo);
  }
}
</script>

<style scoped>
</style>
