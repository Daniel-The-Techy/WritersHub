<template>
    
    <header
      class="flex items-center justify-between px-6 py-4 bg-white shadow-lg border-b-4 border-indigo-600"
    >
       <div class="logo">
        <h3 class="text-2xl font-bold text-gray-700">Writers<span class="text-base text-emerald-800 ">Hub</span></h3>
       </div>
      <div class="flex justify-between items-center">
        

      
        <div class="relative mx-4 lg:mx-0 xs:hidden">
          <span class="absolute inset-y-0 left-0 sm:flex items-center hidden pl-3">
            <svg class="w-5 h-5 text-gray-500" viewBox="0 0 24 24" fill="none">
              <path
                d="M21 21L15 15M17 10C17 13.866 13.866 17 10 17C6.13401 17 3 13.866 3 10C3 6.13401 6.13401 3 10 3C13.866 3 17 6.13401 17 10Z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </span>
  
          <input
            class="w-full pl-10 hidden sm:block pr-4 text-indigo-600 border-gray-200 rounded-md sm:w-64 focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
            type="text"
            placeholder="Search"
          />
        </div>
      </div>
  
      <div class="flex items-center">
       
        <div class="relative">
          <button
            @click="dropdownOpen = !dropdownOpen"
            class="relative z-10 block w-8 h-8 overflow-hidden rounded-full shadow focus:outline-none"
          >
            <img
              class="object-cover w-full h-full"
              src="https://images.unsplash.com/photo-1528892952291-009c663ce843?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=296&q=80"
              alt="Your avatar"
            />
          </button>
  
          <div
            v-show="dropdownOpen"
            @click="dropdownOpen = false"
            class="fixed inset-0 z-10 w-full h-full"
          ></div>
  
          <transition
            enter-active-class="transition duration-150 ease-out transform"
            enter-from-class="scale-95 opacity-0"
            enter-to-class="scale-100 opacity-100"
            leave-active-class="transition duration-150 ease-in transform"
            leave-from-class="scale-100 opacity-100"
            leave-to-class="scale-95 opacity-0"
          >
            <div
              v-show="dropdownOpen"
              class="absolute right-0 z-20 w-48 py-2 mt-2 bg-white rounded-md shadow-xl"
            >
              <Link :href="route('profile-view')" method="get" as="button"

                class="block px-4 py-2 text-sm w-full text-gray-700 hover:bg-indigo-600 hover:text-white"
                >Your Profile</Link
              >
              <Link :href="route('dashboard')" method="get" as="button"
            
                class="block px-4 py-2 w-full text-sm text-gray-700 hover:bg-indigo-600 hover:text-white"
                >Your Dashboard</Link>

                <Link
              :href="route('Connect')" method="post" as="button"
                class="block px-4 py-2  w-full text-sm text-gray-700 hover:bg-indigo-600 hover:text-white"
                >Connect with Writers</Link
              >

              <Link
              :href="route('logout')" method="post" as="button"
                class="block px-4 py-2  w-full text-sm text-gray-700 hover:bg-indigo-600 hover:text-white"
                >Log out</Link
              >
            </div>
          </transition>
        </div>
      </div>
    </header>
  </template>
  
  <script setup>
  import { ref } from "vue";
  import { Link } from "@inertiajs/vue3";
  import {useSidebar} from '@/hooks/useSidebar'
  
  const dropdownOpen = ref(false);
  const { isOpen }=useSidebar();
  </script>