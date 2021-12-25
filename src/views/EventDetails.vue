<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js';

export default {
  props: ['id'],
  data() {
    return {
      event: null,
    };
  },
  async created() {
    try {
      const res = await EventService.getEvent(this.id);
      this.event = res.data;
    } catch (e) {
      console.log(e);
    }
  },
};
</script>
