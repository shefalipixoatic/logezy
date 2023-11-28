<template>
  <div>
    <div class="container-fluid p-0">
      <div id="main">
        <div class="pagetitle d-flex justify-content-between px-2">
          <div class="py-3">
            <ol class="breadcrumb mb-1">
              <li class="breadcrumb-item active text-uppercase fs-6">
                Dashboard / CANDIDATES /

                <span class="badge text-dark">{{
                  activeCandidate.active_candidate
                }}</span>
                <span>Active Candidates</span>
              </li>
            </ol>
          </div>
        </div>
      </div>
    </div>
    <div class="container-fluid p-0">
      <div class="row">
        <div class="">
          <div class="d-flex gap-2 justify-content-between bg-define">
            <ul class="nav nav-pills my-3 p-2" role="tablist">
              <li class="nav-item d-inline-flex gap-2" role="presentation">
                <button
                  a
                  class="nav-link"
                  aria-selected="true"
                  type="button"
                  role="tab"
                  data-bs-toggle="pill"
                  v-for="(tab, index) in tabs"
                  :key="index"
                  @click="selectTab(index)"
                >
                  {{ tab.name }}
                </button>
              </li>
            </ul>
            <div class="d-flex align-items-center p-2">
              <div class="d-flex justify-content-between">
                <form
                  class="form-inline my-2 my-lg-0 d-flex align-items-center justify-content-between gap-2"
                >
                  <input
                    class="form-control mr-sm-2"
                    type="search"
                    placeholder="Search by Name"
                    aria-label="Search"
                    v-model="searchQuery"
                    @input="search"
                  />
                  <!-- <button class="btn btn-primary">search</button> -->

                  <div class="d-flex justify-content-between gap-2">
                    <button
                      type="button"
                      class="btn btn-outline-success text-nowrap text-nowrap"
                      data-bs-toggle="modal"
                      data-bs-target="#addCandidate"
                      data-bs-whatever="@mdo"
                      @click="showPopup"
                    >
                      <i class="bi bi-person-plus-fill"></i>
                      Add Candidate
                    </button>
                  </div>
                </form>
              </div>
            </div>
          </div>
          <div>
            <component :is="activeComponent"></component>
          </div>

          <div v-if="searchQuery">
            <table class="table candidateTable">
              <thead>
                <tr>
                  <th scope="col">Name</th>
                  <th scope="col">Positions</th>
                  <th scope="col">Email</th>
                  <th scope="col">Phone</th>
                  <th scope="col">Status</th>
                  <th scope="col">Access</th>
                  <th scope="col">Assign</th>
                  <th scope="col">Last Login</th>
                  <th scope="col">Action</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="datas in searchResults" :key="datas.id">
                  <td>{{ datas.first_name }}</td>
                  <td>1</td>
                  <td>1</td>
                  <td>1</td>
                  <td>1</td>
                  <td>1</td>
                  <td>1</td>
                  <td>1</td>
                  <td>1</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

    <CandidateAdd />
  </div>
</template>

<script>
import axios from "axios";
import CandidateAdd from "../modals/CandidatePage/CandidateAdd.vue";
import ActiveCandidate from "../CandidatePages/ActiveCandidate.vue";
import InActiveCandidate from "../CandidatePages/InActiveCandidate.vue";
import Rejected from "../CandidatePages/Rejected.vue";

export default {
  name: "CAndidatesList",
  data() {
    return {
      getCandidatesData: [],
      inactiveCandidateData: [],
      activeCandidate: [],
      searchQuery: "",
      searchResults: [],
      tabs: [
        { name: "Active Candidates", component: "ActiveCandidate" },
        { name: "InActive Candidates", component: "InActiveCandidate" },
        { name: "Pending...", component: "Rejected" },
      ],
      activeTab: 0,
    };
  },
  computed: {
    activeComponent() {
      return this.tabs[this.activeTab].component;
    },
  },
  components: {
    CandidateAdd,
    ActiveCandidate,
    InActiveCandidate,
    Rejected,
  },

  onMounted() {},
  methods: {
    selectTab(index) {
      this.activeTab = index;
    },

    async getCandidate() {
      try {
        const response = await axios.get(
          "https://logezy.onrender.com/candidates"
        );

        this.getCandidatesData = response.data.data;
        this.activeCandidate = response.data;
      } catch (error) {
        if (error.response) {
          if (error.response.status == 404) {
            alert(error.response.data.message);
          }
        } else {
          console.error("Error fetching candidates:", error);
        }
      }
    },

    //search api start

    async search() {
      // Implement your API search endpoint
      const apiUrl = `https://logezy.onrender.com/candidate/search_candidate?=${this.searchQuery}`;

      try {
        const response = await axios.get(apiUrl);
        this.searchResults = response.data;
        console.log(this.searchResults);
      } catch (error) {
        console.error("Error fetching search results:", error);
      }
    },

    // search api end

    // redirectToUserProfile() {
    //   this.$router.push({
    //     name: "CandidateProfile",
    //     params: { id: this.userId },
    //   });
    //   console.log("redirect");
    // },
  },

  mounted() {
    this.getCandidate();
  },
};
</script>

<style scoped>
#main {
  transition: all 0.3s;
}
.main-content {
  transition: all 0.3s;
}
.bg-define {
  background-color: #fdce5e17;
  border-bottom: 1px solid #ded9d9;
  border-top: 1px solid #ded9d9;
}
.btn-primary {
  border: none;
  font-size: 13px;
  font-weight: 700;
}
a {
  color: black;
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
table th {
  background-color: #ff5f30;
}
.badge {
  background: #ff572247;
  border-radius: 50%;
  padding: 8px 11px;
}
a:link {
  color: black;
  text-decoration: none;
}

.switch {
  width: 50px;
  height: 17px;
  position: relative;
  display: inline-block;
}

.switch input {
  display: none;
}

.switch .slider {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  cursor: pointer;
  background-color: #e7ecf1;
  border-radius: 30px !important;
  border: 0;
  padding: 0;
  display: block;
  margin: 12px 10px;
  min-height: 11px;
}

.switch .slider:before {
  position: absolute;
  background-color: #aaa;
  height: 15px;
  width: 15px;
  content: "";
  left: 0px;
  bottom: -2px;
  border-radius: 50%;
  transition: ease-in-out 0.5s;
}

.switch .slider:after {
  content: "";
  color: white;
  display: block;
  position: absolute;
  transform: translate(-50%, -50%);
  top: 50%;
  left: 70%;
  transition: all 0.5s;
  font-size: 10px;
  font-family: Verdana, sans-serif;
}

.switch input:checked + .slider:after {
  transition: all 0.5s;
  left: 30%;
  content: "";
}

.switch input:checked + .slider {
  background-color: #d3d6d9;
}

.switch input:checked + .slider:before {
  transform: translateX(15px);
  background-color: #ff9800;
}
</style>
