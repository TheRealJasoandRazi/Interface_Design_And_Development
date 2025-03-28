<script setup>

import { ref, computed } from 'vue';

var events = [
  {eventid: 'EVT10001', eventname: 'Tech Innovations Conference', category: 'Technology', durationhour: 8},
  {eventid: 'EVT10002', eventname: 'Startup Pitch Day', category: 'Business', durationhour: 6},
  {eventid: 'EVT10003', eventname: 'AI & Machine Learning Summit', category: 'Technology', durationhour: 10},
  {eventid: 'EVT10004', eventname: 'Cybersecurity Workshop', category: 'Technology', durationhour: 4},
  {eventid: 'EVT10005', eventname: 'Digital Marketing Bootcamp', category: 'Marketing', durationhour: 6},
  {eventid: 'EVT10006', eventname: 'Blockchain and Cryptocurrency', category: 'Finance', durationhour: 5},
  {eventid: 'EVT10007', eventname: 'Entrepreneurship Forum', category: 'Business', durationhour: 7},
  {eventid: 'EVT10008', eventname: 'Data Science Hackathon', category: 'Technology', durationhour: 12},
  {eventid: 'EVT10009', eventname: 'Leadership and Management Summit', category: 'Business', durationhour: 9},
  {eventid: 'EVT10010', eventname: 'E-commerce Strategies', category: 'Marketing', durationhour: 6},
  {eventid: 'EVT10011', eventname: 'AI for Business', category: 'Business', durationhour: 8},
  {eventid: 'EVT10012', eventname: 'IoT & Smart Devices Expo', category: 'Technology', durationhour: 7},
  {eventid: 'EVT10013', eventname: 'Brand Strategy and Growth', category: 'Marketing', durationhour: 5},
  {eventid: 'EVT10014', eventname: 'Investment and Wealth Management', category: 'Finance', durationhour: 6},
  {eventid: 'EVT10015', eventname: 'Financial Technology (FinTech) Summit', category: 'Finance', durationhour: 8},
  {eventid: 'EVT10016', eventname: 'AI Ethics and Regulations', category: 'Technology', durationhour: 4},
  {eventid: 'EVT10017', eventname: 'Business Analytics Workshop', category: 'Business', durationhour: 6},
  {eventid: 'EVT10018', eventname: 'SEO and Content Marketing', category: 'Marketing', durationhour: 7},
  {eventid: 'EVT10019', eventname: 'Cryptocurrency Investment Strategies', category: 'Finance', durationhour: 9},
  {eventid: 'EVT10020', eventname: 'Social Media Marketing Trends', category: 'Marketing', durationhour: 5}
]
const selectedCategory = ref('All'); //initialises variable with the value 'All'
const searchedCategoryEventId = ref('');
const searchedCategoryEventName = ref('');
const searchedCategoryDuration = ref('');

var filteredEvents = events;

filteredEvents = computed(() => {
  return events.filter(event => {
    
    const categoryMatch = selectedCategory.value === 'All' || event.category === selectedCategory.value;

    const eventIdMatch = !searchedCategoryEventId.value || event.eventid.includes(searchedCategoryEventId.value);

    // if the value is an empty string it will return true, otherwise it will check if the value is apart of the events array item
    const eventNameMatch = !searchedCategoryEventName.value || event.eventname.toLowerCase().includes(searchedCategoryEventName.value.toLowerCase());

    const durationMatch = !searchedCategoryDuration.value || event.durationhour == searchedCategoryDuration.value;
    // Return the event if all conditions match
    return categoryMatch && eventIdMatch && eventNameMatch && durationMatch;
  });
});

</script>

<template>
    <div class="row">
        <h1 style="text-align: center;"> Event List </h1>
    </div>

    <!-- Filtering Buttons -->
    <div class="filter-container">
        <!-- Radio Buttons -->
        <div class="radio-buttons">
            <label>
                <input type="radio" value="All" v-model="selectedCategory" aria-label="radio button to filter for all categories"/> All
            </label>
            <label>
                <input type="radio" value="Technology" v-model="selectedCategory" aria-label="radio button to filter for technology categories"/> Technology
            </label>
            <label>
                <input type="radio" value="Business" v-model="selectedCategory" aria-label="radio button to filter for business categories"/> Business
            </label>
            <label>
                <input type="radio" value="Marketing" v-model="selectedCategory" aria-label="radio button to filter for marketing categories"/> Marketing
            </label>
            <label>
                <input type="radio" value="Finance" v-model="selectedCategory" aria-label="radio button to filter for finance categories"/> Finance
            </label>
        </div>

        <!-- Text Inputs -->
        <div class="inputs">
            <input type="text" v-model="searchedCategoryEventId" placeholder="Event ID" class="input-field" aria-label="input field to filter for event id"/>
            <input type="text" v-model="searchedCategoryEventName" placeholder="Event Name" class="input-field" aria-label="input field to filter for event name"/>
            <input type="text" v-model="searchedCategoryDuration" placeholder="Duration" class="input-field" aria-label="input field to filter for event duration"/>
        </div>
    </div>



    <div class="row">
        <table id="EventsInformationTable">
        <thead>
            <tr>
            <th>Event ID</th>
            <th>Event Name</th>
            <th>Category</th>
            <th>Duration (hours)</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="event in filteredEvents" :key="event.eventid">
            <td>{{ event.eventid }}</td>
            <td>{{ event.eventname }}</td>
            <td>{{ event.category }}</td>
            <td>{{ event.durationhour }}</td>
            </tr>
        </tbody>
        </table>
    </div>
</template>

<style scoped>

.filter-container {
    display: flex; /* allows to arrange elements in row */
    justify-content: space-between;
}

.radio-buttons {
    display: flex;
    gap: 10px;
}

.inputs {
    display: flex;
    gap: 10px;
}

.input-field {
    padding: 5px;
    font-size: 14px;
}

#EventsInformationTable {
    padding: 12px;
    margin: 16px;
}

#EventsInformationTable tbody tr:nth-child(odd) {
  background-color: #f2f2f2; 
}

#EventsInformationTable tbody tr:nth-child(even) {
  background-color: white; 
}

</style>