<script>
  import { onMount } from "svelte";
  import LeafletMap from "./components/LeafletMap.svelte";
  import LeafletMarker from "./components/LeafletMarker.svelte";
  let data;
  onMount(async () => {
    const res = await fetch(
      "https://geo.ipify.org/api/v1?apiKey=at_yD3vEaoAvXcwTfz6Dtskb3YdADme8&ipAddress="
    );
    data = await res.json();
  });
</script>

<main id="main-container">
  <header>
    <h1>IP Adress Traker</h1>
    <div id="content">
      <div id="search-bar">
        <input type="text" placeholder="Search for any IP address" />
        <button>&RightAngleBracket;</button>
      </div>
      <!-- display details -->
      <div id="api-details">
        <div>
          <span>ip address</span>
          <h3>
            {#if data}
              {data.ip}
            {:else}
              192.212.174.101
            {/if}
          </h3>
        </div>
        <div>
          <span>Location</span>
          <h3>
            {#if data}
              {data.location.country},{data.location.city}
            {:else}
              Brooklyn,NY 10001
            {/if}
          </h3>
        </div>
        <div>
          <span>Timezone</span>
          <h3>
            {#if data}
              {data.location.timezone}
            {:else}
              UTC-05:00
            {/if}
          </h3>
        </div>
        <div>
          <span>ISP</span>
          <h3>
            {#if data}
              {data.as.name}
            {:else}
              SpaceX Starlink
            {/if}
          </h3>
        </div>
      </div>
    </div>
  </header>
  <LeafletMap>
    <!-- <LeafletMarker lat="40" lng="-3" /> -->
  </LeafletMap>
</main>

<style>
  @media (min-width: 320px) {
    :global(body) {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }
    #main-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      height: 100%;
    }
    header {
      z-index: 1;
      background-image: linear-gradient(80deg, blue 50%, rgb(15, 15, 172));
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      max-height: 200px;
    }
    #content {
      width: 80%;
    }
    #search-bar {
      width: 100%;
      max-width: 400px;
      position: relative;
      margin: 0 auto;
      margin-bottom: 1rem;
    }
    #search-bar > input {
      width: 85%;
      padding: 0.5em;
      border: 1px solid black;
      border-top-left-radius: 12px;
      border-bottom-left-radius: 12px;
      font-weight: 600;
    }
    #search-bar > input:focus {
      outline: none;
    }

    #search-bar button {
      position: absolute;
      top: 0;
      right: 0;
      height: 100%;
      width: 15%;
      border: 1px solid black;
      border-top-right-radius: 12px;
      border-bottom-right-radius: 12px;
      background-color: black;
      color: whitesmoke;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 1rem;
    }
    #api-details {
      background-color: whitesmoke;
      color: black;
      border-radius: 12px;
      padding: 1em;
      text-align: center;
      box-shadow: gray 1px 2px 4px;
    }
    #api-details > div {
      margin-bottom: 0;
      padding: 0;
      display: block;
      margin-bottom: 0.6em;
    }
    #api-details > div span {
      display: inline-block;
      margin-bottom: 0.4em;
      font-size: 0.7rem;
      text-transform: uppercase;
      color: gray;
    }
    #api-details > div h3 {
      margin: 0;
      text-transform: capitalize;
      font-size: 1.1rem;
    }
  }
  @media (min-width: 360px) {
    header {
      max-height: 250px;
    }
    #search-bar {
      margin-bottom: 1.5rem;
    }
    #search-bar > input {
      padding: 0.9em;
    }
    #api-details {
      padding: 1.5em;
    }
    #api-details > div {
      margin-bottom: 0.8em;
    }
    #api-details > div span {
      font-size: 0.8rem;
    }
    #api-details > div h3 {
      font-size: 1.2rem;
    }
  }
  @media (min-width: 768px) {
    #main-container {
      max-width: 1024px;
      height: 90%;
    }
    header {
      max-height: 200px;
    }
    header > h1 {
      font-size: 2.4rem;
    }
    #content {
      width: 100%;
      max-width: 800px;
    }
    #search-bar {
      width: 55%;
      margin: 0 auto;
      margin-bottom: 1.5em;
    }
    #search-bar > input {
      font-size: 1rem;
    }
    #api-details {
      text-align: left;
      display: flex;
      justify-content: space-around;
      padding: 1.2em 0;
    }
    #api-details > div:not(:first-child) {
      padding-left: 1em;
      border-left: 1px solid gray;
    }
  }
  @media (min-width: 1024px) {
    #main-container {
      height: 80%;
    }
  }
</style>
