<template>
    <div v-if="shortcutView" class="meal_shortcut">
        <div class="meal__title_shortcut">
            <component :is="mealIcon" class="meal__icon_shortcut"/>
            <span class="meal__name_shortcut">{{ mealName }}</span>
            <v-btn :size="addButtonSize" icon="mdi-plus" @click="mealCaloriesCount+=1"></v-btn>
        </div>
        
        <div v-if="mealCaloriesCount > 0" class="meal__calories_shortcut">
            <hr class="meal__divider_shortcut">
            {{ mealCaloriesCount }} Ккал
        </div>
    </div>
</template>

<script setup>
    import { ref, computed, onBeforeMount} from 'vue'
    import BreakfastIcon from '../icons/BreakfastIcon.vue';
    import LunchIcon from '../icons/LunchIcon.vue';
    import DinnerIcon from '../icons/DinnerIcon.vue';
    import SnackIcon from '../icons/SnackIcon.vue';

    onBeforeMount(() => {
        addButtonSize.value = window.matchMedia("(max-width: 415px)").matches ? `x-small` : `small`;
    });

    const mealCaloriesCount = ref(1);
    const shortcutView = ref(true);
    
    const addButtonSize = ref('');

    const mealIcon = computed(() => {
        switch (props.mealName) {
            case "Завтрак":
                return BreakfastIcon;
            case "Обед":
                return LunchIcon;
            case "Ужин":
                return DinnerIcon;
            case "Перекус":
                return SnackIcon;
        }
    })

    const props = defineProps({
        mealName: String,
    })
</script>

<style scoped lang="scss">
    @media (max-width: 426px) {
        .meal__icon_shortcut {
            width: 35px;
        }
    }

    @media (min-width: 427px) {
        .meal__icon_shortcut {
            width: 41px;
        }
    }

    .meal_shortcut {
        text-align: center;
        display: flex;
        flex-direction: column;
        border: 1px solid #eee;
        border-radius: 0.5em;
        padding: 0.5em 0 0.7em;
    }

    
    .meal__name_shortcut {
        font-size: 1em;
    }

    .meal__title_shortcut {
        display: flex;
        align-items: center;
        justify-content: space-around;
    }

    .meal__divider_shortcut {
        margin: 0.5em 0;
    }

</style>