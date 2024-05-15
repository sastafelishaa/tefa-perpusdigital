<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <nuxt-link to="/" class="btn bg-warning btn-lg rounded-5 px-5 text-white mt-3">Kembali</nuxt-link>
          <div class="my-3">
            <form @submit.prevent="getBuku">
              <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
            </form>
          </div>

          <div class="my-3 text-muted">Menampilkan {{ buku.length }} dari {{ total }}</div>
          <div class="row">
            <div v-for="(book, i) in buku" :key="i" class="col-lg-2">
              <nuxt-link :to="`buku/${book.id}`">
                <div class="card mb-3">
                  <div class="card-body">
                    <img :src="book.cover" class="cover" alt="cover" />
                  </div>
                </div>
              </nuxt-link>
            </div>
          </div>

      </div>
    </div>
  </div>
      

</template>

<script setup>

useHead({
  title:"Digitial Library Application",
  meta: [
    {
      name:"description",
      content:"Ini adalah halaman cari buku dimana kamu bisa melihat buku yang terdapat di Perpustakaan",
    }
  ]
})

const supabase = useSupabaseClient()

const buku = ref([])

const keyword = ref('')

const total = ref([])

const getBuku = async () => {
  const {data, error} = await supabase.from('buku').select(`*, kategori(nama), rak(kode)`)
  .ilike('judul', `%${keyword.value}%`)
  if(data) buku.value = data
}
const banyakBuku = async () => {
  const { data, count } = await supabase.from('buku').select(`*`, { count: "exact" });
  if (data) total.value = count;
};

onMounted(() =>{
  getBuku()
  banyakBuku()
})
</script>

<style scoped>
.card-body {
  /* width: 100%;
  height: 20rem;
  padding: 0; */
  box-shadow: 1px 1px 5px black;  
}
.cover {
  width: 100%;
  /* height: 100%; */
  object-fit: cover;
  object-position: 0;
  
}
.bg-warning {
  box-shadow: 1px 1px 10px #E4C72D;
}
</style>  