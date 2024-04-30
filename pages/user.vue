<template>
    <div>
      <div class="row bg-all">
        <div class="col-lg-2">
          <Navbar />
        </div>
        <div class="col-lg-10">
          <div class="card">
            <div class="row">
                <div class="col-lg-2">

                    <h3>Kelola User</h3>
                </div>
                <div class="col-lg-2">
                    <NuxtLink to="/tambahuser">

                        <button type="submit" class="btn bg-primary text-light">Tambah</button>
                    </NuxtLink>
                </div>
            </div>
            <table class="table">
              <thead>
                <tr>
                  <th scope="col">Id</th>
                  <th scope="col">User Name</th>
                  <th scope="col">Tipe User</th>
                  <th scope="col">Email</th>
                </tr>
              </thead>
              <tbody>
             
        
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </template>
  