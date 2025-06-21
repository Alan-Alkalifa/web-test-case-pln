<template>
    <nav class="bg-gradient-to-r from-[#18A2BA] to-[#296377] flex items-center justify-between px-2 sm:px-4 py-2">
        <!-- Logo Section -->
        <div class="flex items-center gap-2 sm:gap-4">
            <img src="/src/components/icons/IconLogo.svg" alt="Logo" class="w-6 h-6 sm:w-8 sm:h-8">
            <h1 class="text-white text-sm sm:text-[16px] font-bold">iMeeting</h1>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden lg:flex items-center gap-4">
            <!-- Button Kotak Aduan - hanya muncul di route tertentu -->
            <button 
                v-if="showKotakAduanButton" 
                class="cursor-pointer flex gap-2 text-white text-[14px] font-semibold items-center bg-[#3D7D8F] p-3 rounded-xl hover:bg-[#2a5d6b] transition-colors">
                <img src="/src/components/icons/IconHorn.svg" alt="Icon Horn" class="w-4 h-4">
                Kotak Aduan
            </button>
            <button class="cursor-pointer hover:opacity-80 transition-opacity">
                <img src="/src/components/icons/IconNotifications.svg" alt="Notifications" class="w-6 h-6">
            </button>
            <button class="cursor-pointer hover:opacity-80 transition-opacity">
                <img src="/src/components/icons/IconAvatar.svg" alt="Avatar" class="w-8 h-8">
            </button>
            <h2 class="text-white text-[16px]">John Doe</h2>
            <button class="cursor-pointer hover:opacity-80 transition-opacity">
                <img src="/src/components/icons/IconDropDown.svg" alt="DropDown" class="w-4 h-4">
            </button>
        </div>

        <!-- Mobile Navigation -->
        <div class="flex lg:hidden items-center gap-2 sm:gap-3">
            <!-- Button Kotak Aduan untuk mobile - hanya muncul di route tertentu -->
            <button 
                v-if="showKotakAduanButton" 
                class="cursor-pointer flex items-center gap-1 text-white text-xs font-semibold bg-[#3D7D8F] px-2 py-1.5 rounded-lg hover:bg-[#2a5d6b] transition-colors">
                <img src="/src/components/icons/IconHorn.svg" alt="Icon Horn" class="w-3 h-3">
                <span class="hidden sm:inline">Aduan</span>
            </button>
            <button class="cursor-pointer hover:opacity-80 transition-opacity">
                <img src="/src/components/icons/IconNotifications.svg" alt="Notifications" class="w-5 h-5 sm:w-6 sm:h-6">
            </button>
            
            <!-- Mobile Menu Button -->
            <button @click="toggleMobileMenu" class="cursor-pointer hover:opacity-80 transition-opacity">
                <img src="/src/components/icons/IconAvatar.svg" alt="Avatar" class="w-6 h-6 sm:w-8 sm:h-8">
            </button>
        </div>

        <!-- Mobile Dropdown Menu -->
        <div v-if="showMobileMenu" class="absolute top-full left-0 right-0 bg-[#296377] lg:hidden border-t border-[#3D7D8F] z-50">
            <div class="px-4 py-3 border-b border-[#3D7D8F]">
                <div class="flex items-center gap-3">
                    <img src="/src/components/icons/IconAvatar.svg" alt="Avatar" class="w-8 h-8">
                    <h2 class="text-white text-sm font-medium">John Doe</h2>
                </div>
            </div>
            <div class="px-4 py-2">
                <button class="w-full text-left text-white text-sm py-2 hover:bg-[#3D7D8F] px-2 rounded transition-colors">
                    Profile Settings
                </button>
                <button class="w-full text-left text-white text-sm py-2 hover:bg-[#3D7D8F] px-2 rounded transition-colors">
                    Logout
                </button>
            </div>
        </div>
    </nav>
</template>

<script setup>
import { computed, ref, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const showMobileMenu = ref(false)

// Computed property untuk mengecek apakah button harus ditampilkan
const showKotakAduanButton = computed(() => {
    const allowedRoutes = ['/RuangMeeting', '/RuangMeeting/PesanRuangan']
    return allowedRoutes.includes(route.path)
})

// Toggle mobile menu
const toggleMobileMenu = () => {
    showMobileMenu.value = !showMobileMenu.value
}

// Close mobile menu when clicking outside
const handleClickOutside = (event) => {
    if (!event.target.closest('nav')) {
        showMobileMenu.value = false
    }
}

// Close mobile menu on route change
const closeMobileMenuOnRouteChange = () => {
    showMobileMenu.value = false
}

onMounted(() => {
    document.addEventListener('click', handleClickOutside)
})

onUnmounted(() => {
    document.removeEventListener('click', handleClickOutside)
})

// Watch for route changes to close mobile menu
import { watch } from 'vue'
watch(() => route.path, closeMobileMenuOnRouteChange)
</script>