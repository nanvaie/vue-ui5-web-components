<template>
    <ui5-calendar
        :hide-week-numbers="props.hideWeekNumbers"
        :selection-mode="props.selectionMode"
        :format-pattern="props.formatPattern"
        :max-date="props.maxDate"
        :min-date="props.minDate"
        :primary-calendar-type="props.primaryCalendarType"
        :secondary-calendar-type="props.secondaryCalendarType"
    >
        <slot></slot>
    </ui5-calendar>
</template>

<script setup>

import "@ui5/webcomponents/dist/Calendar";
import "@ui5/webcomponents-localization/dist/features/calendar/Buddhist.js";
import "@ui5/webcomponents-localization/dist/features/calendar/Islamic.js";
import "@ui5/webcomponents-localization/dist/features/calendar/Japanese.js";
import "@ui5/webcomponents-localization/dist/features/calendar/Persian.js";

const props = defineProps({
    hideWeekNumbers: {
        type: Boolean,
        default: undefined,
    },
    selectionMode: {
        type: String,
        validator(value) {
            return [
                "Single",
                "Range",
                "Multiple"
            ].includes(value);
        }
    },
    formatPattern: String,
    maxDate: String,
    minDate: String,
    primaryCalendarType: {
        type: String,
        validator(value) {
            return [
                "Gregorian",
                "Islamic",
                "Japanese",
                "Buddhist",
                "Persian",
            ].includes(value);
        }
    },
    secondaryCalendarType: {
        type: String,
        validator(value) {
            return [
                "Gregorian",
                "Islamic",
                "Japanese",
                "Buddhist",
                "Persian",
            ].includes(value);
        }
    },
});

</script>
