<template>
  <header>
    <div>
      <h1>{{ title }}</h1> 
      <h3>{{ weekDate() }}</h3>   
    </div>
    
    <!-- <h2>Task Tracker</h2> -->
    <!-- <img alt="Vue logo" src="../assets/logo.png" style="max-width: 50px;"> -->
    <Button @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" />
  </header>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  components: {
    Button
  },
  props: {
    title: String,
    showAddTask: Boolean
  },
  methods: {
    // printFullDate: function() {
    //   return new Date();
    // },
    currentDate() {
      const today = new Date();
      const formatToday = today.toLocaleDateString("en-US", { month: 'short' }) + " " + today.toLocaleDateString("en-US", { day: 'numeric' }) + ", " + today.toLocaleDateString("en-US", { year: 'numeric' });
      return formatToday;
    },
    weekDate() {
      const today = new Date();
      const start = today.getDate() - today.getDay();
      // const startday = new Date(today.setDate(start)).toLocaleDateString("en-US");
      const startday = new Date(today.setDate(start));
      const end = start+6
      const endday = new Date(today.setDate(end)+1);
      const test = endday.toLocaleDateString("en-US", { month: 'short' })
      const week = startday.toLocaleDateString("en-US", { month: 'short' }) + " " + startday.toLocaleDateString("en-US", { day: 'numeric' }) + ", " + startday.toLocaleDateString("en-US", { year: 'numeric' }) + " to " + endday.toLocaleDateString("en-US", { month: 'short' }) + " " + endday.toLocaleDateString("en-US", { day: 'numeric' }) + ", " + endday.toLocaleDateString("en-US", { year: 'numeric' })
      return week;
    },
    testDate: function() {
      var current = new Date();
      const entireWeek = Date.getDay();
      // const entireWeek = moment.localeData().format("MMMM D -") + moment.localeData().add(7, 'days').format("D YYYY")
      return current; // ex July 1 - 7 2021
    }
  },
  mounted: function () {
    this.fulldatetime = this.printFullDate();
  }
}
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>