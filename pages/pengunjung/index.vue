<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">DAFTAR RIWAYAT KUNJUNGAN</h2>
        <nuxt-link to="/" class="btn bg-warning btn-lg rounded-5 px-5 text-white mt-3">Kembali</nuxt-link>
        <div class="my-3">
          <input type="search" class="form-control form-control-lg rounded-5" placeholder="Filter...">
        </div>

        <div class="my-3 text-muted">Menampilkan 1 dari 1</div>

        <table class="table">
          <thead>
            <tr>
              <td>#</td>
              <td>Nama</td>
              <td>Keanggotaan</td>
              <td>Waktu</td>
              <td>Keperluan</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>1.</td>
              <td>Arunika</td>
              <td>Siswa</td>
              <td>27 Februari 2024, 09.22.13</td>
              <td>Baca</td>
            </tr>
          </tbody>
        </table>

      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-warning {
  box-shadow: 1px 1px 10px #E4C72D;
}
</style>