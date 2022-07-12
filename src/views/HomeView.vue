<template>
  <div>
    <h1>test</h1>
    <MyPicker
      :disp_time="start_date_time"
      v-on:update="setStartDateTime"
    ></MyPicker>
    <MyPicker
      :disp_time="end_date_time"
      v-on:update="setEndDateTime"
    ></MyPicker>
  </div>
</template>
<script>
import MyPicker from "../components/MyPicker.vue";
export default {
  data() {
    return {
      // end_date_time: new Date(),
      end_date_time: "",
      start_date_time: "",
      st_time: { year: "", month: "", date: "", hour: "", min: "" },
      end_time: { year: "", month: "", date: "", hour: "", min: "" },
    };
  },
  components: {
    MyPicker,
  },
  methods: {
    ret_time: function () {
      let ddd = new Date();
      return ddd;
    },
    setStartDateTime: function (arg) {
      console.log(arg);
      this.st_time.year = arg.year;
      this.st_time.month = arg.month;
      this.st_time.date = arg.date;
      this.st_time.hour = arg.hour;
      this.st_time.min = arg.min_d;
      console.log(this.st_time.year);
      console.log(this.st_time.month);
      console.log(this.st_time.date);
      console.log(this.st_time.hour);
      console.log(this.st_time.min);
    },
    setEndDateTime: function (arg) {
      console.log(arg);
      this.end_time.year = arg.year;
      this.end_time.month = arg.month;
      this.end_time.date = arg.date;
      this.end_time.hour = arg.hour;
      this.end_time.min = arg.min;
      console.log(this.st_time.year);
      console.log(this.st_time.month);
      console.log(this.st_time.date);
      console.log(this.st_time.hour);
      console.log(this.st_time.min);
    },
  },
  created() {
    this.end_date_time = new Date();
    this.start_date_time = new Date(this.end_date_time - 3600000);
  },
};
</script>
