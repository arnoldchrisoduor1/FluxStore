<script setup>
import { PackageCheck, Store, ShoppingCart, Wallet } from 'lucide-vue-next';
import StatBox from '../components/StatBox.vue';
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
        <StatBox title="Orders fullfilled" value="1200+" :icon="PackageCheck"  />
        <StatBox title="Active Shops" value="220+" :icon="Store"  />
        <StatBox title="Active Buyers" value="171000+" :icon="ShoppingCart"  />
        <StatBox title="Orders fullfilled" value="320400+" :icon="Wallet"  />
    </div>
</div>
</template>

<style>
</style>