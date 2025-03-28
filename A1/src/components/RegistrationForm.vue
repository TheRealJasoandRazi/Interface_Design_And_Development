<script setup>
    import { ref, computed, watch } from 'vue';
    
    const username = ref('');
    const password = ref('');
    const confirmPassword = ref('');
    const selectedCategory = ref('Business'); 
    const selectedEvent = ref('');
    const summary = ref(false);
  
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
    
    const filteredEvents = computed(() => {
        return events.filter(event => event.category === selectedCategory.value);
    });
    
    // if the user changes the category, then set the selected event to nothing
    watch(selectedCategory, () => {
        selectedEvent.value = ''; 
        summary.value = false; 
    });
    
    // only show summary when everything is set and done correctly
    watch([username, selectedCategory, selectedEvent, password, confirmPassword], () => {
        if (username.value != '' && selectedCategory.value && selectedEvent.value != '' && password.value != '' && confirmPassword.value == password.value) {
            summary.value = true; 
        } else {
            summary.value = false;
        }
    });
  
</script>

<template>
    <div class="registration-form">
      <h1>Registration Form</h1>
  
      <div>
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" />
      </div>
  
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" />
      </div>
  
      <div>
        <label for="confirmPassword">Confirm Password:</label>
        <input type="password" id="confirmPassword" v-model="confirmPassword" />
        <!-- Show message if passwords do not match -->
        <p v-if="password && confirmPassword && password !== confirmPassword" style="color: red;">
          Passwords do not match.
        </p>
      </div>
  
      <!-- Event Category -->
      <div>
        <label>
          <input type="radio" value="Business" v-model="selectedCategory" aria-label="radio button to select business as your category for registration"/> Business
        </label>
        <label>
          <input type="radio" value="Technology" v-model="selectedCategory" aria-label="radio button to select technology as your category for registration"/> Technology
        </label>
        <label>
          <input type="radio" value="Marketing" v-model="selectedCategory" aria-label="radio button to select marketing as your category for registration"/> Marketing
        </label>
        <label>
          <input type="radio" value="Finance" v-model="selectedCategory" aria-label="radio button to select finance as your category for registration"/> Finance
        </label>
      </div>
  
      <!-- Event Name -->
      <div>
        <label for="eventName">Select Event:</label>
        <select id="eventName" v-model="selectedEvent">
          <option v-for="event in filteredEvents" :key="event.eventid" :value="event.eventname">
            {{ event.eventname }}
          </option>
        </select>
      </div>
  
      <!-- Summary -->
      <div v-if="summary">
        <h3>Summary</h3>
        <p><strong>Username:</strong> {{ username }}</p>
        <p><strong>Category:</strong> {{ selectedCategory }}</p>
        <p><strong>Event Name:</strong> {{ selectedEvent }}</p>
      </div>
    </div>
  </template>
  
  <style scoped>
  .registration-form {
    width: 50%;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
  }
  
  h1 {
    text-align: center;
  }
  
  div {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input, select {
    width: 100%;
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  
  input[type="radio"] {
    width: auto;
  }
  
  p {
    font-size: 14px;
  }
  
  summary {
    margin-top: 20px;
  }
  
  </style>
  