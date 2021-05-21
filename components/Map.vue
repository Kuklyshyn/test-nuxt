<template>
  <div>
    <GMap
      ref="gMap"
      language="en"
      :center="{lat: locations[0].lat, lng: locations[0].lng}"
      :zoom="10"
    >
      <GMapMarker
        v-for="location in locations"
        :key="location.id"
        :position="{lat: location.lat, lng: location.lng}"
        :options="{icon: location.logo}"

      >
        <GMapInfoWindow :options="{maxWidth: 200}">
          <code>
            lat: {{ location.lat }},
            lng: {{ location.lng }}
          </code>
        </GMapInfoWindow>
      </GMapMarker>
    </GMap>
  </div>
</template>

<script>
export default {
  name: "Map",
  props: {
    locations: {
      type: Array,
      required: true
    }
  },
  data: () => ({
    currentLocation: {}
  })
}
</script>

<style scoped>

</style>
