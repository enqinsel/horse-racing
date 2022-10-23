<script setup>
const props = defineProps(["result"])
</script>

<template>
    <div>
        <ul>
            <li>{{props.result}}</li>
        </ul>
    </div>
</template>