<script>
</script>

<main id="main-container">
  <header>
    <h1>IP Adress Traker</h1>
    <div id="content">
      <div id="search-bar">
        <input type="text" />
        <button>&RightAngleBracket;</button>
      </div>
      <!-- display details -->
      <div id="api-details">
        <div>
          <span>ip address</span>
          <h3>192.212.174.101</h3>
        </div>
        <div>
          <span>Location</span>
          <h3>Brooklyn, NY 100001</h3>
        </div>
        <div>
          <span>Timezone</span>
          <h3>UTC -05:00</h3>
        </div>
        <div>
          <span>ISP</span>
          <h3>SpaceX Starlink</h3>
        </div>
      </div>
    </div>
  </header>
  <div id="map" />
</main>

<style>
  @media (min-width: 320px) {
    #main-container {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    header {
      background-image: linear-gradient(80deg, blue 50%, rgb(248, 248, 248));
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
      position: relative;
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
      /* background-color: darkcyan; */
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
</style>
