<template>
    <VSButton
        @click="handleMenu"
        :accessibility-attributes="props.options?.buttonOptions?.props.accessibilityAttributes"
        :accessible-name="props.options?.buttonOptions?.props.accessibleName"
        :accessible-name-ref="props.options?.buttonOptions?.props.accessibleNameRef"
        :design="props.options?.buttonOptions?.props.design"
        :disabled="props.options?.buttonOptions?.props.disabled"
        :icon="props.options?.buttonOptions?.props.icon"
        :icon-end="props.options?.buttonOptions?.props.iconEnd"
        :submits="props.options?.buttonOptions?.props.submits"
        :tooltip="props.options?.buttonOptions?.props.tooltip"
    >
        {{ props.options?.buttonOptions?.text }}
    </VSButton>

    <VSMenu/>
</template>

<script setup>

import { createVNode, defineComponent, getCurrentInstance } from 'vue';
import { defineProps } from "vue";
import VSButton from "./VSButton.vue";

const props = defineProps({
    options: Object
})

const componentUid = 'vs-' + getCurrentInstance().uid.toString();
const items = prepareItems(props.options.items);
let isMenuVisible = false;

const VSMenu = defineComponent({
    name: "VSMenu",
    render: () => createVNode('ui5-menu', {id: componentUid}, items)
})

function prepareItems(items) {
    let generatedItems = [];

    for (const _item of items) {
        let subItems;

        if (_item.subItems !== undefined) {
            subItems = prepareItems(_item.subItems);
        }

        let item = createVNode('ui5-menu-item', {
            "accessible-name": _item.accessibleName,
            disabled: _item.disabled,
            text: _item.text,
            "starts-section": _item.startsSection,
            icon: _item.icon
        }, subItems);

        generatedItems.push(item);
    }

    return generatedItems;
}

function handleMenu(event) {
    const menu = document.getElementById(componentUid);

    if (isMenuVisible) {
        menu.close();
    } else {
        menu.showAt(event.target);
    }

    isMenuVisible = !isMenuVisible;
}

</script>
