<template>
  <div>
    <h1>test</h1>
    <MyPicker :disp_time="current_time" v-on:update="getDayTime"></MyPicker>
  </div>
</template>
<script>
import MyPicker from "../components/MyPicker.vue";
export default {
  data() {
    return {
      current_time: new Date(),
      st_time: { year: "", month: "", date: "", hour: "", min: "" },
      end_time: { year: "", month: "", date: "", hour: "", min: "" },
    };
  },
  components: {
    MyPicker,
  },
  methods: {
    getDayTime: function (arg) {
      console.log(arg);
      this.st_time.year = arg.y_d;
      this.st_time.month = arg.mon_d;
      this.st_time.date = arg.d_d;
      this.st_time.hour = arg.h_d;
      this.st_time.min = arg.min_d;
      console.log(this.st_time.year);
      console.log(this.st_time.month);
      console.log(this.st_time.date);
      console.log(this.st_time.hour);
      console.log(this.st_time.min);
    },
  },
};
</script>
