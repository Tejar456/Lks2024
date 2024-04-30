<template>
  <div>
    <div class="row bg-all">
      <div class="col-lg-2">
        <Navbar />
      </div>
      <div class="col-lg-10">
        <div class="card">
          <div class="row">
            <div class="col-lg-12">
              <h3>Tambah Resep</h3>
            </div>
          </div>
          <form @submit.prevent="tambahResep">
            <div class="mb-3">
              <input
                v-model="form.No_Resep"
                type="text"
                class="form-control"
                placeholder="No Resep"
              />
            </div>

            <div class="mb-3">
              <input
                v-model="form.Nama_Dokter"
                type="text"
                class="form-control"
                placeholder="Nama Dokter"
              />
            </div>
            <div class="mb-3">
              <input
                v-model="form.Nama_Pasien"
                type="text"
                class="form-control"
                placeholder="Nama Pasien"
              />
            </div>
            <div class="mb-3">
              <select v-model="form.Obat_Resep"  class="form-select">
                  <option value="">Obat</option>
                  <option v-for="(obat) in Obat"  :value="obat.Nama_Obat">{{  obat.Nama_Obat }}</option>
                </select>
            </div>
            <div class="mb-3">
              <input
                v-model="form.Jumlah_Obat"
                type="number"
                class="form-control"
                placeholder="Jumlah"
              />
            </div>

            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const form = ref({
  No_Resep: "",
  Nama_Dokter: "",
  Nama_Pasien: "",
  Obat_Resep: "",
  Jumlah_Obat: "",
});

const tambahResep = async () => {
  const { error } = await supabase.from("Tbl_DataResep").insert([form.value]);
  if (!error) {
    navigateTo("/resep");
  }
};

const Obat = ref([])

const getObat = async() => {
  const {data} = await supabase.from("Tbl_Obat").select("*")
  if (data) Obat.value = data
}

onMounted(() => {
  getObat()
})
</script>
