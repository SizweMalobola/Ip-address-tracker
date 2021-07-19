<script>
  import L from "leaflet";
  import { setContext, onMount } from "svelte";
  let mapContainer;
  let map = L.map(L.DomUtil.create("div"), { center: [0, 0], zoom: 0 });
  setContext("leafletMapInstance", map);
  console.log("map", map);

  L.tileLayer(
    "https://api.mapbox.com/styles/v1/mapbox/streets-v11/static/-122.4241,37.78,15.25,0,60/400x400?access_token=pk.eyJ1Ijoic2hyaXZlbGVkLXNhY2siLCJhIjoiY2tyYWJidmpiMWZwYTJwbHA2cTI3a2E4NiJ9.dqQivOrTkGJUZCD5P1iDAA",
    {
      attribution:
        'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
    }
  ).addTo(map);
  onMount(() => {
    mapContainer.appendChild(map.getContainer());
    map.getContainer().style.width = "100%";
    map.getContainer().style.height = "100%";
    map.invalidateSize();
  });
</script>

<div class="map" bind:this={mapContainer}>
  <slot />
</div>

<style>
  .map {
    height: 100%;
    width: 100%;
  }
</style>
