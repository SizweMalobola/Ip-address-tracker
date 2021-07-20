<script>
  import L from "leaflet";
  import { onMount } from "svelte";
  export let lat;
  export let lng;
  export let zoom;

  let map;
  let marker;
  onMount(() => {
    map = L.map("map").setView([lat, lng], zoom);
    L.tileLayer("https://a.tile.openstreetmap.org/{z}/{x}/{y}.png ", {
      attribution:
        'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>',
    }).addTo(map);
    marker = L.marker([lat, lng]).addTo(map);
  });
  $: if (lat) {
    map.setView([lat, lng], 12);
    marker.setLatLng([lat, lng]);
  }
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
    integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A=="
    crossorigin=""
  />
</svelte:head>

<div id="map" />

<style>
  #map {
    height: 70vh;
    width: 100%;
    padding: 0;
    margin: 0;
    z-index: 0;
  }
</style>
