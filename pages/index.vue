<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <h1>{{name}}</h1>
    <EventCard
          v-for="(event, index) in events"
          :key="index"
          :event="event"
          :data-index="index"
        />
  </div>
</template>

<script>
import {mapState} from 'vuex'
import EventCard from '@/components/EventCard.vue'
export default {
    components: {
      EventCard
    },
    data () {
        return { 
            name: 'Events'
        }
    },
  async fetch({store, error}) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch(e) {
        error({
          statusCode: 503,
          message: "Data can't be fetched"
        });
    }
    },
    head () {
        return {
            title: 'Event Listing'
        }
    },
    computed: mapState({
      events: state => state.events.events 
    })
}
</script>
