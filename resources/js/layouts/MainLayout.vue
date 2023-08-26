<template>
    <q-layout view="lHh Lpr lFf">
        <q-header elevated>
            <q-toolbar>
                <q-btn
                    flat
                    dense
                    round
                    icon="menu"
                    aria-label="Menu"
                    @click="toggleLeftDrawer"
                />

                <q-toolbar-title>Laravel + Vite + Quasar</q-toolbar-title>

                <div>Quasar v{{ $q.version }}</div>
            </q-toolbar>
        </q-header>

        <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
            <q-list>
                <q-item-label header>Essential Links</q-item-label>

                <EssentialLink
                    v-for="link in essentialLinks"
                    :key="link.title"
                    v-bind="link"
                />
            </q-list>
        </q-drawer>

        <q-page-container>
            <slot />
        </q-page-container>
    </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "../components/EssentialLink.vue";

const linksList = [
    {
        title: "Github",
        caption: "https://github.com/laraquasar",
        icon: "code",
        link: "https://github.com/laraquasar",
    },
    {
        title: "Packagist",
        caption: "https://packagist.org/packages/laraquasar/laraquasar",
        icon: "code",
        link: "https://packagist.org/packages/laraquasar/laraquasar",
    },
    {
        title: "Docs Quasar",
        caption: "quasar.dev",
        icon: "school",
        link: "https://quasar.dev",
    },
    {
        title: "Docs Laravel",
        caption: "laravel.com/docs",
        icon: "school",
        link: "https://laravel.com/docs",
    },
];

export default defineComponent({
    name: "MainLayout",

    components: {
        EssentialLink,
    },

    setup() {
        const leftDrawerOpen = ref(false);

        return {
            essentialLinks: linksList,
            leftDrawerOpen,
            toggleLeftDrawer() {
                leftDrawerOpen.value = !leftDrawerOpen.value;
            },
        };
    },
});
</script>
