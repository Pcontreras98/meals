<template>
    <div class="p-8">
        <input 
            type="text" 
            v-model="keyword"
            class="rounder border-2 border-gray-200 w-full" 
            placeholder="Search for Meals"
            @change="searchMeals"
        />  
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
        <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
            <img :src="meal.strMealThumb" :alt="strMeal" class="rounded-t-xl w-full h-48 object-cover">
            <h3 class="p-3 font-semibold">{{ meal.strMeal }}</h3>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ducimus, expedita dolorem qui nisi saepe est sunt laboriosam, voluptate iste atque iusto nobis ratione? Soluta quas, saepe asperiores natus architecto excepturi?</p>
            <div class="p-3">
                <a :href="meal.strYoutube" target="_blank">Youtube</a>
                <router-link to="/">
                    View
                </router-link>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { ref } from 'vue';
import store from '../store';

const keyword = ref('');
const meals = computed( () => store.state.searchedMeals);

function searchMeals() {
    store.dispatch('searchMeals', keyword.value)
}

</script> 

