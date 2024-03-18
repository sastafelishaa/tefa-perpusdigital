<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">FORM KUNJUNGAN</h2>
        <form>
          <div class="mb-3">
            <input type="text" class="form-control form control-lg rounded-5" placeholder="Nama..">
          </div>

          <div class="mb-3">
            <select class="form-control form-control-lg form-select rounded-5">
              <option value="">Keanggotaan</option>
              <option value="Siswa">Siswa</option>
              <option value="Guru">Guru</option>
              <option value="Staf">Staf</option>
              <option value="Umum">Umum</option>
            </select>
          </div>

          <div class="mb-3">
            <div class="row">
              <div class="col-md-4">
                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">Tingkat</option>
                  <option value="X">X</option>
                  <option value="XI">XI</option>
                  <option value="XII">XII</option>
                </select>
              </div>

              <div class="col-md-4">
                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">Jurusan</option>
                  <option value="PPLG">PPLG</option>
                  <option value="TJKT">TJKT</option>
                  <option value="TBSM">TBSM</option>
                  <option value="DKV">DKV</option>
                  <option value="TOI">TOI</option>
                </select>
              </div>

              <div class="col-md-4">
                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">Kelas</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                </select>
              </div>

              <div class="mb-3 mt-3">
                <select class="form-control form-control-lg form-select rounded-5">
                  <option value="">Keperluan</option>
                  <option value="baca">Membaca</option>
                  <option value="pinjam">Meminjam</option>
                  <option value="kembali">Mengembalikan</option>
                </select>
              </div>

              <div class="d-flex justify-content-between">
                <nuxt-link to="../pengunjung" class="btn bg-primary btn-lg rounded-5 px-5 text-white">Kirim</nuxt-link>
                <nuxt-link to="/" class="btn bg-warning btn-lg rounded-5 px-5 text-white">Kembali</nuxt-link>
              </div>
              
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-primary {
  background-color: #516C84 !important;
  box-shadow: 1px 1px 10px #516C84;
}

.bg-warning {
  box-shadow: 1px 1px 10px #E4C72D;
}
</style>