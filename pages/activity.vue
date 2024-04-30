<template>
  <div>
    <div class="row bg-all">
      <div class="col-lg-2 nav">
        <Navbar />
      </div>
      <div class="col-lg-10">
        <div class="card">
          <div class="row">
            <div class="col-lg-4">
              <h3>Log Activity</h3>
            </div>
         
          </div>
          <table class="table">
            <thead>
              <tr>
                <th>Id</th>
                <th>Tanggal</th>
                <th>Waktu</th>
                <th>Aktivitas</th>
                <th>Username</th>
                <th>Tipe User</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(log, i) in Activity" :key="i">
                <th>{{ i + 1 }}</th>
                <td>{{ log.Tanggal }}</td>
                <td>{{ log.Waktu }}</td>
                <td>{{ log.Aktivitas }}</td>
                <td>{{ log.username }}</td>
                <td>{{ log.tipe_user }}</td>
             
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

const Activity = ref([])

const getObat = async() => {
  const {data} = await supabase.from("Tbl_LogActivity").select("*")
  if (data) Activity.value = data
}

onMounted(() => {
  getObat()
})
</script>
