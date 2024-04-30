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
              <h3>Transaksi</h3>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-6">
              <NuxtLink to="/tnonresep">
                <div class="card border"><h2>Non Resep</h2></div>
              </NuxtLink>
            </div>
            <div class="col-lg-6">
              <NuxtLink to="/tresep">
                <div class="card border"><h2>Resep</h2></div>
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
</script>
