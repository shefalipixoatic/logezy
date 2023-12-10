<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="allCandidateVacancyList"
      aria-labelledby="allCandidateVacancyList"
      tabindex="-1"
    >
      <div class="modal-dialog modal-dialog-centered modal-xl">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="allCandidateVacancyList">
              All Vacancy
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body mx-3">
            <div class="row g-3 align-items-center">
              <table class="table candidateTable">
                <thead>
                  <tr>
                    <th scope="col">candidate code</th>
                    <th scope="col">first name</th>
                    <th scope="col">last name</th>
                    <th scope="col">phone number</th>
                    <th scope="col">email</th>
                    <th scope="col">address</th>
                    <th scope="col">activated</th>
                    <th scope="col">status</th>
                    <th scope="col">position</th>
                    <th scope="col">employment type</th>
                    <th scope="col">last login</th>

                    <th scope="col">Action</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="data in getVacancyDetail" :key="data.id">
                    <td v-text="data.candidate_code"></td>
                    <td v-text="data.first_name"></td>
                    <td v-text="data.last_name"></td>
                    <td v-text="data.phone_number"></td>

                    <td v-text="data.email"></td>

                    <td v-text="data.address"></td>

                    <td v-text="data.activated"></td>
                    <td v-text="data.status"></td>
                    <td v-text="data.position"></td>
                    <td v-text="data.employment_type"></td>
                    <td v-text="data.last_login"></td>
                    <td class="cursor-pointer">
                      <a class="btn btn-outline-success text-nowrap">
                        <i class="bi bi-pencil-square"></i>
                      </a>
                      &nbsp;&nbsp;
                      <button class="btn btn-outline-success text-nowrap">
                        <i
                          class="bi bi-trash"
                          v-on:click="vacancyDeleteMethod(data.id)"
                        ></i>
                      </button>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
          <div class="modal-footer">
            <button
              class="btn btn-secondary rounded-1"
              data-bs-target="#allCandidateVacancyList"
              data-bs-toggle="modal"
              data-bs-dismiss="modal"
            >
              Cancel
            </button>
            <!-- <button
              class="btn btn-primary rounded-1 text-capitalize fw-medium"
              data-bs-dismiss="modal"
              v-on:click="addVacancyMethod()"
            >
              Add Vacancy
            </button> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AllVacancyCandidateList",
  data() {
    return { getVacancyDetail: [], allVacancyData: [] };
  },

  methods: {
    async getAppliedVacancyMethod() {
      const token = localStorage.getItem("token");

      // Manually set the index or use your own logic to determine it
      const customIndex = 0; // Change this to your logic or set it manually

      // Check if vacancyData is not empty and has the item at the determined index
      if (this.allVacancyData.length > customIndex) {
        const vacancyId = this.allVacancyData[customIndex].id;

        try {
          const response = await axios.get(
            `https://logezy.onrender.com/applied_candidate_list?vacancy_id=${vacancyId}`,
            {
              headers: {
                "content-type": "application/json",
                Authorization: "bearer " + token,
              },
            }
          );
          this.getVacancyDetail = response.data;
        } catch (error) {
          if (error.response) {
            if (error.response.status == 404) {
              alert(error.response.data.message);
            }
          }
        }
      } else {
        console.error(
          "Vacancy data is empty or does not have the item at the determined index."
        );
      }
    },

    async getVacancyDataMethod() {
      const token = localStorage.getItem("token");
      try {
        const response = await axios.get(
          "https://logezy.onrender.com/vacancies",
          {
            headers: {
              "content-type": "application/json",
              Authorization: "bearer " + token,
            },
          }
        );
        this.allVacancyData = response.data;
        this.getAppliedVacancyMethod();
      } catch (error) {
        console.error("Error fetching vacancies:", error);
      }
    },
  },

  mounted() {
    this.getVacancyDataMethod();
  },
};
</script>

<style scoped>
.modal-body {
  border-radius: 5px;
  background: #dbdbdb;
}
.modal-header {
  border-bottom: 0px;
}

select {
  width: 100%;
  padding: 10px;
  border-radius: 4px;
  border: 0px;
}
label.form-label {
  text-transform: capitalize;
}
.modal-footer {
  border-top: 0px;
}
.modal-xl {
  --bs-modal-width: 1823px !important;
}
.btn-primary {
  border: none;
}
#head {
  width: 40px;
  height: 40px;
}

.modal {
  --bs-modal-width: 881px;
}
</style>
