<template>
  <b-modal id="modal-projects" size="lg" title="My Projects" hide-footer>
    <b-card no-body class="mb-3 overflow-hidden">
      <b-row no-gutters>
        <b-col md="6">
          <a href="https://getlonlat.com" target="_blank">
            <b-card-img src="getlonlat.png" alt="Image" class="rounded-0"></b-card-img>
          </a>
        </b-col>
        <b-col md="6">
          <b-card-body title="getLonLat">
            <b-card-text>
              Web app utility to get formated coordinates and
              <abbr
                title="Geohash is a latitude/longitude geocode system invented by Gustavo Niemeyer when writing the web service at geohash.org, and put into the public domain. It is a hierarchical spatial data structure which subdivides space into buckets of grid shape. Source: http://wiki.gis.com/wiki/index.php/Geohash">
                geohash
              </abbr>
              from map.
            </b-card-text>
            <a href="https://getlonlat.com" class="card-link" target="_blank">
              View project's page
            </a>
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>

    <b-card no-body class="mb-3 overflow-hidden">
      <b-row no-gutters>
        <b-col md="6">
          <a href="http://3.ondebus.com.br/map#/uberlandia">
            <b-card-img src="ondebus3.png" alt="Image" class="rounded-0"></b-card-img>
          </a>
        </b-col>
        <b-col md="6">
          <b-card-body title="OndeBus">
            <b-card-text>
              <p>
                Web app to know bus stop locations and routes from bus lines.
              </p>
              <p>
                This is a old project started many years ago and its development is stopped now...
              </p>
            </b-card-text>
            <a href="http://3.ondebus.com.br/map#/uberlandia" class="card-link" target="_blank">
              View project's page
            </a>
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>

    <b-card no-body class="overflow-hidden">
      <b-row no-gutters>
        <b-col md="6">
          <a href="https://chrome.google.com/webstore/detail/adicionar-lero-lero/mbgddfahdjkafkbokdlpkjckidbcgnfk">
            <b-card-img src="adicionar-lerolero.png" alt="Image" class="rounded-0"></b-card-img>
          </a>
        </b-col>
        <b-col md="6">
          <b-card-body title="Lero-Lero Generator">
            <b-card-text>
              Google Chrome extension to generate lero-lero (a.k.a. small
              talk) in Brazilian (PT-BR) to fill up form inputs.
            </b-card-text>
            <a href="https://chrome.google.com/webstore/detail/adicionar-lero-lero/mbgddfahdjkafkbokdlpkjckidbcgnfk"
              class="card-link" target="_blank">
              View extension's page
            </a>
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>
  </b-modal>
</template>
