<template>
  <div>
    <Navbar />
    <div class="container-fluid p-0">
      <div id="main">
        <div class="pagetitle d-flex justify-content-between px-2">
          <div class="py-3">
            <ol class="breadcrumb mb-1">
              <li class="breadcrumb-item active text-uppercase fs-6">
                Dashboard / <span class="color-fonts">Vacancies</span>
              </li>
            </ol>
          </div>
        </div>
        <div class="container-fluid p-0 bg-define">
          <div
            class="pagetitle d-flex justify-content-between align-items-center p-2"
          >
            <div class="d-flex justify-content-around gap-2">
              <select class="form-select" aria-label="Default select example ">
                <option selected>Custom</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
            </div>

            <div></div>

            <div class="d-flex align-items-center justify-content-between">
              <div class="d-flex align-items-center gap-2">
                <button
                  type="button"
                  class="btn btn-outline-success text-nowrap"
                  data-bs-toggle="modal"
                  data-bs-target="#addVacancies"
                  data-bs-whatever="@mdo"
                >
                  + Add Vacancy
                </button>
              </div>
            </div>
          </div>
        </div>

        <div class="container-fluid mt-3">
          <div class="row">
            <div class="col-12">
              <div class="">
                <div>
                  <ul
                    class="nav nav-pills mb-3 d-flex justify-content-between"
                    id="pills-tab"
                    role="tablist"
                  >
                    <div class="d-flex">
                      <li
                        class="nav-item"
                        role="presentation"
                        :class="{ 'nav-item': true, active: isActive }"
                      >
                        <button
                          :class="{ 'nav-link': true, active: isActive }"
                          class="nav-link active me-2"
                          id="pills-home-tab"
                          data-bs-toggle="pill"
                          data-bs-target="#pills-home"
                          type="button"
                          role="tab"
                          aria-controls="pills-home"
                          aria-selected="true"
                        >
                          Open(13)
                        </button>
                      </li>
                      <li class="nav-item" role="presentation">
                        <button
                          class="nav-link"
                          id="pills-profile-tab"
                          data-bs-toggle="pill"
                          data-bs-target="#pills-profile"
                          type="button"
                          role="tab"
                          aria-controls="pills-profile"
                          aria-selected="false"
                        >
                          Assigned(23)
                        </button>
                      </li>
                    </div>

                    <div class="searchbox position-relative">
                      <input
                        class="form-control mr-sm-2"
                        type="search"
                        placeholder="&nbsp;&nbsp;&nbsp;&nbsp; Search by vacancy code"
                        aria-label="Search"
                      />
                    </div>
                  </ul>
                  <div class="tab-content" id="pills-tabContent">
                    <div
                      class="tab-pane fade show active"
                      id="pills-home"
                      role="tabpanel"
                      aria-labelledby="pills-home-tab"
                    >
                      <table class="table candidateTable">
                        <thead>
                          <tr>
                            <th scope="col">#RefCode</th>
                            <th scope="col">Client</th>
                            <th scope="col">Business Unit</th>
                            <th scope="col">Job Title</th>
                            <th scope="col">Date</th>
                            <th scope="col">Shift</th>
                            <th scope="col">Notes</th>
                            <th scope="col">Publish</th>
                          </tr>
                        </thead>
                        <tbody>
                          <tr
                            v-for="getdata in getVacancyDetail"
                            :key="getdata.id"
                          >
                            <td v-text="getdata.ref_code"></td>
                            <td v-text="getdata.client"></td>
                            <td v-text="getdata.business_unit"></td>
                            <td v-text="getdata.job_title"></td>
                            <tr v-for="date in getdata.dates" :key="date.id">
                              <td>{{date}}</td>
                            </tr>
                            <!-- <td v-text="getdata.dates[0]"></td> -->
                            <td v-text="getdata.shift"></td>

                            <td v-text="getdata.notes"></td>
                            <td v-text="getdata.publish"></td>
                          </tr>
                        </tbody>
                      </table>
                    </div>
                    <div
                      class="tab-pane fade"
                      id="pills-profile"
                      role="tabpanel"
                      aria-labelledby="pills-profile-tab"
                    >
                      ...
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <AddVacancy />
  </div>
</template>
<script>
import axios from "axios";
import Navbar from "../components/Navbar.vue";
// import DatePicker from "../components/DatePicker.vue";
import AddVacancy from "../components/modals/Vacancy/AddVacancy.vue";

export default {
  data() {
    return {
      getVacancyDetail: [],
      isActive: true,
      searchQuery: "",
    };
  },
  components: {
    Navbar,
    AddVacancy,
  },
  // onMounted() {
  //   const addVacancies = new bootstrap.Modal(
  //     document.getElementById("addVacancies"),
  //     options
  //   );
  // },
  methods: {
    // showPopup() {
    //   addVacancies.show();
    // },
  },

  async created() {
    const token = localStorage.getItem("token");
    axios
      .get("https://logezy.onrender.com/vacancies", {
        headers: {
          "content-type": "application/json",
          Authorization: "bearer " + token,
        },
      })

      .then((response) => (this.getVacancyDetail = response.data));
  },
};
</script>

<style scoped>
#main {
  transition: all 0.3s;
  height: 100dvh;
}
.main-content {
  transition: all 0.3s;
}
.bg-define {
  background-color: #fdce5e17;
}
.color-fonts {
  color: #ff5f30;
  font-weight: bold;
}
.btn-primary {
  border: none;
}
.form-check-input {
  border: 2px solid grey;
}
.border-left {
  border-left: 1px solid #ded9d9;
  height: 100vh;
}

.candidateTable tr:nth-child(odd) td {
  background: #fdce5e17 !important;
}
.btn-primary {
  border-radius: 4px;
}

.nav-pills .nav-link.active,
.nav-pills .show > .nav-link {
  background-color: transparent;
  border: 1px solid green;
  border-radius: 22px;
  color: green;
}

.nav-pills .nav-link {
  background-color: transparent;
  border: 1px solid #0d6efd;
  border-radius: 22px;
}
ul.nav-pills {
  height: 53px;
  border-bottom: 1px solid #b8b1b1;
}
table th {
  background-color: #ff5f30;
}

button.nav-link > li.nav-item {
  border-bottom: 2px solid red; /* Replace with your desired border color */
  padding-bottom: 5px; /* Optional: Add padding for spacing */
}

button.nav-link.active > li.nav-item {
  /* Additional styles for the active state if needed */
}

.form-select {
  width: auto;
}
.searchbox {
  width: 19%;
}
.searchbox::before {
  content: "\F52A";
  font-family: "bootstrap-icons";
  position: absolute;
  top: 8px;
  left: 10px;
  color: #ff5f30;
  font-weight: bolder;
}
input::-webkit-input-placeholder {
  margin-left: 5px;
}
</style>
