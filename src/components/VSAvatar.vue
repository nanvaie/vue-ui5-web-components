<template>
    <ui5-avatar v-bind="props">
        <slot></slot>
        <slot name="badge"></slot>
    </ui5-avatar>
</template>

<script setup>

import "@ui5/webcomponents/dist/Avatar.js";

const props = defineProps({
    accessibleName: String,
    colorScheme: {
        type: String,
        validator(value) {
            return [
                "Accent1",
                "Accent2",
                "Accent3",
                "Accent4",
                "Accent5",
                "Accent6",
                "Accent7",
                "Accent8",
                "Accent9",
                "Accent10",
                "Placeholder",
            ].includes(value);
        }
    },
    icon: String,
    initials: String,
    interactive: {
        type: Boolean,
        default: undefined
    },
    shape: {
        type: String,
        validator(value) {
            return [
                "Square",
                "Circle",
            ].includes(value);
        }
    },
    size: {
        type: String,
        validator(value) {
            return [
                "XS",
                "S",
                "M",
                "L",
                "XL",
            ].includes(value);
        }
    }
});

</script>
