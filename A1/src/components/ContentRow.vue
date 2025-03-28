<script setup>
    import ChooseUsItem from './ChooseUsItem.vue';
</script>

<template>
    <div class="row" id="home-banner-div">
      <div class="col-12">
        <img src="../assets/event_management_img.webp" class="img-fluid w-100" alt="Event Management Banner" id="home-banner" />
      </div>
    </div>
    <div class="row">
      <div class="choose-us-content">
        <div class="col-12">
          <h2 id="why-choose-us-header">Why Choose Us</h2>
        </div>
        <div id="choose-us-row" class="row">
          <div class="col-12 col-md-6 col-lg-4 mb-4"> 
            <ChooseUsItem
              title="Event Management"
              description="Manage and track events easily with our comprehensive system."
            />
          </div>
          <div class="col-12 col-md-6 col-lg-4 mb-4">
            <ChooseUsItem
              title="More Event Management"
              description="Manage more and track events more easily with our more comprehensive system."
            />
          </div>
          <div class="col-12 col-md-6 col-lg-4 mb-4">
            <ChooseUsItem
              title="Less Event Management"
              description="Manage less and track events less easily with our less comprehensive system."
            />
          </div>
          <div class="col-12 col-md-6 col-lg-4 mb-4">
            <ChooseUsItem
              title="People Management"
              description="Manage people and track their every movement"
            />
          </div>
          <div class="col-12 col-md-6 col-lg-4 mb-4">
            <ChooseUsItem
              title="More People Management"
              description="Track employees during weekdays and after work hours"
            />
          </div>
          <div class="col-12 col-md-6 col-lg-4 mb-4">
            <ChooseUsItem
              title="Even More People Management"
              description="Track employees 24/7, know their diet and sleep patterns"
            />
          </div>
        </div>
      </div>
    </div>
</template>

<style scoped>

#home-banner-div {
  width: 100%;
  height: 50vh; 
  overflow: auto;
}

#home-banner {
  object-fit: cover; 
}

#why-choose-us-header {
  text-align: center;
}

</style>