<template>
  <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-12">
            <h2 class="text-center my-4">FORM KUNJUNGAN</h2>
            <form @submit.prevent="kirimData">
              <div class="mb-3">
                <input v-model="form.nama" type="text" class="form-control form control-lg rounded-5" placeholder="Nama..">
              </div>
    
              <div class="mb-3">
                <select v-model="
                form.keanggotaan" class="form-control form-control-lg form-select rounded-5">
                  <option value="">Keanggotaan</option>
                  <option v-for="(members, i) in member" :key="i" :value="members.id">{{ members.nama }}</option>
                </select>
              </div>
    
              <div class="mb-3" v-if="form.keanggotaan == '3'">
                <div class="row">
                  <div class="col-md-4">
                    <select v-model="form.tingkat" class="form-control form-control-lg form-select rounded-5 mb-2">
                      <option value="">Tingkat</option>
                      <option value="X">X</option>
                      <option value="XI">XI</option>
                      <option value="XII">XII</option>
                    </select>
                  </div>
    
                  <div class="col-md-4">
                    <select v-model="form.jurusan" class="form-control form-control-lg form-select rounded-5 mb-2">
                      <option value="">Jurusan</option>
                      <option value="PPLG">PPLG</option>
                      <option value="TJKT">TJKT</option>
                      <option value="TBSM">TBSM</option>
                      <option value="DKV">DKV</option>
                      <option value="TOI">TOI</option>
                    </select>
                  </div>
    
                  <div class="col-md-4">
                    <select v-model="form.kelas" class="form-control form-control-lg form-select rounded-5 mb-2">
                      <option value="">Kelas</option>
                      <option value="1">1</option>
                      <option value="2">2</option>
                      <option value="3">3</option>
                      <option value="4">4</option>
                    </select>
                  </div>
                </div>
              </div>
    
              <div class="mb-3 mt-3">
                <select v-model="form.keperluan" class="form-control form-control-lg form-select rounded-5">
                  <option value="">Keperluan</option>
                  <option v-for="(objek, i) in objektif" :key="i" :value="objek.id">{{ objek.keterangan }}</option>
                </select>
              </div>
    
              <div class="d-flex justify-content-between">
                <button type="submit" class="btn bg-primary btn-lg rounded-5 px-5 text-white">Kirim</button>
                <nuxt-link to="/" class="btn bg-warning btn-lg rounded-5 px-5 text-white">Kembali</nuxt-link>
              </div>
    
            </form>
          </div>
        </div>
      </div>
    </body>
  </html>
</template>

<script setup>

useHead({
  title:"Digitial Library Application",
  meta: [
    {
      name:"description",
      content:"Ini adalah halaman yang harus kamu isi pada saat mengunjungi Perpustakaan",
    }
  ]
})

const supabase = useSupabaseClient()

const member = ref([])
const objektif = ref([])

const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
})

const kirimData = async () => {
  // console.log(form.value)
  const {error} = await supabase.from('pengunjung').insert([form.value])
  if(!error) navigateTo('/pengunjung')
}

const getKeanggotaan = async () => {
  const {data, error} = await supabase.from('keanggotaan').select('*')
  if(data) member.value = data
}

const getKeperluan = async () => {
  const {data, error} = await supabase.from('keperluan').select('*')
  if(data) objektif.value = data
}

onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})

</script>

<style scoped>
.bg-primary {
  background-color: #516C84 !important;
  box-shadow: 1px 1px 10px #516C84;
}

.bg-warning {
  box-shadow: 1px 1px 10px #E4C72D;
}
</style>