<template>
  <div>
    <b-button v-b-modal.modal-projects variant="light"> My Projects </b-button>

    <b-modal id="modal-projects" size="xl" title="My Projects" hide-footer>
      <div class="row">
        <div class="col">
          <div class="card">
            <div class="card-body">
              <h4 class="card-title">getLonLat</h4>
              <p class="card-text">
                Web app utility to get formated coordinates and
                <abbr
                  title="Geohash is a latitude/longitude geocode system invented by Gustavo Niemeyer when writing the web service at geohash.org, and put into the public domain. It is a hierarchical spatial data structure which subdivides space into buckets of grid shape. Source: http://wiki.gis.com/wiki/index.php/Geohash"
                >
                  geohash
                </abbr>
                from map.
              </p>
              <a href="https://getlonlat.com" class="card-link" target="_blank">
                View project's page
              </a>
            </div>
            <a
              href="https://getlonlat.com"
              class="card-link"
              title="Click to visit the project page"
            >
              <img src="getlonlat.png" class="card-img-top" alt="" />
            </a>
          </div>
        </div>
        <div class="col">
          <div class="card">
            <div class="card-body">
              <h4 class="card-title">Lero-Lero Generator</h4>
              <p class="card-text">
                Google Chrome extension to generate lero-lero (a.k.a. small
                talk) in Brazilian (PT-BR) to fill up form inputs.
              </p>
              <a
                href="https://chrome.google.com/webstore/detail/adicionar-lero-lero/mbgddfahdjkafkbokdlpkjckidbcgnfk"
                class="card-link"
                target="_blank"
              >
                View extension's page
              </a>
              <a
                href="https://chrome.google.com/webstore/detail/adicionar-lero-lero/mbgddfahdjkafkbokdlpkjckidbcgnfk"
                class="card-link"
                title="Click to visit the extension page"
              >
                <img src="adicionar-lerolero.png" class="card-img-top" alt="" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </b-modal>
  </div>
</template>
