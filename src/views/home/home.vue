<template>
  <div>
    <base-calendar v-model="time"></base-calendar>
  </div>
</template>

<script>
import BaseCalendar from '@/components/baseCalendar/baseCalendar'

export default {
  components: {
    BaseCalendar
  },

  data () {
    return {
      time: new Date()
    }
  }
}
</script>
