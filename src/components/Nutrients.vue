<template>
    <div class="nutrients">
        <v-progress-circular
        :rotate="360"
        :size="100"
        :width="15"
        :model-value="calories"
        :color="caloriesColor"
        >
            {{ calories }} Ккал
        </v-progress-circular>
        <div class="nutrients__macro">
            <span>Углеводы</span>
            <v-progress-linear
            :model-value="carbs"
            bg-color="pink-lighten-3"
            color="pink-lighten-1"
            />
            <br>
            <span>Белки</span>
            <v-progress-linear
            :model-value="proteins"
            bg-color="blue-grey"
            color="lime"
            />
            <br>
            <span>Жиры</span>
            <v-progress-linear
            :model-value="fats"
            bg-color="success"
            color="error"
            />
        </div>
    </div>
</template>

<script setup>
    import {ref, computed} from 'vue'

    const calories = ref(0);
    const carbs = ref(0);
    const proteins = ref(0);
    const fats = ref(0);
    const caloriesColor = computed(() => {
        return calories.value > 10 ? `red` : `teal`;
    })
</script>

<style scoped lang="scss">
    .nutrients__macro {
        padding: 1.5em 1.7em 2em;
        border: 1px solid #eee;
        border-radius: 0.5em;
        margin: 1em 0 0.5em;
        text-align: left;
    }

</style>