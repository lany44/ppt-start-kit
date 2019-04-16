<template>
    <div class="container">
        <p>{{ count }}</p>
        <button @click="handleOnIncrease">Increase</button>
    </div>
</template>

<script>

export default {
    name: 'increase',
    data() {
        return {
            count: 0
        }
    },
    methods: {
        handleOnIncrease() {
            this.count++
        }
    }
}

</script>

<style lang="sass" scoped>
.container {
    color: 'red'
}
</style>

