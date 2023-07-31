<template>
    <div v-if="currentUser.id" class="min-h-full flex bg-gray-200">
        <!--Sidebar-->
        <Sidebar :class="{ '-ml-[200px]': !sidebarOpened }"></Sidebar>
        <!--/Sidebar-->
        <div class="flex-1">
            <Navbar @toggle-sidebar="toggleSidebar"></Navbar>
            <!--Content-->
            <main class="p-6">
                <div class="p-4 rounded bg-white">
                    <router-view></router-view>
                </div>
            </main>
            <!--/Content-->
        </div>

    </div>
    <div v-else class=" items-center justify-center flex h-full bg-gray-200">
        <Spinner></Spinner>
    </div>
</template>
<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';
const sidebarOpened = ref(true);
const currentUser = computed(() => store.state.user.data);
import Sidebar from "./Sidebar.vue";
import Navbar from "./Navbar.vue";
import store from '../store';
import Spinner from './core/Spinner.vue';
const { title } = defineProps({
    title: String
})


function toggleSidebar() {
    sidebarOpened.value = !sidebarOpened.value;
}
onMounted(() => {
    store.dispatch('getUser');
    handleSidebarOpened();
    window.addEventListener('resize', handleSidebarOpened);
});
onUnmounted(() => {

    window.addEventListener('resize', handleSidebarOpened);
});
function handleSidebarOpened() {
    sidebarOpened.value = window.outerWidth > 768;

}
</script>
  