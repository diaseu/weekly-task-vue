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
import { format, startOfWeek, endOfWeek}  from 'date-fns'

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
      const currentday = format(today, 'MM/dd/yyyy')
      const start = format(startOfWeek(today), 'MMM dd')
      const end = format(endOfWeek(today), 'MMM dd, yy')
      const week = start + ' to ' + end
      // Date.protype.FirstDay = function() {
      //   return(new Date(this.setDate(this.getDate() - this.getDay()+ (this.getDay() == 0 ? -6:1) )))
      // }
      // Date.prototype.LastDay = function() {
      //   new Date(this.setDate(this.getDate() - this.getDay() +7))
      // }
      // const start = today.FirstDay;
      // const end = today.LastDay;
      // const week = start + ' to ' + end;
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