<template>
  <div>
    <div class="row bg-all">
      <div class="col-lg-2">
        <Navbar />
      </div>
      <div class="col-lg-10">
        <div class="card">
          <div class="row">
            <div class="col-lg-4">
              <h3>Kelola Obat</h3>
            </div>
            <div class="col-lg-2">
              <NuxtLink to="/tambahobat">
                <button type="submit" class="btn bg-primary text-light">
                  Tambah
                </button>
              </NuxtLink>
            </div>
          </div>
          <table class="table">
            <thead>
              <tr>
                <th>Id</th>
                <th>Kode Obat</th>
                <th>Nama Obat</th>
                <th>Expired Date</th>
                <th>Jumlah</th>
                <th>Harga</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(obat, i) in Obat" :key="i">
                <th>{{ i + 1 }}</th>
                <td>{{ obat.Kode_Obat }}</td>
                <td>{{ obat.Nama_Obat }}</td>
                <td>{{ obat.Expired_Date }}</td>
                <td>{{ obat.Jumlah }}</td>
                <td>{{ obat.Harga }}</td>
             
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const Obat = ref([])

const getObat = async() => {
  const {data} = await supabase.from("Tbl_Obat").select("*")
  if (data) Obat.value = data
}

onMounted(() => {
  getObat()
})
</script>
