<template>
    <nav class="bg-gradient-to-r from-[#18A2BA] to-[#296377] flex items-center justify-between px-4 py-2">
        <div class="flex items-center gap-4">
            <img src="/src/components/icons/IconLogo.svg" alt="Logo">
            <h1 class="text-white text-[16px] font-bold">iMeeting</h1>
        </div>
        <div class="flex items-center gap-4">
            <!-- Button Kotak Aduan - hanya muncul di route tertentu -->
            <button 
                v-if="showKotakAduanButton" 
                class="cursor-pointer flex gap-4 text-white text-[14px] font-semibold items-center bg-[#3D7D8F] p-3 rounded-xl">
                <img src="/src/components/icons/IconHorn.svg" alt="Icon Horn">
                Kontak Aduan
            </button>
            <button class="cursor-pointer">
                <img src="/src/components/icons/IconNotifications.svg" alt="Notifications">
            </button>
            <button class="cursor-pointer">
                <img src="/src/components/icons/IconAvatar.svg" alt="Avatar">
            </button>
            <h2 class="text-white text-[16px]">John Doe</h2>
            <button class="cursor-pointer">
                <img src="/src/components/icons/IconDropDown.svg" alt="DropDown">
            </button>
        </div>
    </nav>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

// Computed property untuk mengecek apakah button harus ditampilkan
const showKotakAduanButton = computed(() => {
    const allowedRoutes = ['/RuangMeeting', '/RuangMeeting/PesanRuangan']
    return allowedRoutes.includes(route.path)
})
</script>