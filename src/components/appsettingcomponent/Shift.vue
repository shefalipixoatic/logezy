<template>
  <div class="row">
    <div class="col-12 p-0">
      <div class="pagetitle d-flex justify-content-between">
        <div class="d-flex align-items-center">
          <ol class="breadcrumb mb-1">
            <li class="breadcrumb-item active text-uppercase fw-bold">
              Shift / <span>shift</span>
            </li>
          </ol>
        </div>
        <!-- End Page Title -->
        <div class="d-flex align-items-center"></div>
      </div>
      <div class="mt-3">
        <form class="" v-for="shift in shifts" :key="shift.id">
          <div class="row mb-3 border-bottom pb-4 mx-1">
            <div class="col-2 p-0">
              <label for="" class="form-label fw-medium">{{
                shift.shift_name
              }}</label>
            </div>
            <div class="col-10">
              <div class="d-flex justify-content-around">
                <div class="col-5">
                  <label for="time" class="form-label"
                    >Start Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="text"
                    id="time"
                    name="time"
                    :v-model:value="shift.start_time"
                    class="form-control"
                  />{{ new Date(shift.start_time).getUTCHours() }}
                </div>

                <div class="col-5">
                  <label for="time" class="form-label"
                    >End Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />{{ new Date(shift.end_time).getUTCHours() }}
                </div>
              </div>
            </div>
          </div>
          <!-- <div class="row mb-3 border-bottom pb-4 mx-1">
            <div class="col-2 p-0">
              <label for="" class="form-label fw-medium">Night Shift</label>
            </div>
            <div class="col-10">
              <div class="d-flex justify-content-around">
                <div class="col-5">
                  <label for="time" class="form-label"
                    >Start Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />
                </div>

                <div class="col-5">
                  <label for="time" class="form-label"
                    >End Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />
                </div>
              </div>
            </div>
          </div>
          <div class="row mb-3 border-bottom pb-4 mx-1">
            <div class="col-2 p-0">
              <label for="" class="form-label fw-medium"
                >Holiday Day Shift</label
              >
            </div>
            <div class="col-10">
              <div class="d-flex justify-content-around">
                <div class="col-5">
                  <label for="time" class="form-label"
                    >Start Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />
                </div>

                <div class="col-5">
                  <label for="time" class="form-label"
                    >End Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />
                </div>
              </div>
            </div>
          </div>
          <div class="row mb-3 border-bottom pb-4 mx-1">
            <div class="col-2 p-0">
              <label for="" class="form-label fw-medium"
                >Holiday Night Shift</label
              >
            </div>
            <div class="col-10">
              <div class="d-flex justify-content-around">
                <div class="col-5">
                  <label for="time" class="form-label"
                    >Start Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />
                </div>

                <div class="col-5">
                  <label for="time" class="form-label"
                    >End Time<span class="text-danger">*</span></label
                  >
                  <input
                    type="time"
                    id="time"
                    name="time"
                    class="form-control"
                  />
                </div>
              </div>
            </div>
          </div> -->
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Shift",
  data() {
    return {
      shifts: [],
    };
  },
  methods: {
    async getTime() {
      await axios
        .get("https://logezy.onrender.com/shifts")
        .then((response) => (this.shifts = response.data));
    },
  },

  mounted() {
    this.getTime();
  },
};
</script>

<style scoped></style>
