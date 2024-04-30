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
          <form @submit.prevent="tambahTransaksi">
            
            <div class="mb-3">
              <select v-model="Harga"  class="form-select">
                <option value="">Obat</option>
                <option v-for="(obat) in Obat"  :value="obat.Harga">{{  obat.Nama_Obat }}</option>
              </select>
            </div>
            <div class="mb-3">
              <input class="form-control" type="number" v-model="Harga" placeholder="Harga" readonly>
            </div>
            <div class="mb-3">
              <input class="form-control" type="number" v-model="Quantity" placeholder="Jumlah">
            </div>

            <button type="submit" class="btn btn-primary">Submit</button>

            Rp {{ Total_Bayar }}
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const Harga = ref("")
const Quantity = ref("")
const Total_Bayar = computed(() => Harga.value * Quantity.value )
const Obat = ref([])


const tambahTransaksi = async() => {
  const { error } = await supabase.from("Tbl_Transaksi").insert({
    Quantity : Quantity.value,
    Total_Bayar : Total_Bayar.value,
  })
  if (!error) {
    navigateTo("/laporan")
  }
}

const getObat = async() => {
  const {data} = await supabase.from("Tbl_Obat").select("*")
  if (data) Obat.value = data
}

onMounted(() => {
  getObat()
})
</script>
