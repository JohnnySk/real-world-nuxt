<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <h1>{{name}}</h1>
  </div>
</template>

<script>
export default {
    data () {
        return {
            name: 'Create Events'
        }
    },
    head () {
        return {
            title: 'Create an Event',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Create Real world events'
                }
            ]
        }
    }
}
</script>
