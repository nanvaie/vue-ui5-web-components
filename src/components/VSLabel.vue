<template>
    <ui5-label
        :for="props.for"
        :required="props.required === true ? true : null"
        :show-colon="props.showColon === true ? true : null"
        :wrapping-type="props.wrappingType === true ? true : null"
    >
        <slot></slot>
    </ui5-label>
</template>

<script setup>

import "@ui5/webcomponents/dist/Label";

const props = defineProps({
    for: String,
    required: Boolean,
    showColon: Boolean,
    wrappingType: Boolean
})

</script>
