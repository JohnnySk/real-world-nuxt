<template>
    <div>
        <h1>Event #{{id}}</h1>
        <div>{{event.title}}</div>
        <ul>
            <li v-for="(data, index) in event.user" :key="index">{{data}}</li>
        </ul>
    </div>
</template>
<script>
import {mapState} from 'vuex'
export default {
    async fetch({ store, params, error }) {
        try {
          await store.dispatch('events/fetchEvent', params.id)
        } catch (e) {
          error({
            statusCode: 503,
            message: 'Unable to fetch event #' + params.id
          })
        }
      },
    head () {
        return {
            title: `Create an Event ${this.event.title}`,
            meta: [ 
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Create Real world events for event with title:' + this.event.title
                }
            ]
        }
    },
    computed: mapState({
        event: state => state.events.event
    })
}
</script>