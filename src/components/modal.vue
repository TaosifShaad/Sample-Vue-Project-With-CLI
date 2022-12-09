<template>
    <div id="modal">
        <h2>You can check out any time you like!</h2>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: 'modal'
    }
</script>

<style scoped>
.modal {
    background: cyan;
    color: black;
    padding: 20px;
    margin-top: 200px;
    width: 200px;
    position: absolute;
    border: 2px solid black;
}
</style>
