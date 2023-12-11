<template>
  <div>
    <div class="row">
      <div class="col-12">
        <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
          <li class="nav-item" role="presentation">
            <button
              class="nav-link active"
              id="activecandidate"
              data-bs-toggle="pill"
              data-bs-target="#pills-active"
              type="button"
              role="tab"
              aria-controls="pills-active"
              aria-selected="true"
            >
              Active Documents
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button
              class="nav-link"
              id="deletedDocument"
              data-bs-toggle="pill"
              data-bs-target="#pills-delete"
              type="button"
              role="tab"
              aria-controls="pills-delete"
              aria-selected="false"
            >
              Deleted Documents
            </button>
          </li>
        </ul>
        <div class="tab-content" id="pills-tabContent">
          <div
            class="tab-pane fade active"
            id="pills-active"
            role="tabpanel"
            aria-labelledby="activecandidate"
          >
            <div class="">
              <div class="row mb-3">
                <div
                  class="d-flex justify-content-between align-items-baseline"
                >
                  <div>
                    <h6>Document Categories</h6>
                  </div>
                  <div class="d-flex">
                    <button type="button" class="btn btn-primary btn-sm">
                      Download All
                    </button>
                  </div>
                </div>
              </div>

              <div class="row">
                <div
                  class="accordion accordion-flush"
                  id="accordionFlushExample"
                  v-for="data in get_Candidate_Document_Categories"
                  :key="data.id"
                >
                  <div class="accordion-item">
                    <h2 class="accordion-header" id="flush-headingOne">
                      <button
                        class="accordion-button collapsed"
                        type="button"
                        data-bs-toggle="collapse"
                        data-bs-target="#flush-collapseOne"
                        aria-expanded="false"
                        aria-controls="flush-collapseOne"
                      >
                        {{ data.category_name }}
                      </button>
                    </h2>
                    <div
                      id="flush-collapseOne"
                      class="accordion-collapse collapse"
                      aria-labelledby="flush-headingOne"
                      data-bs-parent="#accordionFlushExample"
                    >
                      <div class="accordion-body">
                        <form>
                          <div class="row">
                            <div class="col-md-6">
                              <div class="mb-3">
                                <label class="form-label">ISSUE DATE</label>
                                <input
                                  type="text"
                                  class="form-control"
                                  id="issue"
                                  placeholder="issue date"
                                  v-model="issue_date"
                                  title="issue date"
                                />
                              </div>
                            </div>
                            <div class="col-6">
                              <div class="mb-3">
                                <label class="form-label">EXPIRY DATE</label>
                                <input
                                  type="text"
                                  class="form-control"
                                  id="expiry"
                                  placeholder="expiry date"
                                  v-model="expiry_date"
                                  title="expiry date"
                                />
                              </div>
                            </div>
                          </div>

                          <div class="row">
                            <div class="mb-3">
                              <label class="form-label">Description</label>
                              <textarea
                                class="form-control"
                                rows="3"
                                v-model="description"
                              ></textarea>
                            </div>
                            <div class="mb-3">
                              <label for="formFile" class="form-label"
                                >UPLOAD DOCUMENT</label
                              >
                              <input
                                class="form-control"
                                type="file"
                                id="formFile"
                                ref="fileInput"
                                placeholder="upload doc"
                              />
                            </div>
                            <button type="button" class="btn btn-primary">
                              Save
                            </button>
                          </div>
                        </form>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div
            class="tab-pane fade"
            id="pills-delete"
            role="tabpanel"
            aria-labelledby="deletedDocument"
          >
            ...
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Document",
  data() {
    return {
      get_Candidate_Document_Categories: [],
    };
  },
  components: {},
  //  candidate category doc apis start
  async created() {
    const token = localStorage.getItem("token");
    axios
      .get("https://logezy.onrender.com/document_categories", {
        headers: {
          "content-type": "application/json",
          Authorization: "bearer " + token,
        },
      })

      .then(
        (response) => (this.get_Candidate_Document_Categories = response.data)
      );
  },

  //  candidate category doc apis end
};
</script>

<style scoped>
.fs-smaller {
  font-size: smaller;
}
.borderbottom {
  border-bottom: 1px solid #ebe2e2;
}

.accordion-button {
  width: 25%;
  background-color: transparent;
}
.accordion-button:focus {
  z-index: 3;
  border-color: none;
  outline: 0;
  box-shadow: none;
}
.accordion-button:not(.collapsed) {
  border: none;
  background: transparent;
  box-shadow: none;
}
.profile {
  border-radius: 0px;
  border-top: 1px solid transparent;
}
#main {
  transition: all 0.3s;
  padding: 10px;
  transition: all 0.3s;
}
.bg-white {
  border-left: 1px solid #dedede;
}
.bg-orange-light {
  background: #fef8f8;
  background-color: #fdce5e17;
}
.card ul li {
  display: inline-block;
}

table th {
  font-size: 14px;
}
.card {
  border-radius: 0px;
}

.border-box {
  border: 1px solid lightgrey;
  padding: 12px;
  border-radius: 4px;
}
.card .round {
  background: #ff572266;
  border-radius: 50%;
  padding: 10px 7px;
  margin-right: 8px;
}

.card .hround {
  background: #ff572266;
  border-radius: 50%;
  padding: 10px 11px;
  margin-right: 8px;
}
.card .dround {
  background: #ff572266;
  border-radius: 50%;
  padding: 12px 17px;
  margin-right: 8px;
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
.form-check-input {
  border: 2px solid grey;
}
.btn-primary {
  border: none;
}
.switch .slider {
  position: absolute;
  top: -3;
  bottom: 0;
  right: 0;
  left: 0;
  cursor: pointer;
  background-color: #e7ecf1;
  border-radius: 30px !important;
  border: 0;
  padding: 0;
  display: block;
  margin: 3px 10px;
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

.nav-pills .nav-link.active,
.nav-pills .show > .nav-link {
  color: #ff5722;

  border-bottom: 3px solid #ff5722;
  border-radius: 0px;
  background-color: transparent;
}
.nav-pills .nav-link {
  color: grey;
}
ul.nav-pills {
  border-bottom: 1px solid grey;
}
.nav-pills .nav-link {
  border-radius: 0px;
  padding: 5px 13px;
}

.accordion-item {
  margin-bottom: 8px;
}

.accordion-header {
  padding: 8px;
  cursor: pointer;
  background-color: #f1f1f1;
  border-bottom: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
}

.accordion-icon {
  font-size: 16px;
  transition: transform 0.3s;
}

.expanded {
  transform: rotate(90deg);
}
</style>
