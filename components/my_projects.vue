<template>
  <div>
    <b-button v-b-modal.modal-projects variant="light">
      My Projects
    </b-button>

    <b-modal id="modal-projects" size="xl" title="Projects" hide-footer>
      <div class="row">
        <div class="col">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">getLonLat</h5>
              <p class="card-text">App utility to get coordinates from map.</p>
              <a href="https://getlonlat.com" class="card-link" target="_blank">
                View project's page
              </a>
            </div>
            <a href="https://getlonlat.com" class="card-link" title="Click to visit the project page" target="_blank">
              <img src="getlonlat.png" class="card-img-top" alt="">
            </a>
          </div>
        </div>
        <div class="col">
          <div class="card">

            <div class="card-body">
              <h5 class="card-title">Lero-Lero Generator</h5>
              <p class="card-text">
                Google Chrome extension to generate lero-lero (a.k.a. small talk) in Brazilian (PT-BR) to
                fill up form inputs.
              </p>
              <a href="https://chrome.google.com/webstore/detail/adicionar-lero-lero/mbgddfahdjkafkbokdlpkjckidbcgnfk"
                class="card-link" target="_blank">
                View extension's page
              </a>
              <a href="https://chrome.google.com/webstore/detail/adicionar-lero-lero/mbgddfahdjkafkbokdlpkjckidbcgnfk"
                class="card-link" title="Click to visit the extension page" target="_blank">
                <img src="adicionar-lerolero.png" class="card-img-top" alt="">
              </a>
            </div>
          </div>
        </div>
      </div>
    </b-modal>
  </div>
</template>
