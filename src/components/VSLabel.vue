<template>
    <ui5-label v-bind="props">
        <slot></slot>
    </ui5-label>
</template>

<script setup>

import "@ui5/webcomponents/dist/Label";
import {defineProps} from "vue";

const props = defineProps({
    for: String,
    required: {
        type: Boolean,
        default: undefined
    },
    showColon: {
        type: Boolean,
        default: undefined
    },
    wrappingType: {
        type: Boolean,
        default: undefined
    }
});

</script>
