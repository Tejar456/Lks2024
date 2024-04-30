<template>
<div class="text">
    <h1>Logout</h1>
</div>
</template>


<script setup>
const supabase = useSupabaseClient()

const Logout = async() => {
    const { error } = await supabase.auth.signOut()
    if (!error) navigateTo("/login")
}

async function insertLog() {
    const user = useSupabaseUser()
  const { error } = await supabase.from("Tbl_LogActivity").insert([
    {
    Aktivitas: "Logout",
    username: user.value.user_metadata.username,
    nama: user.value.user_metadata.username,
    tipe_user: user.value.user_metadata.tipe_user,
  }
])
if (!error) {
    Logout()
}
}

onMounted(() =>{
    insertLog()
})
</script>

<style scoped>
.text {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
</style>