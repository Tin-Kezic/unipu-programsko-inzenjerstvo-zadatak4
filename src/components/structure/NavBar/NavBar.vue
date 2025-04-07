<script setup>
    import LinkItem from './LinkItem.vue';
    const props = defineProps(['links', 'activeLink', 'linkClick'])
</script>
<template>
    <nav class="sticky top-0 w-full flex gap-4 flex-wrap items-center justify-around bg-[#070F2B]/25 backdrop-blur-sm py-2 px-8 rounded-lg">
        <div v-for="link in $props.links"
            class="text-sm z-10 relative transition" @click="$props.linkClick(link.name)"
            :class="[
                link.name == $props.activeLink ? 'underline text-purple-100' :
                'cursor-pointer text-indigo-300 text-sm hover:text-indigo-200 hover:scale-105', 
                link.active ? '' : 'text-indigo-500/50 text-sm pointer-events-none font line-through'
                ]">

            <LinkItem :name="link.name" :active-link="$props.activeLink"></LinkItem>
        </div>
    </nav>
</template>