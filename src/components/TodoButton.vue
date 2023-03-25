<script setup>

</script>
<template>
        <button>
            <slot>Create</slot>
        </button>
</template>


<style lang="scss" scoped>
button {
    margin-left: .3rem;
    border-radius: 5px;
    white-space: nowrap;
    padding: 8px 23px;
    border: none;
    text-transform: capitalize;
}
</style>