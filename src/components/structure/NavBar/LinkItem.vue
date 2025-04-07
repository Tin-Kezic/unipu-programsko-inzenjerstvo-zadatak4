<script>
    const props = defineProps(['name', 'activeLink'])
</script>

<template>
    {{ $props.name }} 
    <b v-if="$props.name == $props.activeLink" class="text-purple-400 -z-[5] absolute -left-0.5 blur-sm">
        {{ $props.name }}
    </b>
</template>