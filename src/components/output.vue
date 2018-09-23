<template>
    <div id="translateOutput">
        <h2 class="text-success">{{translatedText}}</h2>
    </div>
</template>

<script>
export default {
    name: 'translateOutput',
    props: {
        translatedText: {
            type: String,
            require: true,
            default: ''
        }
    }
}
</script>

<style>

</style>
