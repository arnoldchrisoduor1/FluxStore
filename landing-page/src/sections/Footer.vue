<script setup>
import { ChevronRight } from 'lucide-vue-next';
</script>

<template>
    <div class="bg-gradient-to-b from-indigo-800 to-violet-900 pt-10">
        <div class="flex flex-col gap-5 px-5 md:px-10 md:py-10">
            <div class="w-fit text-center flex flex-col gap-5">
                <h1 class="text-indigo-200 font-bold text-4xl text-center">FluxStore</h1>
                <p class="text-indigo-200 text-lg font-semibold">Revolutionizing commerce through AI and Blockchain
                    Technology</p>
            </div>
            <div class="flex flex-col gap-10 md:flex-row md:gap-20 mt-10">
                <div>
                    <h2 class="font-bold text-indigo-100 text-lg">About</h2>
                    <ul class="">
                        <div class="flex items-center">
                            <ChevronRight class="text-indigo-200 h-4 w-4" />
                            <li class="font-semibold text-indigo-300">Our Product</li>
                        </div>
                        <div class="flex items-center">
                            <ChevronRight class="text-indigo-200 h-4 w-4" />
                            <li class="font-semibold text-indigo-300">Features</li>
                        </div>
                        <div class="flex items-center">
                            <ChevronRight class="text-indigo-200 h-4 w-4" />
                            <li class="font-semibold text-indigo-300">Getting Started</li>
                        </div>
                    </ul>
                </div>
                <div>
                    <h2 class="font-bold text-indigo-100 text-lg">Payments</h2>
                    <ul>
                        <div class="flex items-center">
                            <ChevronRight class="text-indigo-200 h-4 w-4" />
                            <li class="font-semibold text-indigo-300">Pricing</li>
                        </div>
                        <div class="flex items-center">
                            <ChevronRight class="text-indigo-200 h-4 w-4" />
                            <li class="font-semibold text-indigo-300">Blockchain</li>
                        </div>
                        <div class="flex items-center">
                            <ChevronRight class="text-indigo-200 h-4 w-4" />
                            <li class="font-semibold text-indigo-300">Secure Transactions</li>
                        </div>

                    </ul>
                </div>
                <div>
                    <h2 class="font-bold text-indigo-100 text-lg">News Letter</h2>
                    <div class="flex flex-col gap-5 mt-5">
                        <input
                            class="bg-violet-600/20 py-2 px-2 rounded-lg border outline-none border-indigo-300 placeholder:text-indigo-200"
                            placeholder="Email Address" />
                        <div class="text-indigo-800 font-semibold bg-white/80 w-fit px-10 py-2 rounded-lg">Subscribe
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="mt-5 pb-5">
            <!-- <p class="text-indigo-900">Created by Arnold Oduor</p>  -->
            <p class="font-semibold text-indigo-300 py-2 text-center">&copy; 2025 Arnold Oduor</p>
        </div>
    </div>
</template>

<style></style>