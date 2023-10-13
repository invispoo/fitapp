<template>
  <Nutrients class="nutrients-card"/>
  <div class="meal-group">
    <Meal mealName="Завтрак" class="meal-card"/>
    <Meal mealName="Обед" class="meal-card"/>
    <Meal mealName="Ужин" class="meal-card"/>
    <Meal mealName="Перекус" class="meal-card"/>
  </div>
  

</template>

<script setup>
  import Meal from './components/Meal.vue'
  import Nutrients from './components/Nutrients.vue'
</script>

<style scoped lang="scss">
   @media (min-width: 427px) { 
    .meal-card {
      width: 25%;
      margin: 0.5em;
    }
   }

   @media (max-width: 426px) { 
    .meal-card {
      width: 50%;
      margin: 0.5em;
    }
   }

   @media (max-width: 300px) { 
    .meal-card {
      width: 70%;
      margin: 0.5em;
    }
   }

   @media (min-aspect-ratio: 7/10) and (max-aspect-ratio: 9/10) and (min-width: 427px) {
    .meal-card {
      width: 30%;
      margin: 0.5em;
    }
   }

   .meal-group {
    display: flex;
    place-items: center;
    flex-direction: column;
   }

   .nutrients-card {
    text-align: center;
    width: 25%;
    margin: 0.5em auto 0;
   }
  
</style>
