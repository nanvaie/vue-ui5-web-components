<template>
    <ui5-button
        :accessibility-attributes="props.accessibilityAttributes"
        :accessible-name="props.accessibleName"
        :accessible-name-ref="props.accessibleNameRef"
        :design="props.design"
        :disabled="props.disabled"
        :icon="props.icon"
        :icon-end="props.iconEnd"
        :slot="props.slot"
        :submits="props.submits"
        :tooltip="props.tooltip"
    >
        <slot></slot>
    </ui5-button>
</template>

<script setup>

import "@ui5/webcomponents/dist/Button";
import { defineProps } from "vue";

const props = defineProps({
    accessibilityAttributes: Object,
    accessibleName: String,
    accessibleNameRef: String,
    design: {
        type: String,
        validator(value) {
            return [
                "Default",
                "Emphasized",
                "Positive",
                "Negative",
                "Transparent",
                "Attention",
            ].includes(value);
        }
    },
    disabled: {
        type: Boolean,
        default: undefined
    },
    icon: String,
    iconEnd: {
        type: Boolean,
        default: undefined
    },
    slot: String,
    submits: {
        type: Boolean,
        default: undefined
    },
    tooltip: String
});

</script>
