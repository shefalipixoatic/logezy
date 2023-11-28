<template>
  <div>
    <Navbar />

    <div class="container-fluid p-0 mt-3">
      <div id="main" class="bg-orange-light">
        <div class="pagetitle d-flex justify-content-between">
          <div class="">
            <ol class="breadcrumb mb-1">
              <li class="breadcrumb-item active text-uppercase fs-6">
                Dashboard / CANDIDATES / {{ getCandidates.first_name }}
              </li>
            </ol>
          </div>
        </div>
      </div>
    </div>
    <div class="">
      <div id="main">
        <div class="row">
          <div class="col-12 borderbottom pb-3 pt-1">
            <div class="float-end">
              <button type="button" class="btn btn-outline-primary">
                Next <i class="bi bi-caret-right-fill"></i>
              </button>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-3 p-0">
            <div class="card profile">
              <img src="./profilenotimg.jpg" class="card-img-top" alt="..." />
              <div class="card-body">
                <div
                  class="mt-3 d-flex justify-content-between align-items-center"
                >
                  <div>
                    <h6 class="card-title text-nowrap fw-bold">
                      {{ getCandidates.first_name }}
                    </h6>
                    <span class=""> {{ getCandidates.email }}</span>
                  </div>

                  <div>
                    <button type="button" class="btn btn-outline-primary">
                      Edit
                    </button>
                  </div>
                </div>
                <hr />
                <div class="mt-3">
                  <div class="d-flex justify-content-between">
                    <div>
                      <h6
                        class="card-title text-uppercase fs-smaller text-nowrap"
                      >
                        contact information
                      </h6>
                    </div>

                    <div class="d-flex justify-content-between">
                      <h6 class="fs-smaller text-nowrap">Profile View</h6>
                      <label class="switch">
                        <input
                          type="checkbox"
                          id="togBtn"
                          title="check"
                          checked
                        />
                        <div class="slider round"></div>
                      </label>
                    </div>
                  </div>

                  <div class="d-flex justify-content-between mt-3">
                    <div class="d-flex align-items-center">
                      <span
                        ><i class="bi bi-telephone"></i>
                        {{ getCandidates.phone_number }}</span
                      >
                    </div>
                    <button type="button" class="btn btn-outline-primary">
                      Edit
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md-9 bg-white">
            <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
              <li class="nav-item" role="presentation">
                <router-link
                  class="nav-link active"
                  to="/candidate/candidate_profile/:id/Overview"
                  id="overview"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-home"
                  type="button"
                  role="tab"
                  aria-controls="pills-home"
                  aria-selected="true"
                >
                  Overview
                </router-link>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="document"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-profile"
                  type="button"
                  role="tab"
                  aria-controls="pills-profile"
                  aria-selected="false"
                >
                  Document
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="profile"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-contact"
                  type="button"
                  role="tab"
                  aria-controls="pills-contact"
                  aria-selected="false"
                >
                  Profile
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="restricted"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-restricted"
                  type="button"
                  role="tab"
                  aria-controls="pills-restricted"
                  aria-selected="false"
                >
                  Restricted
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="ratecard"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-ratecard"
                  type="button"
                  role="tab"
                  aria-controls="pills-ratecard"
                  aria-selected="false"
                >
                  Rate-Card
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="notes"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-contact"
                  type="button"
                  role="tab"
                  aria-controls="pills-contact"
                  aria-selected="false"
                >
                  Notes
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="staff-id"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-contact"
                  type="button"
                  role="tab"
                  aria-controls="pills-contact"
                  aria-selected="false"
                >
                  Staff ID
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="candidate-history"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-contact"
                  type="button"
                  role="tab"
                  aria-controls="pills-contact"
                  aria-selected="false"
                >
                  Candidate History
                </button>
              </li>
              <li class="nav-item" role="presentation">
                <button
                  class="nav-link"
                  id="candidate-history"
                  data-bs-toggle="pill"
                  data-bs-target="#pills-contact"
                  type="button"
                  role="tab"
                  aria-controls="pills-contact"
                  aria-selected="false"
                >
                  Candidate Reference
                </button>
              </li>
            </ul>
            <div class="tab-content" id="pills-tabContent">
              <div
                class="tab-pane fade show active"
                id="pills-home"
                role="tabpanel"
                aria-labelledby="overview"
              >
                <div class="row">
                  <div class="col-6">
                    <div class="card rounded-0">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            Starter Check List
                          </h5>
                          <button
                            type="button"
                            class="btn btn-outline-primary mb-3"
                          >
                            Edit
                          </button>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table table-borderless">
                          <thead>
                            <tr class=""></tr>
                          </thead>
                          <tbody class="text-capitalize">
                            <tr>
                              <td>Candidate ID</td>
                              <td>:</td>
                              <td></td>
                              <td v-text="getCandidates.candidate_code"></td>
                            </tr>
                            <tr>
                              <td>Employment Type</td>
                              <td>:</td>
                              <td></td>
                              <td>PAYE</td>
                            </tr>
                            <tr>
                              <td>Companies</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>DBS/PVG No</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>DBS/PVG Issue Date</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>DBS/PVG Expiry Date</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>Next Check Date</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>NMC/NISCC/SSSC Pin</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>Nationality</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>Date of Birth</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>Place of Birth</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>Gender</td>
                              <td>:</td>
                              <td></td>
                              <td>...</td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>

                    <div class="card mt-3">
                      <div class="card-header">
                        <div class="d-flex justify-content-between">
                          <div class="d-flex align-items-center">
                            <div class="fs-smaller text-nowrap">
                              Profile View
                            </div>
                            <label class="switch">
                              <input type="checkbox" id="togBtn" checked />
                              <div class="slider round"></div>
                            </label>
                          </div>

                          <div>
                            <button
                              type="button"
                              class="btn btn-outline-primary"
                            >
                              Edit
                            </button>
                          </div>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table table-borderless">
                          <thead>
                            <tr class=""></tr>
                          </thead>
                          <tbody class="text-capitalize">
                            <tr>
                              <td>Bank Details</td>
                              <td>:</td>
                              <td>...</td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                  <div class="col-6">
                    <div class="card">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            Jobs
                          </h5>
                        </div>
                      </div>
                      <div class="card-body">
                        <div class="d-flex gap-2">
                          <button type="button" class="btn btn-primary btn-sm">
                            Assitance number
                          </button>
                          <button type="button" class="btn btn-primary btn-sm">
                            HCA
                          </button>
                          <button type="button" class="btn btn-primary btn-sm">
                            + Add
                          </button>
                        </div>
                      </div>
                    </div>
                    <div class="card rounded-0 mt-3">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            payroll
                          </h5>
                          <button
                            type="button"
                            class="btn btn-outline-primary mb-3"
                          >
                            Edit
                          </button>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table table-borderless">
                          <thead>
                            <tr class=""></tr>
                          </thead>
                          <tbody class="text-capitalize">
                            <tr>
                              <td>NI Number</td>
                              <td>:</td>
                              <td>LOG1CA1</td>
                            </tr>
                            <tr>
                              <td>Tax Code</td>
                              <td>:</td>
                              <td>PAYE</td>
                            </tr>
                            <tr>
                              <td>PAyroll ID</td>
                              <td>:</td>
                              <td>...</td>
                            </tr>
                            <tr>
                              <td>Status</td>
                              <td>:</td>
                              <td>This is my only job</td>
                            </tr>
                            <tr>
                              <td>Payroll Frequency</td>
                              <td>:</td>
                              <td>Monthly</td>
                            </tr>
                            <tr>
                              <td>Payroll Reference</td>
                              <td>:</td>
                              <td>...</td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>

                    <div class="card text-center mt-3">
                      <div class="card-header">
                        <div class="d-flex justify-content-between">
                          <div class="d-flex align-items-center">
                            <div class="d-flex fs-smaller text-nowrap">
                              Profile View
                            </div>
                            <label class="switch">
                              <input type="checkbox" id="togBtn" checked />
                              <div class="slider round"></div>
                            </label>
                          </div>

                          <div>
                            <button
                              type="button"
                              class="btn btn-outline-primary"
                            >
                              Edit
                            </button>
                          </div>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table table-borderless">
                          <thead>
                            <tr class=""></tr>
                          </thead>
                          <tbody class="text-capitalize">
                            <tr>
                              <td>social care wealth</td>
                              <td>:</td>
                              <td>2345678978</td>
                              <td>
                                <div class="d-flex justify-content-between">
                                  <div class="fs-smaller text-nowrap">
                                    Profile View
                                  </div>

                                  <input type="checkbox" id="togBtn" />
                                </div>
                              </td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="row mt-3">
                  <div class="col-12">
                    <div class="card">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            NEXT TO KIN
                          </h5>
                          <button type="button" class="btn btn-primary mb-3">
                            Edit
                          </button>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table">
                          <thead class="table-light">
                            <tr>
                              <th scope="col">Name</th>
                              <th scope="col">Phone</th>
                              <th scope="col">Relation</th>
                              <th scope="col">Address Line 1</th>
                              <th scope="col">Address Line 2</th>
                              <th scope="col">City</th>
                              <th scope="col">Post Code</th>
                              <th scope="col">Action</th>
                            </tr>
                          </thead>
                          <tbody>
                            ...
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="row mt-3">
                  <div class="col-12">
                    <div class="card">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            Work experience
                          </h5>
                          <button type="button" class="btn btn-primary mb-3">
                            + Add
                          </button>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table">
                          <thead class="table-light"></thead>
                          <tbody>
                            ...
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="row mt-3">
                  <div class="col-12">
                    <div class="card">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            Education
                          </h5>
                          <button type="button" class="btn btn-primary mb-3">
                            + Add
                          </button>
                        </div>
                      </div>
                      <div class="card-body">
                        <table class="table">
                          <thead class="table-light"></thead>
                          <tbody>
                            ...
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div
                class="tab-pane fade"
                id="pills-profile"
                role="tabpanel"
                aria-labelledby="document"
              >
                <div class="row">
                  <div class="col-12">
                    <ul
                      class="nav nav-pills mb-3"
                      id="pills-tab"
                      role="tablist"
                    >
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
                                <button
                                  type="button"
                                  class="btn btn-primary btn-sm"
                                >
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
                                <h2
                                  class="accordion-header"
                                  id="flush-headingOne"
                                >
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
                                            <label class="form-label"
                                              >ISSUE DATE</label
                                            >
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
                                            <label class="form-label"
                                              >EXPIRY DATE</label
                                            >
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
                                          <label class="form-label"
                                            >Description</label
                                          >
                                          <textarea
                                            class="form-control"
                                            rows="3"
                                            v-model="description"
                                          ></textarea>
                                        </div>
                                        <div class="mb-3">
                                          <label
                                            for="formFile"
                                            class="form-label"
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
                                        <button
                                          type="button"
                                          class="btn btn-primary"
                                        >
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
              <div
                class="tab-pane fade"
                id="pills-contact"
                role="tabpanel"
                aria-labelledby="profile"
              >
                ...
              </div>
              <div
                class="tab-pane fade"
                id="pills-restricted"
                role="tabpanel"
                aria-labelledby="restricted"
              >
                <div class="row">
                  <div class="col-12">
                    <div class="card">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between"
                        >
                          <h5
                            class="card-title text-uppercase fw-bold small d-flex align-items-center"
                          >
                            RESTRICTED SHIFTS
                          </h5>
                        </div>
                      </div>
                      <div class="card-body d-flex justify-content-between">
                        <div class="d-flex gap-3">
                          <ul v-for="shift in shifts" :key="shift.id">
                            <li>
                              <input
                                class="form-check-input"
                                type="checkbox"
                                v-model="selectedOptions"
                                :value="shift"
                              />&nbsp;{{ shift.shift_name }}
                            </li>
                          </ul>
                        </div>
                        <div class="d-flex gap-2 align-items-baseline">
                          <button
                            type="button"
                            class="btn btn-primary btn-sm"
                            v-on:click="getRestrictedShifts"
                          >
                            <i class="bi bi-file-earmark-medical"></i> Save
                          </button>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="row mt-3">
                  <div class="col-12">
                    <div class="card">
                      <div class="card-body">
                        <div
                          class="border-bottom d-flex justify-content-between align-items-center pb-3"
                        >
                          <h5 class="card-title text-uppercase fw-bold small">
                            RESTRICTED LOCATIONS (15)
                          </h5>
                          <div class="d-flex gap-2">
                            <button
                              type="button"
                              class="btn btn-primary btn-sm"
                            >
                              + Add
                            </button>
                          </div>
                        </div>
                      </div>
                      <div class="card-body">
                        <ul class="list-unstyled d-inline-flex gap-3">
                          <li>
                            <div
                              class="d-flex gap-3 justify-content-start border-box"
                            >
                              <div>
                                <div class="round">ABC</div>
                              </div>
                              <div>
                                <h5 class="fw-bold">ABC</h5>
                                <span>ABC</span>
                              </div>
                            </div>
                          </li>
                          <li>
                            <div
                              class="d-flex justify-content-start border-box"
                            >
                              <div>
                                <div class="hround">H1</div>
                              </div>
                              <div>
                                <h5 class="fw-bold">Hospital 1</h5>
                                <span>Hospital 1</span>
                              </div>
                            </div>
                          </li>
                          <li>
                            <div
                              class="d-flex justify-content-start border-box"
                            >
                              <div>
                                <div class="hround">H2</div>
                              </div>
                              <div>
                                <h5 class="fw-bold">Hospital 2</h5>
                                <span>Hospital 2</span>
                              </div>
                            </div>
                          </li>
                          <li>
                            <div
                              class="d-flex justify-content-start border-box"
                            >
                              <div>
                                <div class="dround">D</div>
                              </div>
                              <div>
                                <h5 class="fw-bold">Demo</h5>
                                <span>Demo</span>
                              </div>
                            </div>
                          </li>
                          <li>
                            <div
                              class="d-flex justify-content-start border-box"
                            >
                              <div>
                                <div class="round">ABC</div>
                              </div>
                              <div>
                                <h5 class="fw-bold">ABC</h5>
                                <span>ABC</span>
                              </div>
                            </div>
                          </li>
                        </ul>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div
                class="tab-pane fade"
                id="pills-ratecard"
                role="tabpanel"
                aria-labelledby="ratecard"
              >
                <div class="container-fluid p-0 bg-define">
                  <div
                    class="pagetitle d-flex justify-content-between align-items-center p-2"
                  >
                    <div class="d-flex justify-content-around gap-2"></div>

                    <div></div>

                    <div
                      class="d-flex align-items-center justify-content-between"
                    >
                      <div class="d-flex align-items-center gap-2">
                        <button
                          type="button"
                          class="btn btn-outline-success text-nowrap"
                          data-bs-toggle="modal"
                          data-bs-target="#rateCards"
                          data-bs-whatever="@mdo"
                          @click="showPopup()"
                        >
                          + Add Or Update Notes
                        </button>

                        <button
                          type="button"
                          class="btn btn-outline-success text-nowrap"
                        >
                          <i class="bi bi-funnel"></i>
                          Show Filters
                        </button>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="container-fluid mt-3">
                  <div class="row">
                    <div class="col-12">
                      <div class="">
                        <table class="table candidateTable">
                          <thead>
                            <tr>
                              <th scope="col">
                                Sl.No
                                <input
                                  class="form-check-input"
                                  type="checkbox"
                                  value=""
                                  id="flexCheckDefault"
                                />
                              </th>
                              <th scope="col">Business Unit</th>
                              <th scope="col">Position</th>
                              <th scope="col">Day</th>
                              <th scope="col">Employment Type</th>
                              <th scope="col">Shift Type Start End Time</th>
                              <th scope="col">Staff Rate</th>
                              <th scope="col">Last Update</th>
                              <th scope="col">Action</th>
                            </tr>
                          </thead>
                          <tbody>
                            <tr>
                              <td scope="row">
                                <div class="form-check">
                                  {{ index + 1 }}
                                  <input
                                    class="form-check-input"
                                    type="checkbox"
                                    value=""
                                    id="flexCheckDefault"
                                  />
                                </div>
                              </td>
                              <td></td>
                              <td></td>
                              <td></td>
                              <td></td>
                              <td></td>
                              <td></td>
                              <td></td>
                              <td class="cursor-pointer d-flex">
                                <i
                                  class="bi bi-trash3 cursor-pointer btn btn-outline-success text-nowrap"
                                ></i
                                >&nbsp;&nbsp;
                                <i
                                  type="button"
                                  class="bi bi-pencil-square cursor-pointer btn btn-outline-success text-nowrap"
                                  data-bs-toggle="modal"
                                  data-bs-target="#updateCandidate"
                                  data-bs-whatever="@mdo"
                                ></i>
                              </td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div
                class="tab-pane fade"
                id="pills-contact"
                role="tabpanel"
                aria-labelledby="notes"
              >
                ...
              </div>
              <div
                class="tab-pane fade"
                id="pills-contact"
                role="tabpanel"
                aria-labelledby="staff-id"
              >
                ...
              </div>
              <div
                class="tab-pane fade"
                id="pills-contact"
                role="tabpanel"
                aria-labelledby="candidate-history"
              >
                ...
              </div>
              <div
                class="tab-pane fade"
                id="pills-contact"
                role="tabpanel"
                aria-labelledby="candidate-reference"
              >
                ...
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Navbar from "../Navbar.vue";
// import Overview from "../CAndidates/ProfileDetail/Overview.vue";
// import Document from "../CAndidates/ProfileDetail/Document.vue";
// import Restricted from "../CAndidates/ProfileDetail/Restricted.vue";
// import RateCardTabs from "../CAndidates/ProfileDetail/RateCard.vue";

