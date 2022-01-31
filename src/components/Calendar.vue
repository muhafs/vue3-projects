<template>
  <div class="row justify-content-center">
    <div class="col-6">
      <h1 class="display-3 text-center mb-2">Calendar</h1>

      <section class="d-flex justify-content-between px-4">
        <h2 class="text-center">{{ currentMonthName }}</h2>
        <h2 class="text-center">{{ currentYear }}</h2>
      </section>

      <section class="d-flex justify-content-between mb-2">
        <button class="btn btn-primary px-5" @click="prevMonth()">Prev</button>
        <button class="btn btn-primary px-5" @click="nextMonth()">Next</button>
      </section>

      <main class="bg-secondary p-3 rounded text-white">
        <section class="d-flex justify-content-center my-3">
          <p
            class="fs-5 text-center"
            style="width: 14.28%"
            v-for="day in days"
            :key="day"
          >
            {{ day }}
          </p>
        </section>

        <section class="d-flex justify-content-start flex-wrap">
          <p
            class="fs-5 text-center"
            style="width: 14.28%"
            v-for="num in startDay()"
            :key="num"
          ></p>
          <p
            class="fs-5 text-center"
            style="width: 14.28%"
            v-for="num in monthInDays()"
            :key="num"
            :class="currentDateClass(num)"
          >
            {{ num }}
          </p>
        </section>
      </main>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
      currentDate: new Date().getUTCDay()
    }
  },
  methods: {
    monthInDays() {
      return new Date(this.currentYear, this.currentMonth + 1, 0).getDate()
    },
    startDay() {
      return new Date(this.currentYear, this.currentMonth, 1).getDay()
    },
    nextMonth() {
      if (this.currentMonth == 11) {
        this.currentMonth = 0
        this.currentYear++
      } else {
        this.currentMonth++
      }
    },
    prevMonth() {
      if (this.currentMonth == 0) {
        this.currentMonth = 11
        this.currentYear--
      } else {
        this.currentMonth--
      }
    },
    currentDateClass(num) {
      const fullCalendar = new Date(
        this.currentYear,
        this.currentMonth,
        num
      ).toDateString()
      const currentCalendar = new Date().toDateString()
      return fullCalendar === currentCalendar ? 'text-light badge bg-dark' : ''
    }
  },
  computed: {
    currentMonthName() {
      return new Date(this.currentYear, this.currentMonth).toLocaleString(
        'default',
        { month: 'long' }
      )
    }
  }
}
</script>

<style></style>
