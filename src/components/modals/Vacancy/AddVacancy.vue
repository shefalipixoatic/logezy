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
                    <select v-model="business_unit" id="selectBusinessUnit">
                      <option
                        v-for="option in businessUnit"
                        :key="option.id"
                        :value="option.name"
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
                    <select v-model="client" id="selectClients">
                      <option
                        v-for="option in clientData"
                        :key="option.id"
                        :value="option.first_name"
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
                  <select v-model="job_title" id="selectJobTitle">
                    <option
                      v-for="option in options"
                      :key="option.id"
                      :value="option.name"
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
                    <select v-model="shift" id="selectShifts">
                      <option
                        v-for="option in shiftsTime"
                        :key="option.id"
                        :value="option.shift_name"
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
      business_unit: "",
      client: "",
      clientData: [],
      job_title: "",
      options: [],
      businessUnit: [],
      dates: [],
      shift: "",
      shiftsTime: [],
      notes: "",
      client_id: 1,
    };
  },
  computed: {
    selectedOptionText() {
      const job_title = this.options.find(
        (option) => option.id === this.job_title
      );
      return job_title ? job_title.name : "";
    },

    selectBusinessUnit() {
      const business_unit = this.businessUnit.find(
        (option) => option.id === this.business_unit
      );
      return business_unit ? business_unit.name : "";
    },

    selectClients() {
      const client = this.clientData.find(
        (option) => option.id === this.client
      );
      return client ? client.first_name : "";
    },

    selectShifts() {
      const shift = this.shiftsTime.find((option) => option.id === this.shift);
      return shift ? shift.shift_name : "";
    },
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
        client_id: this.client_id,
      };
      try {
        const token = localStorage.getItem("token");
        const response = await fetch("https://logezy.onrender.com/vacancies", {
          method: "POST",
          headers: {
            Authorization: token,
          },
          body: JSON.stringify(data),
        });
        console.log(data);
      } catch (error) {
        console.log(error);
      }
    },
    async getJobTitleMethod() {
      try {
        const response = await axios.get("https://logezy.onrender.com/jobs");
        this.options = response.data;
        console.log(this.options);
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
        console.log(this.businessUnit);
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
        console.log(this.clientData);
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
