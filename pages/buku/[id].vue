<template>
  <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-2">
            <nuxt-link to="../buku" class="btn bg-warning btn-lg rounded-5 px-5 text-white mt-3">Kembali</nuxt-link>
            <h3 class="mt-3">DETAIL BUKU</h3>
            <div class="card mt-5">
              <div class="card-body">
                <span v-if="loading">Loading....</span>
                <span v-else>
                  <img :src="buku.cover" alt="cover" class="cover" />
                </span>
                <!-- <img :src="buku.cover" alt="cover" class="cover">  -->
              </div>
            </div>
          </div>
          <div class="col-lg-4" style="margin-top: 155px">
            <!-- <h2 class="text-start my-4">
                {{ buku.judul }}
              </h2> -->
            <div class="row">
              <!-- <div class="col-md-3">
                  
                </div> -->
              <!-- <div class="col-md-6">
                  <div class="badge bg-primary p-2">
                    {{ buku.kategori }}
                  </div>
                </div> -->
              <ul class="list-group list-group-flush">
                <li class="list-group-item">Judul Buku : {{ buku.judul }}</li>
                <li class="list-group-item">
                  <span v-if="buku.kategori">
                    Kategori : {{ buku.kategori.nama }}
                  </span>
                </li>
                <li class="list-group-item">
                  <span v-if="buku.rak">
                    No Rak : {{ buku.rak.kode }}
                  </span>
                </li>
                <li class="list-group-item">Penulis : {{ buku.penulis }}</li>
                <li class="list-group-item">Penerbit : {{ buku.penerbit }}</li>
                <li class="list-group-item">Tahun Terbit : {{ buku.tahun_terbit }}</li>
                <li class="list-group-item">Deskripsi : {{ buku.deskripsi }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </body>
  </html>  
</template>

<script setup>
const supabase = useSupabaseClient();

const route = useRoute();

const buku = ref([]);

const loading = ref(true);

const getBukuById = async () => {
  loading.value = true;
  const { data, error } = await supabase.from("buku")
  .select(`*, kategori(nama), rak(kode)`)
  .eq("id", route.params.id);
  if (data) {
    buku.value = data[0];
    loading.value = false;
  }
};

onMounted(() => {
  getBukuById();
});
</script>

<style scoped>
.cover {
  width: 100%;
}
/* .card-body {
  width: 100%;
  height: 100%;
  padding: 0;
  box-shadow: 1px 1px 5px black;  
} */
.bg-warning {
  box-shadow: 1px 1px 10px #e4c72d;
}
</style>
