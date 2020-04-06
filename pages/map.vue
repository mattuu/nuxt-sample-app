<template>
  <div class="container">
    <div>
      <h1>Map</h1>
      <GmapMap
        :center="{lat:10, lng:10}"
        :zoom="7"
        ref="mapRef"
        map-type-id="terrain"
        style="width: 1500px; height: 300px"
      >
        <GmapMarker
          :key="index"
          v-for="(m, index) in markers"
          :position="m.position"
          :clickable="true"
          :draggable="true"
          @click="center=m.position"
        />
      </GmapMap>
      <p>
        <NLink to="/" class="button--grey">Back home</NLink>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  asyncData () {
    return {
      markers: []
    }
  },
  mounted () {
    // At this point, the child GmapMap has been mounted, but
    // its map has not been initialized.
    // Therefore we need to write mapRef.$mapPromise.then(() => ...)
    // this.$refs.mapRef.$mapPromise.then((map) => {
    //   map.panTo({ lat: 1.38, lng: 103.8 })
    // })
  }
}
</script>
