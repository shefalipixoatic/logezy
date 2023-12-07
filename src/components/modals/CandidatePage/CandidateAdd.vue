<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="addCandidate"
      aria-labelledby="candidatePage"
      tabindex="-1"
    >
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="addCandidate">Add Candidate</h5>
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
                  <div class="col-4">
                    <label class="form-label">name</label>
                  </div>
                  <div class="col-8">
                    <input
                      type="text"
                      class="form-control"
                      v-model="first_name"
                    />
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-4">
                    <label class="form-label" for="selectOption"
                      >position</label
                    >
                  </div>
                  <div class="col-8">
                    <select v-model="job_id" id="selectOption">
                      <option
                        v-for="option in options"
                        :key="option.id"
                        :value="option.name"
                      >
                        {{ option.name }}
                      </option>
                    </select>
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-4">
                    <label class="form-label">email</label>
                  </div>
                  <div class="col-8">
                    <input type="email" class="form-control" v-model="email" />
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-4">
                    <label class="form-label">password</label>
                  </div>
                  <div class="col-8">
                    <input
                      type="password"
                      class="form-control"
                      v-model="password"
                    />
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-4">
                    <label class="form-label">confirm password</label>
                  </div>
                  <div class="col-8">
                    <input
                      type="password"
                      class="form-control"
                      v-model="confirm_password"
                    />
                  </div>
                </div>
                <div class="mb-3 d-flex justify-content-between">
                  <div class="col-4">
                    <label class="form-label">phone number</label>
                  </div>
                  <div class="col-8">
                    <input
                      type="number"
                      class="form-control"
                      v-model="phone_number"
                    />
                  </div>
                </div>
              </form>
            </div>
          </div>
          <div class="modal-footer">
            <button
              class="btn btn-secondary rounded-1"
              data-bs-target="#addCandidate"
              data-bs-toggle="modal"
              data-bs-dismiss="modal"
            >
              Cancel
            </button>
            <button
              class="btn btn-primary rounded-1 text-capitalize fw-medium"
              data-bs-dismiss="modal"
              v-on:click="addCandidate()"
            >
              Add
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
  name: "CandidateAdd",
  data() {
    return {
      selectedOption: null,

      first_name: "",
      last_name: "",
      password: "",
      job_id: "",
      options: [],
      confirm_password: "",
      address: "",

      phone_number: "",
      email: "",
      activated: "",
      employment_type_id: "",

      error: [],
    };
  },
  computed: {
    selectedOptionText() {
      const job_id = this.options.find((option) => option.id === this.job_id);
      return job_id ? job_id.name : "";
    },
  },
  methods: {
    async addCandidate() {
      const data = {
        first_name: this.first_name,
        job_id: 1,
        password: this.password,
        confirm_password: this.confirm_password,

        phone_number: this.phone_number,
        email: this.email,
        activated: this.activated,
      };
      try {
        const response = await fetch("https://logezy.onrender.com/candidates", {
          method: "POST",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
          body: JSON.stringify(data),
        });

        if (data) {
          location.reload();
        }
      } catch (error) {
        console.log(error);
      }
    },
    async getPositionMethod() {
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
  },

  mounted() {
    this.getPositionMethod();
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
.modal-footer {
  border-top: 0px;
}

#head {
  width: 40px;
  height: 40px;
}

select {
  width: 100%;
  padding: 10px;
  border-radius: 4px;
  border: 0px;
}
.btn-primary {
  background-color: #ff5f30 !important;
  font-weight: bold;
  border: none;
  border-radius: 4px;
  outline: none;
}
label.form-label {
  text-transform: capitalize;
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
