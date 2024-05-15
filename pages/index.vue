<template>
  <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
      <div class="container-fluid">
        <div class="row my-5">
          <div class="col-lg-6">
            <nuxt-link to="/pengunjung/tambah">
              <div class="card bg-kunjungan rounded-4">
                <div class="card-body">
                  <h2>Pengunjung</h2>
                </div>
              </div>
            </nuxt-link>
          </div>
    
          <div class="col-lg-6">
            <nuxt-link to="/buku">
              <div class="card bg-buku rounded-4">
                <div class="card-body">
                  <h2>Cari Buku</h2>
                </div>
              </div>
            </nuxt-link>
          </div>
    
          <h2 class="Statistik mt-5">STATISTIK</h2>
    
          <div class="col-lg-6">
            <nuxt-link to="/pengunjung">
              <div class="card kunjungan rounded-4">
                <div class="card-body d-flex align-items-center">
                  <h1>{{ pengunjung }}</h1>
                  <h2 class="pt-5">Pengunjung</h2>
                </div>
              </div>
            </nuxt-link>
          </div>
    
          <div class="col-lg-6">
            <!-- <nuxt-link to="/buku"> -->
            <div class="card buku rounded-4">
              <div class="card-body d-flex align-items-center">
                <h1>{{ buku }}</h1>
                <h2 class="pt-5">Buku</h2>
              </div>
            </div>
            <!-- </nuxt-link> -->
          </div>
        </div>
        <div class="container">
          <Chart />
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
      content:"Home Page"
    }
  ]
})

const supabase = useSupabaseClient();

const pengunjung = ref(0);

const buku = ref(0);

const totalPengunjung = async () => {
  const { data, error, count } = await supabase.from("pengunjung").select("*", { count: "exact" });
  if (count) pengunjung.value = count;
};

const totalBuku = async () => {
  const { data, error, count } = await supabase.from("buku").select("*", { count: "exact" });
  if (count) buku.value = count;
};

onMounted(() => {
  totalPengunjung();
  totalBuku();
});
</script>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #516c84;
}
.card.bg-kunjungan {
  background: url("../assets/img/bg-kunjungan.webp") no-repeat center center;
  background-size: cover;
  opacity: 50%;
  margin-top: 5%;
}
.card.bg-buku {
  background: url("../assets/img/bg-buku.webp") no-repeat center center;
  background-size: cover;
  opacity: 50%;
  margin-top: 5%;
}
.card.kunjungan {
  background-color: #e4c72d;
  margin-top: 5%;
}
.card.buku {
  background-color: #86e996;
  margin-top: 5%;
}
h1 {
  font-size: 7rem;
}
.Statistik {
  margin-left: 0px;
  font-weight: bold;
}
</style>
