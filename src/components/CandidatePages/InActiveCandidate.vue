<template>
  <div>
    <table class="table candidateTable">
      <thead>
        <tr v-for="datas in getCandidatesData" :key="datas">
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
        <tr>
          <td></td>
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
</template>

<style>
.candidateTable tr:nth-child(odd) td {
  background: #fdce5e17 !important;
}
a {
  color: black;
  text-decoration: none;
}
</style>

<script>
export default {
  name: "InActiveCandidate",
  data() {
    return {
      getCandidatesData: [],
    };
  },
  methods: {
    async getCandidate() {
      try {
        const response = await axios.get(
          "https://logezy.onrender.com/approve_and_notactivated_candidates"
        );

        this.getCandidatesData = response.data.data;
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
  },
  mounted() {
    this.getCandidate();
  },
};
</script>
