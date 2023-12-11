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
                    <label class="form-label" for="selectBusinessUnit"
                      >Business Unit</label
                    >
                  </div>

                  <div class="col-10">
                    <select v-model="business_unit_id" id="selectBusinessUnit">
                      <option
                        v-for="option in businessUnit"
                        :key="option.id"
                        :value="option.id"
                        placeholder="Select BusinessUnit"
                      >
                        {{ option.name }}
                      </option>
                    </select>
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label for="selectClients" class="form-label">Client</label>
                  </div>
                  <div class="col-10">
                    <select v-model="client_id" id="selectClients">
                      <option
                        v-for="option in clientData"
                        :key="option.id"
                        :value="option.id"
                        aria-placeholder="Select Job"
                      >
                        {{ option.first_name }}
                      </option>
                    </select>
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label" for="selectJobTitle"
                      >Job Title</label
                    >
                  </div>
                  <select v-model="job_id" id="selectJobTitle">
                    <option
                      v-for="option in options"
                      :key="option.id"
                      :value="option.id"
                      aria-placeholder="Select Job"
                    >
                      {{ option.name }}
                    </option>
                  </select>
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
                    <label class="form-label" for="selectShifts">Shift</label>
                  </div>
                  <div class="col-10">
                    <select v-model="shift_id" id="selectShifts">
                      <option
                        v-for="option in shiftsTime"
                        :key="option.id"
                        :value="option.id"
                        aria-placeholder="Select Job"
                      >
                        {{ option.shift_name }}
                      </option>
                    </select>
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
      business_unit_id: "",
      client_id: "",
      clientData: [],
      job_id: "",
      options: [],
      businessUnit: [],
      dates: [],
      shift_id: "",
      shiftsTime: [],
      notes: "",
    };
  },
  computed: {
    selectedOptionText() {
      const jobs_id = this.options.find((option) => option.id === this.jobs_id);
      return jobs_id ? jobs_id.name : "";
    },

    selectBusinessUnit() {
      const business_unit_id = this.businessUnit.find(
        (option) => option.id === this.business_unit_id
      );
      return business_unit_id ? business_unit_id.name : "";
    },

    selectClients() {
      const client_id = this.clientData.find(
        (option) => option.id === this.client_id
      );
      return client_id ? client_id.first_name : "";
    },

    selectShifts() {
      const shifts_id = this.shiftsTime.find(
        (option) => option.id === this.shifts_id
      );
      return shifts_id ? shifts_id.shift_name : "";
    },
  },

  methods: {
    async addVacancyMethod() {
      const data = {
        business_unit_id: this.business_unit_id,
        job_id: this.job_id,
        dates: [this.dates],
        shift_id: this.shift_id,
        notes: this.notes,
        client_id: this.client_id,
      };
      try {
        const token = localStorage.getItem("token");
        const response = await fetch("https://logezy.onrender.com/vacancies", {
          method: "POST",
          headers: {
            "content-type": "application/json",
            Authorization: "bearer " + token,
          },
          body: JSON.stringify(data),
        });
      } catch (error) {
        console.log(error);
      }
    },
    async getJobTitleMethod() {
      try {
        const response = await axios.get("https://logezy.onrender.com/jobs");
        this.options = response.data;
      } catch (error) {
        if (error.response) {
          if (error.response.status == 404) {
            alert(error.response.data.message);
          }
        }
      }
    },
    async getBusinessUnitMethod() {
      try {
        const response = await axios.get(
          "https://logezy.onrender.com/business_units"
        );
        this.businessUnit = response.data;
      } catch (error) {
        if (error.response) {
          if (error.response.status == 404) {
            alert(error.response.data.message);
          }
        }
      }
    },
    async getClientMethod() {
      try {
        const response = await axios.get("https://logezy.onrender.com/clients");
        this.clientData = response.data.data;
      } catch (error) {
        if (error.response) {
          if (error.response.status == 404) {
            alert(error.response.data.message);
          }
        }
      }
    },
    async getTimeShift() {
      await axios
        .get("https://logezy.onrender.com/shifts")
        .then((response) => (this.shiftsTime = response.data));
    },
  },
  mounted() {
    this.getJobTitleMethod();
    this.getBusinessUnitMethod();
    this.getClientMethod();
    this.getTimeShift();
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
