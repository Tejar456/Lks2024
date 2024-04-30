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
              <h3>Laporan</h3>
            </div>
          </div>
          <table class="table">
            <thead>
              <tr>
                <th>Id</th>
                <th>No Transaksi</th>
                <th>Tanggal Transaksi</th>
                <th>Total Bayar</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(trx, i) in Transaksi" :key="i">
                <th>{{ i + 1 }}</th>
                <td>{{ trx.No_Transaksi }}</td>
                <td>{{ trx.Tgl_Transaksi }}</td>
                <td>{{ trx.Total_Bayar }}</td>
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

const Transaksi = ref([]);

const getData = async () => {
  const { data } = await supabase.from("Tbl_Transaksi").select("*");
  if (data) Transaksi.value = data;
};

onMounted(() => {
  getData();
});
</script>
