<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.data }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventServices from "@/services/EventServices";

export default {
  name: "EventDetails",
  props: ['id'],
  data: () => ({
    event: null,
  }),
  created() {
    EventServices.getEvent(this.id)
      .then(response => {
        this.event = response.data
      })
      .catch(error => {
        console.log(error);
      })
  }
};
</script>

<style scoped>

</style>