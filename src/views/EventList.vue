<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue';
import EventService from '@/services/EventService.js';

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    };
  },
  async created() {
    try {
      const res = await EventService.getEvents();
      this.events = res.data;
    } catch (e) {
      console.log(e);
    }
  },
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
