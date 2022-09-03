<template>
  <div>
    <b-button v-b-modal.modal-1 variant="light"> Projects </b-button>

    <b-modal id="modal-1" title="Projects" hide-footer>
      <div class="card">
        <img src="getlonlat.png" class="card-img-top" alt="getLonLat screenshot" />
        <div class="card-body">
          <h5 class="card-title">getLonLat</h5>
          <p class="card-text">App utility to get coordinates from map.</p>
        </div>
        <div class="card-body">
          <a href="https://getlonlat.github.io/" class="card-link">
            View project's page
          </a>
        </div>
      </div>
    </b-modal>
  </div>
</template>