export default {
  name: "CandidateProfile",
  data() {
    return {
      getCandidates: [],
      restrictedShift: [],
      get_Candidate_Document_Categories: [],
      getCandidateData: [],

      selectedTab: null,
      // tabs: [
      //   { id: "tab1", label: "Tab 1", component: Restricted },
      //   { id: "tab2", label: "Tab 2", component: TabComponent2 },
      // ],
    };
  },
  props: ["id"],
  computed: {
    userId() {
      return this.id;
    },
  },
  component: {
    Navbar,
    // Overview,
    // Document,
    // Restricted,
    // RateCardTabs,
  },

  methods: {
    showPopup() {
      rateCards.show();
    },
    async getCandidate() {
      try {
        const response = await axios.get(
          `https://logezy.onrender.com/candidates/${this.$route.params.id}`
        );

        this.getCandidates = response.data.data;
        let candidate_id = this.$route.params.id;
        candidate_id = this.getCandidates.id;
        console.log(candidate_id);
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
    //  restricted  doc apis start
    async getTime() {
      await axios
        .get("https://logezy.onrender.com/shifts")
        .then((response) => (this.shifts = response.data));
    },

    async getRestrictedShifts() {
      await axios
        .post("https://logezy.onrender.com/restricted_shifts", {
          restrictedShift: this.restrictedShift,
        })
        .then((response) =>
          console.log("Options submitted successfully:", response.data)
        );
    },

    //  restricted  doc apis start

    //  ratecard apis end
  },
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

  mounted() {
    this.getCandidate();
    this.getTime();
  },
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
