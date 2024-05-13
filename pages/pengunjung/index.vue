<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">DAFTAR RIWAYAT KUNJUNGAN</h2>
        <nuxt-link to="../pengunjung/tambah" class="btn bg-warning btn-lg rounded-5 px-5 text-white mt-3">Kembali</nuxt-link>
        <div class="my-3">
          <form @submit.prevent="getPengunjung">
            <input v-model= "keyword" type="search" class="form-control form-control-lg rounded-5" placeholder="Filter..." />
          </form>
        </div>

        <div class="my-3 text-muted">Menampilkan {{ visitors.length }} dari {{ total }}</div>

        <table class="table">
          <thead>
            <tr>
              <td>No</td>
              <td>Nama</td>
              <td>Keanggotaan</td>
              <td>Tanggal</td>
              <td>Keperluan</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tanggal }}</td>
              <td>{{ visitor.keperluan.keterangan }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const keyword = ref('');

const visitors = ref([]);

const total = ref([]);

const getPengunjung = async () => {
  const { data, error } = await supabase.from("pengunjung")
  .select(`*, keanggotaan(*), keperluan(*)`)
  .ilike('nama' , `%${keyword.value}`)
  .order("id", { ascending: false });
  if (data) visitors.value = data;
};

const banyakPengunjung = async () => {
  const { data, count } = await supabase.from("pengunjung").select(`*`, { count: "exact" });
  if (data) total.value = count;
};

onMounted(() => {
  getPengunjung();
  banyakPengunjung();
});
</script>

<style scoped>
.bg-warning {
  box-shadow: 1px 1px 10px #e4c72d;
}
</style>
