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
      child_item: { year: "", month: "", date: "", hour: "", min: "" },
    };
  },
  components: {
    Datepicker,
    VueTimepicker,
  },
  methods: {
    get_para(arg) {
      let year_d = String(arg.getFullYear());
      let month_d = arg.getMonth();
      let date_d = arg.getDate();
      let hour_d = arg.getHours();
      let min_d = arg.getMinutes();
      this.date_disp = year_d + "-" + (month_d + 1) + "-" + date_d;
      this.time_disp.HH = String(hour_d);
      this.time_disp.mm = String(min_d);
    },
    day_time_pick: function (child_item) {
      this.$emit("update", child_item);
    },
    dateHandler(arg) {
      this.child_item.year = String(arg.getFullYear());
      this.child_item.month = String(arg.getMonth() + 1);
      this.child_item.date = String(arg.getDate());
      this.$emit("update", this.child_item);
    },
    timeHandler(arg) {
      this.child_item.hour = String(arg.data.HH);
      this.child_item.min = String(arg.data.mm);
      this.$emit("update", this.child_item);
    },
  },
  mounted() {
    this.get_para(this.disp_time);
  },
};
</script>
