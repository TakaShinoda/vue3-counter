<template>
    name: {{ user.firstName }}{{ user.lastName }}
</template>

<script>
import { inject } from 'vue'
export default {
    setup() {
        const user = inject('unique')

        return {
            user
        }
    }
}
</script>