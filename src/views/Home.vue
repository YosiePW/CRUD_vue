<template>



      <div class="container-fluid page-body-wrapper">
      <div class="main-panel">
        <div class="content-wrapper">
          <div class="row">
            <div class="col-md-6 col-lg-6 grid-margin stretch-card">
              <div class="row">
                <div class="col-md-6 col-lg-6 grid-margin stretch-card">
                  <div class="card bg-gradient-primary text-white text-center card-shadow-primary">
                    <div class="card-body">
                      <h6 class="font-weight-normal">Data Siswa</h6>
                     <h2 class="mb-0">1450</h2>
                    </div>
                  </div>
                </div>
                <div class="col-md-6 col-lg-6 grid-margin stretch-card">
                  <div class="card bg-gradient-warning text-white text-center card-shadow-warning">
                    <div class="card-body">
                      <h6 class="font-weight-normal">Data Petugas</h6>
                      <h2 class="mb-0">8</h2>
                    </div>
                  </div>
                </div>
                <div class="col-md-6 col-lg-6 grid-margin stretch-card">
                  <div class="card bg-gradient-danger text-white text-center card-shadow-danger">
                    <div class="card-body">
                      <h6 class="font-weight-normal">Data Pelanggaran</h6>
                      <h2 class="mb-0">120</h2>
                    </div>
                  </div>
                </div>
                <div class="col-md-6 col-lg-6 grid-margin stretch-card">
                  <div class="card bg-gradient-success text-white text-center card-shadow-success">
                    <div class="card-body">
                      <h6 class="font-weight-normal">Siswa Melanggar Hari Ini</h6>
                      <h2 class="mb-0">12</h2>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-md-6 col-lg-6 grid-margin stretch-card">
              <div class="card">
                <div class="card-body">
                  <div class="d-flex justify-content-between">
                    <h6 class="card-title"><i class="mdi mdi-finance menu-icon"></i> Poin Tertinggi</h6>
                  </div>
                  <div class="list d-flex align-items-center border-bottom pb-3">
                    <div class="wrapper w-100">
                      <p><b>George Bambang Prakoso</b> <span class="badge badge-danger">300</span></p>
                      <small class="text-muted">XI RPL 2</small>
                    </div>
                  </div>
                  <div class="list d-flex align-items-center border-bottom py-3">
                    <div class="wrapper w-100">
                      <p><b>John Fikri Santoso</b> <span class="badge badge-danger">280</span></p>
                      <small class="text-muted">XII TKJ 3</small>                      
                    </div>
                  </div>
                  <div class="list d-flex align-items-center border-bottom py-3">
                    <div class="wrapper w-100">
                      <p><b>Peter Sudarmono Pambudi</b> <span class="badge badge-danger">260</span></p>
                      <small class="text-muted">X RPL 6</small>                      
                    </div>
                  </div>
                  <div class="list d-flex align-items-center border-bottom py-3">
                    <div class="wrapper w-100">
                      <p><b>Nateila Ayu Rahmawati</b> <span class="badge badge-danger">200</span></p>
                      <small class="text-muted">X TKJ 2</small>                      
                    </div>
                  </div>
                  <div class="list d-flex align-items-center pt-3">
                    <div class="wrapper w-100">
                      <p><b>Ahmad Tom Jerry</b> <span class="badge badge-danger">187</span></p>
                      <small class="text-muted">3 hours ago</small>                      
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- content-wrapper ends -->
        <!-- partial:partials/_footer.html -->
        <footer class="footer">
          <div class="w-100 clearfix">
            <span class="text-muted d-block text-center text-sm-left d-sm-inline-block">Copyright © 2019 <a href="http://www.urbanui.com/" target="_blank">Moklet</a>. All rights reserved.</span>
            <span class="float-none float-sm-right d-block mt-1 mt-sm-0 text-center">UKL Moklet & Made With <i class="mdi mdi-heart-outline text-danger"></i></span>
          </div>
        </footer>
        <!-- partial -->
      </div>
      <!-- main-panel ends -->
    </div>

</template>

<script>

module.exports = {
 data : function(){
    return {
      search: "",
      id: "",
      name: "",
      email: "",
      password: "",
      action: "",
      message: "",
      currentPage: 1,
      rows: 0,
      brows: 0,
      perPage: 2,
      key: "",
      siswa: [],
      sum: "",
      sumdipinjam: "",
      fields: ["id", "name", "email", "Aksi"],
    }
  },

  methods: {
    getData : function(){
      let conf = { headers: { "Authorization" : 'Bearer ' + this.key } };
      let offset = (this.currentPage - 1) * this.perPage;
      this.$bvToast.show("loadingToast");
      axios.get(base_url + "/siswa/" + this.perPage + "/" + offset, conf)
      .then(response => {
        if(response.data.status == 1){
          this.$bvToast.hide("loadingToast");
          this.siswa = response.data.siswa;
          this.rows = response.data.count;
        } else {
          window.location = "../login.html";
        }
        
      })
      .catch(error => {
        console.log(error);
      });
    },
  }
}
</script>
