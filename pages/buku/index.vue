<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
          <nuxt-link to="/" class="btn bg-warning btn-lg rounded-5 px-5 text-white mt-3">Kembali</nuxt-link>
            <div class="my-3">
              <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
            </div>

            <div class="my-3 text-muted">Menampilkan 4 dari 4</div>
            <div class="row">
              <div class="col-lg-2">
                <div class="card mb-3">
                  <div class="card-body">
                    <img src="~/assets/img/lautbercerita.jpeg" alt="cover1" class="cover">
                  </div>
                </div>
              </div>

              <div class="col-lg-2">
                <div class="card mb-3">
                  <div class="card-body">
                    <img src="~/assets/img/ephujan.jpg" alt="cover2" class="cover">
                  </div>
                </div>
              </div>

              <div class="col-lg-2">
                <div class="card mb-3">
                  <div class="card-body">
                    <img src="~/assets/img/bsi.jpg" alt="cover3" class="cover">
                  </div>
                </div>
              </div>
          </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-body {
  /* width: 100%;
  height: 100%;
  padding: 0; */
  box-shadow: 1px 1px 5px black;  
}
.cover {
  width: 100%;
  
}
.bg-warning {
  box-shadow: 1px 1px 10px #E4C72D;
}
</style>  