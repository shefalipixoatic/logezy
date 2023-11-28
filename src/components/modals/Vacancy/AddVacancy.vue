<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="addVacancies"
      aria-labelledby="addVacancies"
      tabindex="-1"
    >
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="addVacancies">Add Vacancy</h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body mx-3">
            <div class="row g-3 align-items-center">
              <form>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Business Unit</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="business_unit"
                    />
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Client</label>
                  </div>
                  <div class="col-10">
                    <input type="text" class="form-control" v-model="client" />
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Job Title</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="job_title"
                    />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Dated</label>
                  </div>
                  <div class="col-10">
                    <input type="text" class="form-control" v-model="dates" />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Shift</label>
                  </div>
                  <div class="col-10">
                    <input type="text" class="form-control" v-model="shift" />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Notes</label>
                  </div>
                  <div class="col-10">
                    <input type="text" class="form-control" v-model="notes" />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Publish</label>
                  </div>
                  <div class="col-10">
                    <input type="text" class="form-control" v-model="publish" />
                  </div>
                </div>
              </form>
            </div>
          </div>
          <div class="modal-footer">
            <button
              class="btn btn-secondary rounded-1"
              data-bs-target="#addVacancies"
              data-bs-toggle="modal"
              data-bs-dismiss="modal"
            >
              Cancel
            </button>
            <button
              class="btn btn-primary rounded-1 text-capitalize fw-medium"
              data-bs-dismiss="modal"
              v-on:click="addVacancyMethod()"
            >
              Add Vacancy
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AddVacancy",
  data() {
    return {
      business_unit: "",
      client: "",
      job_title: "",
      dates: "",
      shift: "",
      notes: "",
      publish: "",
    };
  },
  methods: {
    async addVacancyMethod() {
      const data = {
        business_unit: this.business_unit,
        client: this.client,
        job_title: this.job_title,
        dates: this.dates,
        shift: this.shift,
        notes: this.notes,
        publish: this.publish,
      };
      try {
        const token = localStorage.getItem("token");
        const response = await fetch("https://logezy.onrender.com/vacancies", {
          method: "POST",
          headers: {
            Authorization: "bearer " + token,
          },
          body: JSON.stringify(data),
        });
        console.log(response.data.data);
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {},
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
.modal-footer {
  border-top: 0px;
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
