<template>
  <div>
    <Datepicker
      :value="date_disp"
      :format="date_format"
      @input="dateHandler"
    ></Datepicker>
    <VueTimepicker
      v-model="time_disp"
      :format="time_format"
      @close="timeHandler"
    ></VueTimepicker>
    <p>{{ disp_time }}</p>
  </div>
</template>
<script>
import Datepicker from "vuejs-datepicker";
import VueTimepicker from "vue2-timepicker/src/vue-timepicker.vue";
import "vue2-timepicker/dist/VueTimepicker.css";
export default {
  props: ["disp_time"],
  data() {
    return {
      date_disp: "",
      date_format: "yyyy-MM-dd",
      time_format: "HH:mm",
      time_disp: { HH: "", mm: "" },
      disp_time2: "",
      child_item: { y_d: "", mon_d: "", d_d: "", h_d: "", min_d: "" },
    };
  },
  components: {
    Datepicker,
    VueTimepicker,
  },
  methods: {
    get_para(arg) {
      let year_d = arg.getFullYear();
      let month_d = arg.getMonth();
      let date_d = arg.getDate();
      let hour_d = arg.getHours();
      let min_d = arg.getMinutes();
      this.date_disp =
        year_d + "-" + ("00" + (month_d + 1)).slice(-2) + "-" + date_d;
      this.time_disp.HH = "" + ("00" + hour_d).slice(-2);
      this.time_disp.mm = "" + ("00" + min_d).slice(-2);
    },
    day_time_pick: function (child_item) {
      this.$emit("update", child_item);
    },
    dateHandler(arg) {
      this.child_item.y_d = arg.getFullYear();
      this.child_item.mon_d = arg.getMonth() + 1;
      this.child_item.d_d = arg.getDate();
      this.$emit("update", this.child_item);
    },
    timeHandler(arg) {
      this.child_item.h_d = arg.data.HH;
      this.child_item.min_d = arg.data.mm;
      this.$emit("update", this.child_item);
    },
  },
  mounted() {
    this.get_para(this.disp_time);
  },
};
</script>
