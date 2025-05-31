<script setup>
import { PackageCheck, Store, ShoppingCart, Wallet } from 'lucide-vue-next';
</script>

<template>
<div class="mt-30 w-full">
    <div class="text-center flex flex-col justify-center items-center gap-5">
        <div class="border border-indigo-100 px-2 rounded-full bg-gradient-to-r from-indigo-100/50 to-indigo-200/50">
            <p class="text-indigo-700">Why Choose Us</p>
        </div>
        <h2 class="text-3xl text-indigo-800">What Sets Us Apart ?</h2>
    </div>
    <div class="flex flex-col items-center mt-10">
        <!-- Orders fullfiled -->
        <div class="flex flex-row gap-10 border border-indigo-300 rounded-md min-w-[300px] p-5 mb-5 shadow">
            <div>
                <PackageCheck class="h-12 w-12 text-indigo-900" />
            </div>
            <div>
                <p class="text-2xl font-bold text-indigo-700">13,000+</p>
                <p class="text-sm text-indigo-900">Orders fullfiled</p>
            </div>
        </div>
        <div class="flex flex-row gap-10 border border-indigo-300 rounded-md min-w-[300px] p-5 mb-5 shadow">
            <div>
                <Store class="h-12 w-12 text-indigo-900" />
            </div>
            <div>
                <p class="text-2xl font-bold text-indigo-700">53,000+</p>
                <p class="text-sm text-indigo-900">Satisfied Shoppers</p>
            </div>
        </div>
        <div class="flex flex-row gap-10 border border-indigo-300 rounded-md min-w-[300px] p-5 mb-5 shadow">
            <div>
                <ShoppingCart class="h-12 w-12 text-indigo-900" />
            </div>
            <div>
                <p class="text-2xl font-bold text-indigo-700">200+</p>
                <p class="text-sm text-indigo-900">Active Shops</p>
            </div>
        </div>
        <div class="flex flex-row gap-10 border border-indigo-300 rounded-md min-w-[300px] p-5 mb-5 shadow">
            <div>
                <Wallet class="h-12 w-12 text-indigo-900" />
            </div>
            <div>
                <p class="text-2xl font-bold text-indigo-700">1,956,000+</p>
                <p class="text-sm text-indigo-900">Completed Transactions</p>
            </div>
        </div>
    </div>
</div>
</template>

<style></style>