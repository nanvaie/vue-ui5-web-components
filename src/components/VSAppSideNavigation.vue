<template>
    <ui5-side-navigation
        :collapsed="props.collapsed"
        :default-items="props.defaultItems"
        :fixed-items="props.fixedItems"
    >
        <slot></slot>

        <ui5-side-navigation-item
            v-for="_defaultItem of props.defaultItems"
            :expanded="_defaultItem.expanded"
            :icon="_defaultItem.icon"
            :selected="_defaultItem.selected"
            :text="_defaultItem.text"
            :whole-item-toggleable="_defaultItem.wholeItemToggleable"
        >
            <template v-if="_defaultItem.subItems !== undefined">
                <ui5-side-navigation-sub-item
                    v-for="_defaultSubItem of _defaultItem.subItems"
                    :icon="_defaultSubItem.icon"
                    :selected="_defaultSubItem.selected"
                    :text="_defaultSubItem.text"
                ></ui5-side-navigation-sub-item>
            </template>
        </ui5-side-navigation-item>

        <ui5-side-navigation-item
            v-for="_fixedItems of props.fixedItems"
            :expanded="_fixedItems.expanded"
            :icon="_fixedItems.icon"
            :selected="_fixedItems.selected"
            slot="fixedItems"
            :text="_fixedItems.text"
            :whole-item-toggleable="_fixedItems.wholeItemToggleable"
        >
            <template v-if="_fixedItems.subItems !== undefined">
                <ui5-side-navigation-sub-item
                    v-for="_fixedSubItem of _fixedItems.subItems"
                    :icon="_fixedSubItem.icon"
                    :selected="_fixedSubItem.selected"
                    :text="_fixedSubItem.text"
                ></ui5-side-navigation-sub-item>
            </template>
        </ui5-side-navigation-item>

    </ui5-side-navigation>
</template>

<script setup>

import "@ui5/webcomponents-fiori/dist/SideNavigation";
import "@ui5/webcomponents-fiori/dist/SideNavigationItem";
import "@ui5/webcomponents-fiori/dist/SideNavigationSubItem";

const props = defineProps({
    collapsed: {
        type: Boolean,
        default: undefined
    },
    defaultItems: Object,
    fixedItems: Object,
});

</script>
