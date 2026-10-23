<script setup lang="ts">
import { TokenRarityColorEnum } from '@/tokens/types.ts'

const props = withDefaults(
    defineProps<{
        color: TokenRarityColorEnum
        size?: 'normal' | 'large'
    }>(),
    {
        type: 'common',
        size: 'normal',
    },
)
</script>

<template>
    <span class="star" :class="[props.size]" />
</template>

<style scoped lang="scss">
.star {
    &.normal {
        width: 16px;
        height: 16px;
    }

    &.large {
        width: 28px;
        height: 28px;
    }

    display: inline-block;
    width: 16px;
    height: 16px;
    aspect-ratio: 1;
    background: v-bind(color);
    clip-path: polygon(
        50% 0%,
        57.8% 25.9%,
        79.4% 9.5%,
        70.5% 35.1%,
        97.6% 34.5%,
        75.3% 50%,
        97.6% 65.5%,
        70.5% 64.9%,
        79.4% 90.5%,
        57.8% 74.1%,
        50% 100%,
        42.2% 74.1%,
        20.6% 90.5%,
        29.5% 64.9%,
        2.4% 65.5%,
        24.7% 50%,
        2.4% 34.5%,
        29.5% 35.1%,
        20.6% 9.5%,
        42.2% 25.9%
    );
}
</style>
