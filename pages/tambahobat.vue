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
              <h3>Tambah Obat</h3>
            </div>
          </div>
          <form @submit.prevent="tambahObat">
            <div class="mb-3">
              <input v-model="form.Kode_Obat" type="text" class="form-control" placeholder="Kode Obat" />
            </div>
            <div class="mb-3">
              <input v-model="form.Nama_Obat" type="text" class="form-control" placeholder="Nama Obat" />
            </div>
            <div class="mb-3">
                <label for="">Expired Date</label>
              <input v-model="form.Expired_Date" type="date" class="form-control"  />
            </div>
            <div class="mb-3">
              <input v-model="form.Jumlah" type="number" class="form-control" placeholder="Jumlah" />
            </div>
            <div class="mb-3">
              <input v-model="form.Harga" type="number" class="form-control" placeholder="Harga" />
            </div>

            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
          
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const form = ref ({
  Kode_Obat:"",
  Nama_Obat:"",
  Expired_Date:"",
  Jumlah:"",
  Harga:"",
})


const tambahObat = async() => {
  const { data} = await supabase.from("Tbl_Obat").insert([form.value])
  if (data) {
    navigateTo("/obat")
  }
}
</script>
