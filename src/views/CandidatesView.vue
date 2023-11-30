<template>
  <div>
    <Navbar />
    <RateCard />
    <CandidateAdd />
    <router-view />
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import RateCard from "../components/modals/CandidatePage/RateCard.vue";
import CandidateAdd from "../components/modals/CandidatePage/CandidateAdd.vue";
export default {
  name: "CandidatesView",
  components: {
    Navbar,
    RateCard,
    CandidateAdd,
  },
};
</script>
