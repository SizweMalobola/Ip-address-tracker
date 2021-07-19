<script>
  import L from "leaflet";
  import { setContext, onMount } from "svelte";
  let map;
  onMount(() => {
    map = L.map("map").setView([-25.74486, 28.18783], 13);
    L.tileLayer("https://a.tile.openstreetmap.org/{z}/{x}/{y}.png ", {
      attribution:
        'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>',
    }).addTo(map);
  });
  setContext("leafletMapInstance", map);
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
    integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A=="
    crossorigin=""
  />
</svelte:head>
<div id="map">
  <slot />
</div>

<style>
  #map {
    height: 70vh;
    width: 100%;
    padding: 0;
    margin: 0;
    z-index: 0;
  }
</style>
