<template>
<div class=" absolute w-full h-full bg-white">
    <div class="relative w-full m-0">

        <!-- navbar -->
        <div class=" relative w-full h-auto">
            <div id="bg_Navbar" class=" rounded-full h-16 text-black flex flex-row bg-daskom-abu-muda m-10 font-bebas text-lg">
                <div id="logo_dsk" class=" w-1/2 h-full flex">
                    <inertia-link href="/" class="w-auto h-12 my-auto flex flex-row hover:no-underline hover:text-black">
                        <div class=" w-auto h-12 my-auto ml-2 flex flex-row bg-white rounded-full">
                            <img src="/images/daskom.svg" class=" w-16" alt="LOGO">
                            <div class=" my-auto w-24">
                                DASKOM BLOG
                            </div>
                        </div>
                    </inertia-link>
                </div>
                <div id="menu_dsb" class=" w-1/2 flex flex-row text-daskom-abu-tua">
                    <div class="flex-1"></div>
                    <!-- <div class=" w-auto h-auto my-auto mr-10 hover:text-black">
                        ARTICLES
                    </div> -->
                    <div class=" w-auto h-auto my-auto mr-10 hover:text-black">
                        <inertia-link href="/about" class="hover:no-underline hover:text-black">ABOUT</inertia-link>
                    </div>
                    <!-- <div class=" w-auto h-auto my-auto mr-10 hover:text-black">
                        CONTACTS
                    </div> -->
                    <div class=" w-auto h-auto my-auto mr-10">
                        <inertia-link href="/login" class="hover:no-underline hover:text-black" :class="[{ 'hidden': this.currentUser!=null },
                                    { 'visible': this.currentUser==null }]">LOGIN</inertia-link>
                        <inertia-link href="/logout/home/null" class="hover:no-underline hover:text-black" :class="[{ 'hidden': this.currentUser==null },
                                    { 'visible' : this.currentUser!=null}]">
                            <div class=" flex flex-row">
                                <img class=" w-10 h-10 my-auto mr-2 rounded-full" :src="currentUser == null ? '':'/images/'+currentUser.code+'.jpg'" alt="foto asisten">
                                <span class="my-auto">
                                    {{currentUser == null ? '':currentUser.code}} | LOGOUT
                                </span>
                            </div>
                        </inertia-link>
                    </div>
                </div>
            </div>
        </div>

        <!-- main page -->
        <div class=" relative w-full h-auto flex flex-row">
            <div class="flex-1 pl-16 pr-4">
                <div class=" relative flex">
                    <div class="w-full max-w-xs mx-auto">
                        
                        <!-- user: TST
                        pass: test123 -->

                        <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" @keyup.enter="login">
                            <div class="mb-4">
                                <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
                                    Kode Asisten
                                </label>
                                <input v-model="formLogin.code" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="TST">
                            </div>
                            <div class="mb-6">
                                <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
                                    Password
                                </label>
                                <input v-model="formLogin.password" class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="******************">
                                <p class="text-red-500 text-xs italic" v-if="error != ''">{{ error }}</p>
                            </div>
                            <div class="flex items-center justify-between">
                                <button v-on:click="login" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
                                    Sign In
                                </button>
                                <!-- <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="#">
                                    Forgot Password?
                                </a> -->
                            </div>
                        </form>
                        <p class="text-center text-gray-500 text-xs">
                            &copy;2020 Daskom Lab. All rights reserved.
                        </p>
                    </div>
                </div>
            </div>
            <div class="flex flex-col">
                <!-- search bar -->
                <div class="mx-auto h-auto">
                    <div class=" mr-24 mt-6 w-auto h-auto">
                        <div class="border rounded-full p-2">
                            <input class=" py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:placeholder-transparent" id="username" type="text" placeholder="Search">
                            <button class=" text-white font-bold p-2 rounded-full focus:outline-none">
                                <img src="/images/cari.png" class=" w-4 h-4" alt="Cari">
                            </button>
                        </div>
                    </div>
                </div>

                <!-- socmed bar -->
                <div class=" mx-auto mt-6">
                    <div class=" mr-24 flex flex-row text-daskom-abu-tua w-64">
                        <div class="w-1/4">
                            <a href=""><svg class=" fill-current w-full h-8 mx-auto hover:text-daskom-hijau" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 26 26" width="26px" height="26px">
                                    <path d="M 7.546875 0 C 3.390625 0 0 3.390625 0 7.546875 L 0 18.453125 C 0 22.609375 3.390625 26 7.546875 26 L 18.453125 26 C 22.609375 26 26 22.609375 26 18.453125 L 26 7.546875 C 26 3.390625 22.609375 0 18.453125 0 Z M 7.546875 2 L 18.453125 2 C 21.527344 2 24 4.46875 24 7.546875 L 24 18.453125 C 24 21.527344 21.53125 24 18.453125 24 L 7.546875 24 C 4.472656 24 2 21.53125 2 18.453125 L 2 7.546875 C 2 4.472656 4.46875 2 7.546875 2 Z M 20.5 4 C 19.671875 4 19 4.671875 19 5.5 C 19 6.328125 19.671875 7 20.5 7 C 21.328125 7 22 6.328125 22 5.5 C 22 4.671875 21.328125 4 20.5 4 Z M 13 6 C 9.144531 6 6 9.144531 6 13 C 6 16.855469 9.144531 20 13 20 C 16.855469 20 20 16.855469 20 13 C 20 9.144531 16.855469 6 13 6 Z M 13 8 C 15.773438 8 18 10.226563 18 13 C 18 15.773438 15.773438 18 13 18 C 10.226563 18 8 15.773438 8 13 C 8 10.226563 10.226563 8 13 8 Z" /></svg></a>
                        </div>
                        <div class="w-1/4">
                            <a href=""><svg class=" fill-current w-full h-8 mx-auto hover:text-daskom-hijau" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50" width="50px" height="50px">
                                    <path d="M 9 4 C 6.2504839 4 4 6.2504839 4 9 L 4 41 C 4 43.749516 6.2504839 46 9 46 L 41 46 C 43.749516 46 46 43.749516 46 41 L 46 9 C 46 6.2504839 43.749516 4 41 4 L 9 4 z M 9 6 L 41 6 C 42.668484 6 44 7.3315161 44 9 L 44 41 C 44 42.668484 42.668484 44 41 44 L 9 44 C 7.3315161 44 6 42.668484 6 41 L 6 9 C 6 7.3315161 7.3315161 6 9 6 z M 25 10 C 16.297049 10 9 15.678331 9 22.947266 C 9 29.432462 14.784063 34.70004 22.335938 35.712891 C 22.335938 35.712891 22.337891 35.712891 22.337891 35.712891 C 22.536678 35.755374 22.765454 35.823119 22.900391 35.886719 C 22.927968 35.899717 22.92499 35.900858 22.939453 35.910156 C 22.936808 35.992303 22.962381 36.370293 22.923828 36.660156 C 22.914328 36.716266 22.750575 37.685545 22.716797 37.876953 L 22.716797 37.878906 C 22.670157 38.145846 22.493944 38.683413 22.949219 39.369141 C 23.176856 39.712004 23.648332 39.989421 24.089844 40.027344 C 24.531355 40.065264 24.936512 39.956154 25.388672 39.765625 C 26.423745 39.336822 28.490518 38.115392 30.876953 36.482422 C 33.261295 34.850883 35.83616 32.871381 37.521484 30.970703 C 39.813508 28.503964 41 25.843504 41 22.947266 C 41 15.679227 33.703032 10 25 10 z M 25 12 C 32.838968 12 39 17.041304 39 22.947266 C 39 25.319988 38.105988 27.408105 36.052734 29.615234 L 36.042969 29.625 L 36.035156 29.634766 C 34.573278 31.286637 32.063988 33.245345 29.748047 34.830078 C 27.492074 36.373777 25.386061 37.559635 24.75 37.839844 C 24.81529 37.455902 24.900391 36.957031 24.900391 36.957031 L 24.904297 36.939453 L 24.90625 36.921875 C 24.96188 36.503517 25.111583 35.868916 24.792969 35.083984 L 24.792969 35.082031 L 24.792969 35.080078 C 24.555561 34.50218 24.11359 34.248575 23.751953 34.078125 C 23.390316 33.907675 23.042681 33.819356 22.753906 33.757812 L 22.714844 33.748047 L 22.673828 33.744141 C 15.849442 32.857984 11 28.250827 11 22.947266 C 11 17.040201 17.160951 12 25 12 z M 23.992188 18.998047 C 23.488379 19.007393 23 19.391875 23 20 L 23 26 C 23 26.552 23.448 27 24 27 C 24.552 27 25 26.552 25 26 L 25 23.121094 L 27.185547 26.580078 C 27.751547 27.372078 29 26.973 29 26 L 29 20 C 29 19.448 28.552 19 28 19 C 27.448 19 27 19.448 27 20 L 27 23 L 24.814453 19.419922 C 24.602203 19.122922 24.294473 18.992439 23.992188 18.998047 z M 15 19 C 14.448 19 14 19.448 14 20 L 14 26 C 14 26.552 14.448 27 15 27 L 18 27 C 18.552 27 19 26.552 19 26 C 19 25.448 18.552 25 18 25 L 16 25 L 16 20 C 16 19.448 15.552 19 15 19 z M 21 19 C 20.448 19 20 19.448 20 20 L 20 26 C 20 26.552 20.448 27 21 27 C 21.552 27 22 26.552 22 26 L 22 20 C 22 19.448 21.552 19 21 19 z M 31 19 C 30.448 19 30 19.448 30 20 L 30 26 C 30 26.552 30.448 27 31 27 L 34 27 C 34.552 27 35 26.552 35 26 C 35 25.448 34.552 25 34 25 L 32 25 L 32 24 L 34 24 C 34.553 24 35 23.552 35 23 C 35 22.448 34.553 22 34 22 L 32 22 L 32 21 L 34 21 C 34.552 21 35 20.552 35 20 C 35 19.448 34.552 19 34 19 L 31 19 z" /></svg></a>
                        </div>
                        <div class="w-1/4">
                            <a href=""><svg class=" fill-current w-full h-8 mx-auto hover:text-daskom-hijau" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 26 26" width="26px" height="26px">
                                    <path d="M 6.3125 0.03125 L 8.09375 5.875 L 8.09375 9.6875 L 9.59375 9.6875 L 9.59375 5.6875 L 11.3125 0.03125 L 9.8125 0.03125 L 8.875 3.875 L 8.78125 3.875 L 7.8125 0.03125 Z M 13.21875 2.375 C 12.617188 2.375 12.136719 2.546875 11.78125 2.875 C 11.425781 3.199219 11.25 3.636719 11.25 4.1875 L 11.25 7.875 C 11.25 8.480469 11.433594 8.988281 11.78125 9.34375 C 12.132813 9.703125 12.574219 9.875 13.15625 9.875 C 13.757813 9.875 14.25 9.691406 14.59375 9.34375 C 14.9375 8.996094 15.09375 8.515625 15.09375 7.90625 L 15.09375 4.21875 C 15.09375 3.675781 14.914063 3.25 14.5625 2.90625 C 14.214844 2.558594 13.769531 2.375 13.21875 2.375 Z M 16.21875 2.5625 L 16.21875 8.53125 C 16.21875 8.957031 16.3125 9.257813 16.46875 9.46875 C 16.625 9.679688 16.851563 9.78125 17.15625 9.78125 C 17.402344 9.78125 17.644531 9.710938 17.90625 9.5625 C 18.171875 9.410156 18.445313 9.195313 18.6875 8.90625 L 18.6875 9.6875 L 20 9.6875 L 20 2.5625 L 18.6875 2.5625 L 18.6875 7.96875 C 18.5625 8.121094 18.429688 8.246094 18.28125 8.34375 C 18.132813 8.445313 18.003906 8.5 17.90625 8.5 C 17.785156 8.5 17.679688 8.480469 17.625 8.40625 C 17.566406 8.332031 17.5625 8.195313 17.5625 8.03125 L 17.5625 2.5625 Z M 13.15625 3.625 C 13.332031 3.625 13.488281 3.65625 13.59375 3.75 C 13.703125 3.847656 13.75 3.972656 13.75 4.125 L 13.75 8.03125 C 13.75 8.222656 13.699219 8.363281 13.59375 8.46875 C 13.488281 8.578125 13.335938 8.625 13.15625 8.625 C 12.980469 8.625 12.84375 8.574219 12.75 8.46875 C 12.652344 8.363281 12.625 8.226563 12.625 8.03125 L 12.625 4.125 C 12.625 3.972656 12.679688 3.847656 12.78125 3.75 C 12.882813 3.65625 12.996094 3.625 13.15625 3.625 Z M 13 11.15625 C 10.40625 11.152344 7.863281 11.175781 5.375 11.28125 C 3.636719 11.28125 2.21875 12.683594 2.21875 14.40625 C 2.113281 15.769531 2.058594 17.136719 2.0625 18.5 C 2.058594 19.863281 2.113281 21.230469 2.21875 22.59375 C 2.21875 24.316406 3.636719 25.71875 5.375 25.71875 C 7.863281 25.820313 10.40625 25.847656 13 25.84375 C 15.597656 25.851563 18.140625 25.820313 20.625 25.71875 C 22.363281 25.71875 23.78125 24.316406 23.78125 22.59375 C 23.886719 21.230469 23.941406 19.863281 23.9375 18.5 C 23.945313 17.136719 23.886719 15.769531 23.78125 14.40625 C 23.78125 12.683594 22.363281 11.28125 20.625 11.28125 C 18.140625 11.175781 15.597656 11.152344 13 11.15625 Z M 3.75 13.375 L 8.34375 13.375 C 8.425781 13.375 8.5 13.449219 8.5 13.53125 L 8.5 14.9375 C 8.5 15.019531 8.425781 15.09375 8.34375 15.09375 L 6.9375 15.09375 L 6.9375 23.1875 C 6.9375 23.269531 6.894531 23.34375 6.8125 23.34375 L 5.3125 23.34375 C 5.230469 23.34375 5.15625 23.269531 5.15625 23.1875 L 5.15625 15.09375 L 3.75 15.09375 C 3.667969 15.09375 3.625 15.019531 3.625 14.9375 L 3.625 13.53125 C 3.625 13.449219 3.667969 13.375 3.75 13.375 Z M 13.40625 13.375 L 14.75 13.375 C 14.832031 13.375 14.90625 13.449219 14.90625 13.53125 L 14.90625 16.25 C 15.015625 16.148438 15.132813 16.066406 15.25 16 C 15.476563 15.875 15.707031 15.8125 15.9375 15.8125 C 16.40625 15.8125 16.75 16 17 16.34375 C 17.238281 16.675781 17.375 17.140625 17.375 17.75 L 17.375 21.71875 C 17.375 22.257813 17.261719 22.675781 17.03125 22.96875 C 16.792969 23.273438 16.4375 23.4375 16 23.4375 C 15.722656 23.4375 15.476563 23.363281 15.25 23.25 C 15.128906 23.1875 15.015625 23.128906 14.90625 23.03125 L 14.90625 23.1875 C 14.90625 23.269531 14.832031 23.34375 14.75 23.34375 L 13.40625 23.34375 C 13.324219 23.34375 13.25 23.269531 13.25 23.1875 L 13.25 13.53125 C 13.25 13.449219 13.324219 13.375 13.40625 13.375 Z M 20.21875 15.71875 C 20.867188 15.71875 21.398438 15.921875 21.75 16.3125 C 22.101563 16.703125 22.28125 17.257813 22.28125 17.96875 L 22.28125 19.8125 C 22.28125 19.894531 22.207031 19.9375 22.125 19.9375 L 19.75 19.9375 L 19.75 21.15625 C 19.75 21.59375 19.796875 21.765625 19.84375 21.84375 C 19.882813 21.90625 19.949219 22 20.15625 22 C 20.324219 22 20.441406 21.953125 20.5 21.875 C 20.527344 21.832031 20.59375 21.675781 20.59375 21.15625 L 20.59375 20.65625 C 20.59375 20.574219 20.667969 20.5 20.75 20.5 L 22.125 20.5 C 22.207031 20.5 22.28125 20.574219 22.28125 20.65625 L 22.28125 21.1875 C 22.28125 21.957031 22.074219 22.542969 21.71875 22.9375 C 21.363281 23.335938 20.828125 23.53125 20.125 23.53125 C 19.488281 23.53125 18.992188 23.332031 18.625 22.90625 C 18.261719 22.488281 18.0625 21.910156 18.0625 21.1875 L 18.0625 17.96875 C 18.0625 17.3125 18.253906 16.792969 18.65625 16.375 C 19.058594 15.957031 19.585938 15.71875 20.21875 15.71875 Z M 8.34375 15.90625 L 9.65625 15.90625 C 9.738281 15.90625 9.8125 15.980469 9.8125 16.0625 L 9.8125 21.53125 C 9.8125 21.710938 9.824219 21.785156 9.84375 21.8125 C 9.851563 21.824219 9.886719 21.875 10 21.875 C 10.039063 21.875 10.125 21.859375 10.28125 21.75 C 10.410156 21.664063 10.523438 21.558594 10.625 21.4375 L 10.625 16.0625 C 10.625 15.980469 10.699219 15.90625 10.78125 15.90625 L 12.125 15.90625 C 12.207031 15.90625 12.25 15.980469 12.25 16.0625 L 12.25 23.1875 C 12.25 23.269531 12.207031 23.34375 12.125 23.34375 L 10.78125 23.34375 C 10.699219 23.34375 10.625 23.269531 10.625 23.1875 L 10.625 22.78125 C 10.449219 22.953125 10.277344 23.082031 10.09375 23.1875 C 9.804688 23.351563 9.53125 23.4375 9.25 23.4375 C 8.894531 23.4375 8.621094 23.316406 8.4375 23.0625 C 8.261719 22.824219 8.1875 22.484375 8.1875 22.03125 L 8.1875 16.0625 C 8.1875 15.980469 8.261719 15.90625 8.34375 15.90625 Z M 15.25 17.25 C 15.199219 17.257813 15.148438 17.285156 15.09375 17.3125 C 15.03125 17.34375 14.96875 17.402344 14.90625 17.46875 L 14.90625 21.78125 C 14.984375 21.863281 15.050781 21.933594 15.125 21.96875 C 15.207031 22.007813 15.285156 22.03125 15.375 22.03125 C 15.542969 22.03125 15.609375 21.960938 15.625 21.9375 C 15.664063 21.886719 15.6875 21.769531 15.6875 21.53125 L 15.6875 17.84375 C 15.6875 17.640625 15.667969 17.472656 15.59375 17.375 C 15.519531 17.277344 15.402344 17.222656 15.25 17.25 Z M 20.1875 17.28125 C 20.027344 17.28125 19.910156 17.316406 19.84375 17.40625 C 19.796875 17.472656 19.75 17.636719 19.75 17.96875 L 19.75 18.53125 L 20.59375 18.53125 L 20.59375 17.96875 C 20.59375 17.640625 20.550781 17.480469 20.5 17.40625 C 20.4375 17.320313 20.339844 17.28125 20.1875 17.28125 Z" /></svg></a>
                        </div>
                        <div class="w-1/4">
                            <a href=""><svg class=" fill-current w-full h-8 mx-auto hover:text-daskom-hijau" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 26 26" width="26px" height="26px">
                                    <path d="M 21.125 0 L 4.875 0 C 2.183594 0 0 2.183594 0 4.875 L 0 21.125 C 0 23.816406 2.183594 26 4.875 26 L 21.125 26 C 23.816406 26 26 23.816406 26 21.125 L 26 4.875 C 26 2.183594 23.816406 0 21.125 0 Z M 20.464844 14.003906 L 18.03125 14.003906 L 18.03125 23.007813 L 13.96875 23.007813 L 13.96875 14.003906 L 12.390625 14.003906 L 12.390625 10.96875 L 13.96875 10.96875 L 13.96875 9.035156 C 13.96875 6.503906 15.019531 5 18.007813 5 L 21.03125 5 L 21.03125 8.023438 L 19.273438 8.023438 C 18.113281 8.023438 18.035156 8.453125 18.035156 9.265625 L 18.03125 10.96875 L 20.796875 10.96875 Z" /></svg></a>
                        </div>
                    </div>
                </div>

                <!-- most viewed articles -->
                <div class=" mt-12">
                    <span class="font-bebas text-xl">
                        Most Viewed Articles
                    </span>
                    <transition-group name="most-viewed-articles" tag="div" class=" mt-2">
                        <div v-for="(mv) in mostviewed" v-bind:key="mv.id" class="animation-enable w-full h-120 mt-2">
                            <div class=" font-quicksand ml-3 hover:text-daskom-hijau hover:underline">
                                - {{ mv.title }}
                            </div>
                        </div>
                    </transition-group>
                    <div class="mt-2 ml-3 font-bebas underline text-daskom-hijau">
                        See more...
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- lower navbar -->
    <div class=" relative bg-black w-full h-40 mt-24 flex flex-col w-full">
        <div class=" -mt-8 mx-auto w-auto flex flex-col">
            <a href="#"><img src="/images/panah.png" class=" h-16" alt=""></a>
            <span class=" mx-auto w-auto text-white font-quicksand font-bold">Scroll Up</span>
        </div>
        <!-- <div class=" text-white font-bebas flex flex-row text-xl mt-12 w-auto mx-auto h-auto">
            <div class=" w-auto">
                ARTICLES
            </div>
            <div class=" mx-4">
                |
            </div>
            <div class=" w-auto">
                ABOUT
            </div>
            <div class=" mx-4">
                |
            </div>
            <div class=" w-auto">
                CONTACTS
            </div>
        </div> -->
        <div class="text-white font-quicksand mx-auto w-auto mt-6 mb-6">
            Daskom Laboratory ©2020 All Rights Reserved.
        </div>
    </div>
</div>
</template>

<script>
export default {
props: ['currentUser'],
    data() {
        return {
            formLogin: {
                code: '',
                password: '',
            },
            error: '',
        };
    },

    methods: {

        /**
         * TODO: 
         * 
         * Add Error handling system (UI)
         */
        login: function () {
            const globe = this;
            this.$axios.post('/login', this.formLogin).then(response => {
                if (response.data.message === "Login Failed") {
                    globe.error = "Code or password is wrong";
                } else {
                    globe.$inertia.replace('/');
                }
            }).catch(function (error) {
                if (error.response) {
                    // The request was made and the server responded with a status code
                    // that falls out of the range of 2xx
                    if (error.response.data.errors != null) {
                        if (error.response.data.errors.code != null)
                            globe.error = error.response.data.errors.code[0];
                        if (error.response.data.errors.password != null)
                            globe.error = error.response.data.errors.password[0];
                    }
                }
            });
        },
    },
}
</script>