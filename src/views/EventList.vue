<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard
      v-for="event in events"
      :key="event.id"
      :event="event"
    ></EventCard>
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'

export default {
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    }
  },
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data // For now, logs out the response
      })
      .catch((error) => {
        console.log('There was an error:', error.response) // Logs out the error
      })
  }
}
</script>

<style scoped></style>
