<script setup>
    import { ref, computed } from 'vue'
    import PageGrafika from './components/page/PageGrafika.vue';
    import PagePočetna from './components/page/PagePočetna.vue';
    import PageSlika from './components/page/PageSlika.vue';

    import Footer from './components/structure/Footer.vue';
    import Header from './components/structure/Header.vue';
    import LinkItem from './components/structure/NavBar/LinkItem.vue'
    import NavBar from './components/structure/NavBar/NavBar.vue';

    const links = [
        { name: "POČETNA", active: true},
        { name: "SLIKA", active: true},
        { name: "ZVUK", active: false},
        { name: "GRAFIKA", active: true},
        { name: "MODEL", active: false},
        { name: "VIDEO", active: false}
    ];

    const activeLink = ref("POČETNA");
    const page = computed(() => {
        switch(activeLink.value) {
            case "POČETNA": return PagePočetna
            case "SLIKA": return PageSlika
            case "GRAFIKA": return PageGrafika
            default: return null;
            /* nije rečeno da napravim implementaciju za ove
            case "ZVUK": return
            case "MODEL": return
            case "VIDEO": return
            */
        }
    })
</script>

<template>

    <div class="fixed w-full h-full flex justify-center poppins text-sm text-indigo-300
        bg-gradient-to-b from-[#1B1A55] via-[#2B428D] to-[#3B39BB]">

        <div style="background-image: url('./src/assets/images/pattern.jpg'); 
            background-size: 200px;"
            class="fixed w-full h-full bg-repeat opacity-[3%] -z-10"></div>

        <div class="bg-[#535C91]/25 border-x border-[#9290C3]/10 w-[700px] max-w-[700px] shadow-lg
            flex flex-col justify-between px-8 gap-4 overflow-auto">
            
            <Header></Header>
            <NavBar :links="links" :active-link="activeLink" :link-click="(name) => {activeLink = name}"></NavBar>
            <component :is="page" />
            <Footer></Footer>
        </div>
    </div>
</template>