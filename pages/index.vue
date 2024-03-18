<template>
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-3 mt-5">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-3 mt-5">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <h2 class="Statistik mt-5">
        STATISTIK
      </h2>

      <div class="col-lg-6">
        <div class="card kunjungan rounded-3 mt-5">
          <div class="card-body d-flex align-items-center">
            <h1>5</h1>
            <h2 class="pt-5">Pengunjung</h2>
          </div>
        </div>
      </div>

      <div class="col-lg-6">
        <div class="card buku rounded-3 mt-5">
          <div class="card-body d-flex align-items-center">
            <h1>200</h1>
            <h2 class="pt-5">Buku</h2>
          </div>
        </div>
      </div>
    </div>
    <Chart />
  </div>
</template>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #516C84;
}
.card.bg-pengunjung {
  background: url('../assets/img/bg-kunjungan.jpeg') no-repeat center center;
  background-size: cover;
  opacity: 50%;
  
}
.card.bg-buku {
  background: url('../assets/img/bg-buku.jpg') no-repeat center center;
  background-size: cover;
  opacity: 50%;
}
.card.kunjungan {
  background-color: #E4C72D;
}
.card.buku {
  background-color: #86E996;
}
h1 {
  font-size: 7rem;
}
.Statistik {
  margin-left: 0px;
  font-weight: bold;
}
</style>
