<template>
  <div>
    <div class="row">
      <div class="col-lg-2">
        <Navbar />
      </div>
      <div class="col-lg-10">
        <div class="text">
          <h2>
            Hello {{ username }} Selamat Datang Di Aplikasi Apotek XYZ
            {{ tipe_user }}
          </h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const user = useSupabaseUser();

const tipe_user = user.value.user_metadata.tipe_user;
const username = user.value.user_metadata.username;
</script>


<style scoped>
.text {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>