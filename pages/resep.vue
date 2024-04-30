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
              <h3>Kelola Resep</h3>
            </div>
            <div class="col-lg-2">
              <NuxtLink to="/tambahresep">
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
                <th>Tanggal Resep</th>
                <th>No Resep</th>
                <th>Nama Dokter</th>
                <th>Nama Pasien</th>
                <th>Obat Resep</th>
                <th>Jumlah</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(resep, i) in Resep" :key="i">
                <th>{{ i + 1 }}</th>
                <td>{{ resep.Tgl_Resep }}</td>
                <td>{{ resep.No_Resep }}</td>
                <td>{{ resep.Nama_Dokter }}</td>
                <td>{{ resep.Nama_Pasien }}</td>
                <td>{{ resep.Obat_Resep }}</td>
                <td>{{ resep.Jumlah }}</td>
          
             
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

const Resep = ref([])

const getResep = async() => {
  const {data} = await supabase.from("Tbl_DataResep").select("*")
  if (data) Resep.value = data
}

onMounted(() => {
  getResep()
})
</script>
