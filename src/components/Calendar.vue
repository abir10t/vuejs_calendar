<template>
  <div class="m-auto">
    <h1 class="text-2xl my-2 text-center">Vue calander</h1>
    <section class="flex justify-between">
      <h2 style="font-weight:bold" >{{ currentmonthname }}</h2>
      <h2 style="font-weight:bold">{{ currentYear }}</h2>
    </section>

    <section class="flex my-2">
      <p
        class="text-center"
        style="width:14.28%"
        v-for="day in days"
        :key="day"
      >
        {{ day }}
      </p>
    </section>
    <section class="flex flex-wrap">
      <p
        class="text-center"
        style="width: 14.28%"
        v-for="num in startDay()"
        :key="num"
      ></p>

      <p
        class="text-center"
        style="width: 14.28%"
        v-for="num in daysinmonth()"
        :key="num"
        :class="currenDateClass(num)"
      >
        {{ num }}
      </p>
    </section>
    <section class="flex justify-between my-4">
      <button class="px-2 border rounded" @click="prev()">prev</button>
      <button class="px-2 border rounded" @click="next()">next</button>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
    };
  },
  methods: {
    daysinmonth() {
      return new Date(this.currentYear, this.currentMonth+1, 0).getDate();
    },

    startDay() {
      return new Date(this.currentYear, this.currentMonth, 1).getDay();
    },
    next() {
      if (this.currentMonth === 11) {
        this.currentMonth = 0;
        this.currentYear++;
      } else {
        this.currentMonth++;
      }
    },
    prev() {
      if (this.currentMonth === 0) {
        this.currentMonth = 11;
        this.currentYear--;
      } else {
        this.currentMonth--;
      }
    },
    currenDateClass(num){
       const calenderFullDate = new Date(
         this.currentYear,
         this.currentMonth,
         num
       ).toDateString();
      

      const currentFullDate = new Date().toDateString();
      

      return calenderFullDate == currentFullDate ? ' text-yellow-600': ''
    }
  },
  computed: {
    currentmonthname() {
      return new Date(
        this.currentYear,
        this.currentMonth
      ).toLocaleString("default", { month: "long" });
    },
  },
};
</script>

<style></style>
