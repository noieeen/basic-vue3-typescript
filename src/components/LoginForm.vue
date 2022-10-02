<template>
    <div>
            <h1>{{title}} World</h1>
    </div>

</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({

    props:['title'],

    setup(props) {
        return{}
    },
})
</script>
