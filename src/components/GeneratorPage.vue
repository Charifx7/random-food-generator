<template>
    <section class="hero min-h-screen bg-gray flex flex-col items-center justify-center text-center">
        <h1 class="text-5xl md:text-7xl font-bold text-blue- mb-4">
            Welcome to the Food Randomizer!
        </h1>
        <p class="text-lg md:text-2xl mb-8">
            Discover your next meal with a simple click
        </p>
        <div class="text-4xl md:text-5xl font-semibold text-white  mb-6">
            {{ currentFood.name }}
        </div>
        <button class="btn btn-neutral btn-lg" @click="getRandomFood">Get Random Food</button>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const foods = ref([
    { name: 'ข้าวผัด' },
    { name: 'ไก่ทอด' },
    { name: 'ผัดไทย' },
    { name: 'ข้าวหมกไก่ทอด' },
    { name: 'ชาบู' },
    { name: 'ขนมจีน' },
    { name: 'เบอร์เกอร์' },
    { name: 'ไข่พะโล้' },
    { name: 'ไก่ย่าง' },
    { name: 'ข้าวเนื้อทอดกระเทียม' },
    { name: 'มาม่า' },
    { name: 'ราเมง' },
    { name: 'ผัดขี้เมา' },
    { name: 'ข้าวไข่เจียว' },
])

const currentFood = ref({ name: '' })
let previousIndex = -1

const getRandomFood = () => {
    let randomIndex
    do {
        randomIndex = Math.floor(Math.random() * foods.value.length)
    } while (randomIndex === previousIndex)
    previousIndex = randomIndex
    currentFood.value = foods.value[randomIndex]
}

onMounted(getRandomFood)
</script>