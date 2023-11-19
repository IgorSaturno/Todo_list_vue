<script setup>
    defineProps({
        msg: {
            type: String,
            required: true
        }
    })
</script>

<template>
    <div class="greetings">
        <h1 class="green">{{ msg }}</h1>
        <h3>Ge  t things done, one item at a time.</h3>
    </div>
</template>

<style scoped>
.greetings h1 {
    font-weight: 500;
    font-size: 2.6rem;
    position: relative;
    top: -10px;
}

.greetings h3 {
    font-size: 1.2rem;
    color: white;
}
</style>