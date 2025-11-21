<script setup lang="ts">
import Charm from '../components/Charm.vue';
import RandomGopher from '../components/RandomGopher.vue';

</script>

<template>
    <div class="slidev-layout default">
        <slot/>
        <RandomGopher :gophers="['/images/gophers/1.png', '/images/gophers/2.png', '/images/gophers/3.png', '/images/gophers/20.png', '/images/gophers/21.png', '/images/gophers/33.png', '/images/gophers/41.png', '/images/gophers/50.png']"/>
    </div>
</template>