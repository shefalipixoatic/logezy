<!-- Datepicker.vue -->
<template>
  <div class="datepicker-container">
    <label for="datepicker">
      <i class="fa fa-calendar"></i>
      <datepicker
        id="datepicker"
        v-model="selectedDate"
        :format="datepickerFormat"
        @input="handleDateChange"
      ></datepicker>
    </label>
    <p>Selected Date: {{ formattedDate }}</p>
  </div>
</template>

<script>
import Datepicker from "vue-datepicker";

export default {
  components: {
    Datepicker,
  },
  data() {
    return {
      selectedDate: null,
      datepickerFormat: "yyyy-MM-dd", // Adjust the format as needed
    };
  },
  computed: {
    formattedDate() {
      // Format the selected date for display
      return this.selectedDate
        ? this.$options.filters.date(this.selectedDate, "yyyy-MM-dd")
        : "";
    },
  },
  methods: {
    handleDateChange() {},
  },
};
</script>

<style scoped>
/* Add your custom styles here */
.datepicker-container {
  display: flex;
  align-items: center;
}

label {
  position: relative;
  display: flex;
  align-items: center;
}

i {
  position: absolute;
  left: 10px;
  font-size: 18px;
  color: #ccc;
}

p {
  margin-top: 10px;
}
.datepicker-overlay {
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 998;
  top: 0;
  left: 0;
  overflow: hidden;
  -webkit-animation: fadein 0.5s;
  /* Safari, Chrome and Opera > 12.1 */
  -moz-animation: fadein 0.5s;
  /* Firefox < 16 */
  -ms-animation: fadein 0.5s;
  /* Internet Explorer */
  -o-animation: fadein 0.5s;
  /* Opera < 12.1 */
  animation: fadein 0.5s;
}
@keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/* Firefox < 16 */
@-moz-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/* Safari, Chrome and Opera > 12.1 */
@-webkit-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/* Internet Explorer */
@-ms-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/* Opera < 12.1 */
@-o-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.cov-date-body {
  background: #3f51b5;
  overflow: hidden;
  font-size: 16px;
  font-family: "Roboto";
  font-weight: 400;
  position: fixed;
  display: block;
  width: 400px;
  max-width: 100%;
  z-index: 999;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.2);
}
.cov-picker-box {
  background: #fff;
  width: 100%;
  display: inline-block;
  padding: 25px;
  box-sizing: border-box !important;
  -moz-box-sizing: border-box !important;
  -webkit-box-sizing: border-box !important;
  -ms-box-sizing: border-box !important;
  width: 400px;
  max-width: 100%;
  height: 280px;
  text-align: start !important;
}
.cov-picker-box td {
  height: 34px;
  width: 34px;
  padding: 0;
  line-height: 34px;
  color: #000;
  background: #fff;
  text-align: center;
  cursor: pointer;
}
.cov-picker-box td:hover {
  background: #e6e6e6;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
  width: 100%;
}
.day {
  width: 14.2857143%;
  display: inline-block;
  text-align: center;
  cursor: pointer;
  height: 34px;
  padding: 0;
  line-height: 34px;
  color: #000;
  background: #fff;
  vertical-align: middle;
}
.week ul {
  margin: 0 0 8px;
  padding: 0;
  list-style: none;
}
.week ul li {
  width: 14.2%;
  display: inline-block;
  text-align: center;
  background: transparent;
  color: #000;
  font-weight: bold;
}
.passive-day {
  color: #bbb;
}
.checked {
  background: #f50057;
  color: #fff !important;
  border-radius: 3px;
}
.unavailable {
  color: #ccc;
  cursor: not-allowed;
}
.cov-date-monthly {
  height: 150px;
}
.cov-date-monthly > div {
  display: inline-block;
  padding: 0;
  margin: 0;
  vertical-align: middle;
  color: #fff;
  height: 150px;
  float: left;
  text-align: center;
  cursor: pointer;
}
.cov-date-previous,
.cov-date-next {
  position: relative;
  width: 20% !important;
  text-indent: -300px;
  overflow: hidden;
  color: #fff;
}
.cov-date-caption {
  width: 60%;
  padding: 50px 0 !important;
  box-sizing: border-box;
  font-size: 24px;
}
.cov-date-caption span:hover {
  color: rgba(255, 255, 255, 0.7);
}
.cov-date-previous:hover,
.cov-date-next:hover {
  background: rgba(255, 255, 255, 0.1);
}
.day:hover {
  background: #eaeaea;
}
.unavailable:hover {
  background: none;
}
.checked:hover {
  background: #ff4f8e;
}
.cov-date-next::before,
.cov-date-previous::before {
  width: 20px;
  height: 2px;
  text-align: center;
  position: absolute;
  background: #fff;
  top: 50%;
  margin-top: -7px;
  margin-left: -7px;
  left: 50%;
  line-height: 0;
  content: "";
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  transform: rotate(45deg);
}
.cov-date-next::after,
.cov-date-previous::after {
  width: 20px;
  height: 2px;
  text-align: center;
  position: absolute;
  background: #fff;
  margin-top: 6px;
  margin-left: -7px;
  top: 50%;
  left: 50%;
  line-height: 0;
  content: "";
  -webkit-transform: rotate(-45deg);
  -moz-transform: rotate(-45deg);
  transform: rotate(-45deg);
}
.cov-date-previous::after {
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  transform: rotate(45deg);
}
.cov-date-previous::before {
  -webkit-transform: rotate(-45deg);
  -moz-transform: rotate(-45deg);
  transform: rotate(-45deg);
}
.date-item {
  text-align: center;
  font-size: 20px;
  padding: 10px 0;
  cursor: pointer;
}
.date-item:hover {
  background: #e0e0e0;
}
.date-list {
  overflow: auto;
  vertical-align: top;
  padding: 0;
}
.cov-vue-date {
  display: inline-block;
  color: #5d5d5d;
}
.button-box {
  background: #fff;
  vertical-align: top;
  height: 50px;
  line-height: 50px;
  text-align: right;
  padding-right: 20px;
}
.button-box span {
  cursor: pointer;
  padding: 10px 20px;
}
.watch-box {
  height: 100%;
  overflow: hidden;
}
.hour-box,
.min-box {
  display: inline-block;
  width: 50%;
  text-align: center;
  height: 100%;
  overflow: auto;
  float: left;
}
.hour-box ul,
.min-box ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.hour-item,
.min-item {
  padding: 10px;
  font-size: 36px;
  cursor: pointer;
}
.hour-item:hover,
.min-item:hover {
  background: #e3e3e3;
}
.hour-box .active,
.min-box .active {
  background: #f50057;
  color: #fff !important;
}
::-webkit-scrollbar {
  width: 2px;
}
::-webkit-scrollbar-track {
  background: #e3e3e3;
}
::-webkit-scrollbar-thumb {
  background: #c1c1c1;
  border-radius: 2px;
}
</style>
