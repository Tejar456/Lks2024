<template>
  <div>
    <div class="row">
      <div class="col-lg-3">
        <div class="side bg-primary">
          <div class="logo">
            <img src="~/assets/logo.png" alt="" />
          </div>
          <div class="text-center text-light">
            <h2>Apotek XYZ</h2>
          </div>
        </div>
      </div>
      <div class="col-lg-9">
        <div class="form">
          <div class="card">
            <h2>Login Form</h2>
            <form @submit.prevent="Login">
              <div class="mb-3">
                <input
                  type="email"
                  class="form-control"
                  placeholder="Email"
                  aria-describedby="emailHelp"
                  v-model="email"
                />
              </div>
              <div class="mb-3">
                <input
                  type="password"
                  class="form-control"
                  placeholder="Password"
                  v-model="password"
                />
              </div>

              <button type="submit" class="btn btn-primary">Submit</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div> 
</template>

<script setup>
const supabase = useSupabaseClient()

const email = ref("")
const password = ref("")

const Login = async() => {
  const { data , error } = await supabase.auth.signInWithPassword({
    email: email.value,
    password: password.value,
  })
  if (data) {
    navigateTo("/")
    const user = useSupabaseUser()
    insertLog(user)
  }
}


async function insertLog(user) {
  const { data } = await supabase.from("Tbl_LogActivity").insert([
    {
    Aktivitas: "Login",
    username: user.value.user_metadata.username,
    nama: user.value.user_metadata.username,
    tipe_user: user.value.user_metadata.tipe_user,
  }
])
}

</script>

<style scoped>
.row {
  background-color: #f5f5f5;
}
.side {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.logo img {
  width: 75%;
}
.logo {
  display: flex;
  justify-content: center;
  align-items: center;
}

.form {
    display: flex;
    justify-content: center;
   align-items: center;
   height: 100vh;
}

.card {
  border: none;
  border-radius: 25px;
  padding: 30px;
  width: 80%;
  box-shadow: 5px 5px 5px 5px rgb(126, 125, 125);
}
</style>
