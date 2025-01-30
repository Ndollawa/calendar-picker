<template>
  <div class="calendar-picker">
     <VueDatePicker v-model="date" range multi-calendars position="left"
        :enable-time-picker="false"
        ignore-time-validation
        :markers="markers"
        :action-row="{ showNow: false, showPreview: false, showCancel:false, showSelect:false}"
        placeholder="Select Date">
        <template #action-row="{ internalModelValue, selectDate }">
        <div class="action-row">
          <div class="shortcuts">
      <button @click="selectDays(7)">7 Days</button>
      <button @click="selectDays(15)">15 Days</button>
      <button @click="selectDays(30)">30 Days</button>
      <button @click="selectMonths(1)">1 Month</button>
      <button @click="selectMonths(3)">3 Months</button>
    </div>
        </div>
      </template>
    </VueDatePicker>
  </div>
   
</template>
<style >
.calendar-picker{
  display: flex;
  width:18rem;
  margin-top: -10rem;
}
:root{
    /*General*/
    --dp-font-family: -apple-system, blinkmacsystemfont, "Segoe UI", roboto, oxygen, ubuntu, cantarell, "Open Sans",
    "Helvetica Neue", sans-serif;
    --dp-border-radius: 0.8rem; /*Configurable border-radius*/
    --dp-cell-border-radius: 0.5rem; /*Specific border radius for the calendar cell*/
    --dp-common-transition: all 0.1s ease-in; /*Generic transition applied on buttons and calendar cells*/

 /*Sizing*/
    --dp-button-height: 40px; /*Size for buttons in overlays*/
    --dp-month-year-row-height: 40px; /*Height of the month-year select row*/
    --dp-month-year-row-button-size: 40px; /*Specific height for the next/previous buttons*/
    --dp-button-icon-height: 20px; /*Icon sizing in buttons*/
    --dp-cell-size: 40px; /*Width and height of calendar cell*/
    --dp-cell-padding: 5px; /*Padding in the cell*/
    --dp-common-padding: 2rem; /*Common padding used*/
    --dp-input-icon-padding: 40px; /*Padding on the left side of the input if icon is present*/
    --dp-input-padding: 8px 32px 8px 14px; /*Padding in the input*/
    --dp-menu-min-width: 260px; /*Adjust the min width of the menu*/
    --dp-action-buttons-padding: 2px 5px; /*Adjust padding for the action buttons in action row*/
    --dp-row-margin:  5px 0; /*Adjust the spacing between rows in the calendar*/
    --dp-calendar-header-cell-padding:  0.5rem; /*Adjust padding in calendar header cells*/
    --dp-two-calendars-spacing:  2rem; /*Space between multiple calendars*/
    --dp-overlay-col-padding:  3px; /*Padding in the overlay column*/
    --dp-time-inc-dec-button-size:  32px; /*Sizing for arrow buttons in the time picker*/
    --dp-menu-padding: 8px 12px; /*Menu padding*/
    
    /*Font sizes*/
    --dp-font-size: 1rem; /*Default font-size*/
    --dp-preview-font-size: 0.8rem; /*Font size of the date preview in the action row*/
    --dp-time-font-size: 0.8rem; /*Font size in the time picker*/
}

.dp__theme_light {
    --dp-background-color: #fff;
    --dp-text-color: #959595;
    --dp-hover-color: #f3f3f3;
    --dp-hover-text-color: #212121;
    --dp-hover-icon-color: #959595;
    --dp-primary-color: #000000FF;
    --dp-primary-disabled-color: #6bacea;
    --dp-primary-text-color: #f8f5f5;
    --dp-highlight-color: rgb(25 118 210 / 10%);
    --dp-range-between-dates-background-color: var(--dp-hover-color, #f3f3f3);
    --dp-range-between-dates-text-color: var(--dp-hover-text-color, #212121);
    --dp-range-between-border-color: var(--dp-hover-color, #f3f3f3);
}
.dp__cell_auto_range_end, .dp__date_hover_end:hover, .dp__range_end {
    border-end-start-radius: var(--dp-cell-border-radius); 
    border-start-start-radius: var(--dp-cell-border-radius);
}
.dp__cell_auto_range_start, .dp__date_hover_start:hover, .dp__range_start {
    border-end-end-radius:  var(--dp-cell-border-radius);
    border-start-end-radius:  var(--dp-cell-border-radius);
}
.dp__today {
 border:none;
}
.dp__menu{
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
  padding: 5px;
}
.shortcuts {
  margin-inline: 1rem;
  display: flex;
  align-items: center;
  gap:10px
}
.shortcuts > button{
padding: 0.5rem 1rem;
background:#fff;
color:rgb(134, 134, 134);
box-shadow:0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
border:1px solid rgb(230, 228, 228);
border-radius: var(--dp-cell-border-radius);
}
</style>
<script setup lang="ts">
import { ref,onMounted } from 'vue';
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'
import { addDays, subDays, format, subMonths, addMonths  } from 'date-fns'

const date = ref();
const markers = ref([
  {
    date: addDays(new Date(),0),
    type: 'dot',
    color: "black",
    tooltip: [{ text: 'Dot with tooltip', color: 'black' }],
  },
  
])
const formatDate = (date: Date) => {
  return format(date, 'dd.MM.yyyy, HH:mm');
};

const startDate = ref('')
const endDate = ref('')

// Logic for selecting Days
const selectDays = (days:number) => {
 const startDate = format(new Date(), 'yyyy-MM-dd')
const endDate = format(addDays(new Date(), days), 'yyyy-MM-dd')
  date.value = [startDate, endDate];
}



// Logic for selecting Months
const selectMonths = (months:number) => {
 const startDate = format(new Date(), 'yyyy-MM-dd')
 const endDate = format(addMonths(new Date(), months), 'yyyy-MM-dd')
  date.value = [startDate, endDate];
}

// onMounted(() => {
//   const startDate = new Date();
//   const endDate = new Date(new Date().setDate(startDate.getDate() + 7));
//   date.value = [startDate, endDate];
//   // date.value = "Select Date";
// });
</script>