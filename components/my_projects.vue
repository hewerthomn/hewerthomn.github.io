<template>
  <div>
    <b-button v-b-modal.modal-projects variant="light">
      My Projects
    </b-button>

    <b-modal id="modal-projects" title="Projects" hide-footer>
      <div class="card">
        <img src="getlonlat.png" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">getLonLat</h5>
          <p class="card-text">App utility to get coordinates from map.</p>
          <a href="https://getlonlat.github.io/" class="card-link">
            View project's page
          </a>
        </div>
      </div>
    </b-modal>
  </div>
</template>
