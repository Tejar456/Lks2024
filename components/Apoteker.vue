<template>
  <div>
    <div class="side bg-primary">
      <div class="logo">
        <img src="~/assets/logo.png" alt="" />
        <h6 class="text-light">Apotek XYZ</h6>
      </div>
      <div class="navigasi">
        <NuxtLink to="/obat">
          <p>Kelola Obat</p>
        </NuxtLink>
        <NuxtLink to="/resep">
          <p>Kelola Resep</p>
        </NuxtLink>
      </div>
      <div class="logout">
        <NuxtLink to="/logout">
          <button class="btn btn-light">Logout</button>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
.side {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  position: fixed;
  top: 0px;
}

.logo {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 20px;
}

.logo img {
  width: 40%;
}

.navigasi p {
  color: #ffffff;
}
</style>
