<script setup>
import { useRoute, useRouter } from 'vue-router';

const menus = [
    {
        label: 'Home',
        name: 'home'
    },
    {
        label: 'About',
        name: 'about'
    },
]

const router = useRouter();

function handleRoute(name) {
    router.push({name: name});
}

</script>

<template>
    <div>
        <div class="navbar bg-neutral text-neutral-content">
            <div class="flex-1">
                <a class="btn btn-ghost text-xl">Navbar</a>
            </div>

            <div class="flex-none">
                <ul class="menu menu-horizontal px-1">
                    <li v-for="menu in menus" :key="menu.route">
                        <button @click="handleRoute(menu.name)">
                            {{ menu.label }}
                        </button>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>