<script setup>
  import EventInformation from './components/EventInformation.vue';
  import RegistrationForm from './components/RegistrationForm.vue';
  import NavBar from './components/NavBar.vue';
  import ContentRow from './components/ContentRow.vue';
</script>

<template>
  <div class="container-fluid"> <!-- Takes up entire width of screen -->
    <!-- Navbar Row -->
    <div class="row">
      <NavBar />
    </div>

    <!-- Content Row -->
    <ContentRow />

    <!-- Event Information -->
    <div class="row">
      <EventInformation />
    </div>

    <!-- Registration Form -->
    <div>
      <RegistrationForm />
    </div>

  </div>
</template>


