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
              <h3>Tambah User</h3>
            </div>
          </div>
          <form @submit.prevent="tambahUser">
            <div class="mb-3">
              <select
                v-model="form.tipe_user"
                class="form-select"
                aria-label="Default select example"
              >
                <option selected>Tipe User</option>
                <option value="Admin">Admin</option>
                <option value="Apoteker">Apoteker</option>
                <option value="Kasir">Kasir</option>
              </select>
            </div>
            <div class="mb-3">
              <input
                v-model="form.username"
                type="text"
                class="form-control"
                placeholder="User Name"
              />
            </div>

            <div class="mb-3">
              <input
                v-model="form.email"
                type="email"
                class="form-control"
                placeholder="Email"
              />
            </div>
            <div class="mb-3">
              <input
                v-model="form.password"
                type="password"
                class="form-control"
                placeholder="Password"
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

const form = ref ({
  tipe_user: "",
  username: "",
  email: "",
  password: "",
});

const tambahUser = async () => {
  const { data, error } = await supabase.auth.signUp({
    email: form.value.email,
    password: form.value.password,
    options: {
      data: {
        username: form.value.username,
        tipe_user: form.value.tipe_user,
      },
    },
  });
  if (data) {
    navigateTo("/login")
    insertUser();
  }
  if (!error) {
    insertUser()
  }
};


// const insertUser = async() => {
//   console.log("insert");
//   const { error } = await supabase.from("User").insert([form.value])
//   if (error) throw error;
// }

async function insertUser() {
  const { error } = await supabase
  .from('User')
  .insert({ 
    email: form.value.email,
    password: form.value.password,
    username: form.value.username,
    tipe_user: form.value.tipe_user,
  })
  if (error) throw error
}

</script>
