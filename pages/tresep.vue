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
          <form>
         
            <div class="mb-3">
              <input class="form-control" type="text" placeholder="No Resep" />
            </div>
            <div class="mb-3">
                <select  class="form-select">
                <option value="">Obat</option>
                <option v-for="(obat) in Obat" >{{  obat.Nama_Obat }}</option>
              </select>
            </div>
            <div class="mb-3">
              <input class="form-control" type="number" placeholder="Harga" />
            </div>
            <div class="mb-3">
              <input class="form-control" type="number" placeholder="Jumlah" />
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
  const Obat = ref([])

  const getObat = async() => {
    const {data} = await supabase.from("Tbl_Obat").select("*")
    if (data) Obat.value = data
  }

  onMounted(() => {
    getObat()
  })
</script>
