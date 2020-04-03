<template>
  <div class="app">
    <date-picker :date="date"></date-picker>
  </div>
</template>
<script>
import DatePicker from './DatePicker'
export default {
  data() {
    return {
      date: new Date()
    }
  }
}
</script>
