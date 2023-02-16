<template>
    <Head>
        <title>Welcome to laravel + quasar</title>
    </Head>
    <Layout>
        <q-page class="column flex-center">
            <div class="flex q-gutter-lg">
                <q-img
                    width="100px"
                    src="https://cdn.quasar.dev/logo-v2/svg/logo.svg"
                    alt="Quasar Logo"
                />
                <q-img
                    width="100px"
                    src="https://laravel.com/img/logomark.min.svg"
                    alt="Laravel Logo"
                />
            </div>

            <div class="q-mt-xl">
                <q-btn
                    color="primary"
                    dense
                    round
                    label="-"
                    :disable="count === min"
                    @click="count--"
                />

                <span class="q-mx-md text-bold">{{ count }}</span>

                <q-btn
                    color="primary"
                    dense
                    round
                    label="+"
                    :disable="count === max"
                    @click="count++"
                />
            </div>

            <div class="q-mt-md" style="width: 200px">
                <q-slider v-model="count" :min="min" :max="max" />
            </div>
        </q-page>
    </Layout>
</template>
<script setup>
import Layout from "../layouts/MainLayout.vue";
import { ref } from "vue";
import { Head } from "@inertiajs/vue3";

const count = ref(0);

const min = -5;
const max = 5;
</script>
