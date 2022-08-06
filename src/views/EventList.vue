<template>
  <div class="events">
    <EventCart v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCart from '@/components/EventCart.vue'
import EventService from '@/services/EventService.js'

export default {
  name: 'EventList',
  components: {
    EventCart
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents()
    .then(response => {
      this.events = response.data
    })
    .catch(error=>{
      console.log(error);
    })
  }
}
</script>

<style>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>