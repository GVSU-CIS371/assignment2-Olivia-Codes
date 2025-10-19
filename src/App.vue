<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'" />
    <ul>
      <li>
        <h3>Temperature</h3>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      
      <li>
        <h3>Base Beverage</h3>
        <template v-for="beverage in baseBeverages" :key="beverage">
          <label>
            <input
              type="radio"
              name="baseBeverage"
              :id="`b${beverage}`"
              :value="beverage"
              v-model="currentBeverage"
            />
            {{ beverage }}
          </label>
        </template>
      </li>
      
      <li>
        <h3>Creamer</h3>
        <template v-for="creamer in creamers" :key="creamer">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`c${creamer}`"
              :value="creamer"
              v-model="currentCreamer"
            />
            {{ creamer }}
          </label>
        </template>
      </li>
      
      <li>
        <h3>Syrup</h3>
        <template v-for="syrup in syrups" :key="syrup">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`s${syrup}`"
              :value="syrup"
              v-model="currentSyrup"
            />
            {{ syrup }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp } from "./stores/beverage";

// bev options
const baseBeverages = ['Coffee', 'Green Tea', 'Black Tea'];
const currentBeverage = ref('Coffee');

// cream options
const creamers = ['No Creamer', 'Milk', 'Cream', 'Half & Half'];
const currentCreamer = ref('No Creamer');

// syrup options
const syrups = ['No Syrup', 'Vanilla', 'Caramel', 'Hazelnut'];
const currentSyrup = ref('No Syrup');
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}

ul {
  list-style: none;
  padding: 20px;
  
  li {
    margin-bottom: 20px;
    
    h3 {
      color: #fff;
      margin-bottom: 10px;
      font-size: 16px;
    }
    
    label {
      display: block;
      color: #fff;
      margin-bottom: 8px;
      cursor: pointer;
      
      input[type="radio"] {
        margin-right: 8px;
        cursor: pointer;
      }
      
      &:hover {
        color: #ffd89b;
      }
    }
  }
}
</style>
