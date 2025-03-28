<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
})
</script>

<template>
    <div class="itemBox">
      <h6 class="itemTitle">
        {{ title }}
      </h6>
      <div class="itemDescription">
        {{ description }}
      </div>
    </div>
</template>

<style scoped>
.itemBox {
  background-color: #fff;
  border: 1px solid #ddd; /* Light border */
  border-radius: 8px; /* Rounded corners */
  padding: 16px; /* Add some space inside the box */
  width: 100%;
  max-width: 400px; /* Limit the width */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow */
  margin: 10px auto; /* Center the box horizontally */
}

.itemTitle {
  font-weight: bold;
  font-size: 1.2rem;
  margin-bottom: 8px; /* Add some space below the title */
}

.itemDescription {
  font-size: 1rem;
  color: #555;
}
</style>
