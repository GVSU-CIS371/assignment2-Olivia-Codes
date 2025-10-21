<template>
  <div class="baseBeverage" :class="drinkClass"></div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  drink: string;
  creamer: string;
}>();

const drinkClass = computed(() => {
  const hasCreamer = props.creamer === 'Milk' || props.creamer === 'Cream' || props.creamer === 'Half & Half';
  
  if (hasCreamer) {
    // Light colors when creamer is added
    if (props.drink === 'Green Tea') {
      return 'green-tea-with-creamer';
    } else {
      // Coffee or Black Tea with creamer
      return 'coffee-with-creamer';
    }
  } else {
    // Dark colors without creamer
    switch (props.drink) {
      case 'Coffee':
        return 'coffee';
      case 'Green Tea':
        return 'green-tea';
      case 'Black Tea':
        return 'black-tea';
      default:
        return 'coffee';
    }
  }
});
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
}

/* Dark colors without creamer */
.baseBeverage.coffee {
  background-color: #3e2723; /* Dark brown for coffee */
}

.baseBeverage.green-tea {
  background-color: #2d5016; /* Dark green for green tea */
}

.baseBeverage.black-tea {
  background-color: #553f3b; /* Dark brown for black tea */
}

/* Light colors with creamer */
.baseBeverage.coffee-with-creamer {
  background-color: #a68351ff; /* Light brown for coffee/black tea with creamer */
}

.baseBeverage.green-tea-with-creamer {
  background-color: #89d873ff; /* Light green for green tea with creamer */
}
</style>