<script lang="ts" setup>
import { useI18n } from 'vue-i18n'
import { computed } from 'vue'
import Star from '@/components/icons/Star.vue'
import { TokenRarityColorEnum } from '@/tokens/types.ts'

const props = defineProps<{
    tag: string
    value: string
}>()

const { t } = useI18n()
const text = computed(() => t(`rarity_${props.value}`))
const iconColor = computed(() => {
    switch (props.value) {
        case 'common':
            return TokenRarityColorEnum.common
        case 'uncommon':
            return TokenRarityColorEnum.uncommon
        case 'rare':
            return TokenRarityColorEnum.rare
        case 'exclusive':
            return TokenRarityColorEnum.exclusive
        default:
            return ''
    }
})
</script>

<template>
    <component :is="tag" class="icon-description">
        <span :class="value" class="rarity material-symbols-rounded"
            ><Star
                v-if="iconColor"
                :class="value"
                :color="iconColor"
                size="large"
        /></span>
        <span v-html="text"></span>
    </component>
</template>

<style lang="scss" scoped>
.icon-description .rarity {
    text-align: center;
    font-weight: bold;
    font-size: 150%;

    &.common {
        color: #05e004;
    }

    &.uncommon {
        color: #f2e000;
    }

    &.rare {
        color: #43caff;
    }

    &.exclusive {
        color: var(--white-icon);
    }
}
</style>
