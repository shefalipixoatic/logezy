<template>
  <div>
    <Navbar />
    <RateCard />
    <CandidateAdd />
    <AddRestrictedLocation />
    <OverviewEdit />
    <RestrictShift />
    <router-view />
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import RateCard from "../components/modals/CandidatePage/RateCard.vue";
import CandidateAdd from "../components/modals/CandidatePage/CandidateAdd.vue";
import AddRestrictedLocation from "../components/modals/CandidatePage/AddRestrictedLocation.vue";
import OverviewEdit from "../components/modals/CandidatePage/OverviewEdit.vue";
import RestrictShift from "../components/modals/CandidatePage/RestrictShift.vue";
export default {
  name: "CandidatesView",
  components: {
    Navbar,
    RateCard,
    CandidateAdd,
    AddRestrictedLocation,
    OverviewEdit,
    RestrictShift,
  },
};
</script>
