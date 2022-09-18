<template>
    <ui5-bar :design="props.design">
        <div v-if="$slots.startContent" slot="startContent">
            <slot name="startContent"></slot>
        </div>

        <slot></slot>

        <div v-if="$slots.endContent" slot="endContent">
            <slot name="endContent"></slot>
        </div>
    </ui5-bar>
</template>

<script setup>

import "@ui5/webcomponents-fiori/dist/Bar";
import { defineProps } from "vue";

const props = defineProps({
    design: {
        type: String,
        validator(value) {
            return [
                "Header",
                "Subheader",
                "Footer",
                "FloatingFooter",
            ].includes(value);
        }
    }
});

</script>
