<template>
  <nav class="w-full h-full flex flex-col sm:flex-row mx-3 sm:mx-5 my-3 sm:my-5 justify-between items-start sm:items-center gap-3 sm:gap-0">
    <!-- Title Section -->
    <div class="flex-1">
      <h1 class="text-black text-xl sm:text-2xl lg:text-[28px] font-extrabold leading-tight">
        Ruang Meeting
      </h1>
      <h2 class="text-[#4A8394] text-xs sm:text-sm lg:text-[14px] font-normal mt-1">
        Ruang Meeting
      </h2>
    </div>
    
    <!-- Button Section -->
    <div class="w-full sm:w-auto">
      <RouterLink 
        to="/RuangMeeting/PesanRuangan" 
        class="w-full sm:w-auto inline-flex items-center justify-center bg-[#4A8394] hover:bg-[#3a6b7a] active:bg-[#2f5660] px-4 py-3 text-white rounded-xl transition-all duration-200 ease-in-out transform hover:scale-105 active:scale-95 shadow-md hover:shadow-lg"
      >
        <span class="text-sm lg:text-[14px] font-semibold whitespace-nowrap">
          + Pesan Ruangan
        </span>
      </RouterLink>
    </div>
  </nav>
</template>