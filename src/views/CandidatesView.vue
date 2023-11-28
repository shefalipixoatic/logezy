<template>
  <div>
    <Navbar />
    <RateCard />

    <router-view />
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import RateCard from "../components/modals/CandidatePage/RateCard.vue";

export default {
  name: "CandidatesView",
  components: {
    Navbar,
    RateCard,
  },
};
</script>
