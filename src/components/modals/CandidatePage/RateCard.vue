<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="rateCards"
      aria-labelledby="ratePAge"
      tabindex="-1"
    >
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="rateCards">Add RateCard</h5>
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
                    <label class="form-label">Position</label>
                  </div>
                  <div class="col-10">
                    <input type="text" class="form-control" v-model="job_id" />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Day</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="weekname"
                    />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Employment Type</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="employment_type_id"
                    />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Shift Type Start End Time</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="shift_id"
                    />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Staff Rate</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="staff_rate"
                    />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Last Update</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="last_updated"
                    />
                  </div>
                </div>

                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-2">
                    <label class="form-label">Last Update</label>
                  </div>
                  <div class="col-10">
                    <input
                      type="text"
                      class="form-control"
                      v-model="last_updated"
                    />
                  </div>
                </div>
              </form>
            </div>
          </div>
          <div class="modal-footer">
            <button
              class="btn btn-secondary rounded-1"
              data-bs-target="#rateCards"
              data-bs-toggle="modal"
              data-bs-dismiss="modal"
            >
              Cancel
            </button>
            <button
              class="btn btn-primary rounded-1 text-capitalize fw-medium"
              data-bs-dismiss="modal"
              v-on:click="addRateCardMethod()"
            >
              Add RateCard
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
  name: "RateCard",
  data() {
    return {
      weekname: "",
      staff_rate: "",
      business_unit: "",
      job_id: "",
      employment_type_id: "",
      shift_id: "",
      last_updated: "",
    };
  },
  methods: {
    async addRateCardMethod() {
      const data = {
        weekname: this.weekname,
        staff_rate: this.staff_rate,
        business_unit: this.business_unit,
        job_id: this.job_id,
        employment_type_id: this.employment_type_id,
        shift_id: this.shift_id,
        last_updated: this.last_updated,
      };
      try {
        const response = await fetch("https://logezy.onrender.com/rate_cards", {
          method: "POST",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
          body: JSON.stringify(data),
        });

        console.log(data);
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
