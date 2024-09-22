<template>
  <div id="menu-container">
    <!-- Main button -->
    <button id="menu-btn" @click="toggleMenu">Menu</button>

    <!-- Spawned buttons (conditionally shown) -->
    <button v-if="isMenuActive" class="menu-item top" @click="action('Top')">
      Apple
    </button>
    <button
      v-if="isMenuActive"
      class="menu-item bottom"
      @click="action('Bottom')"
    >
      Banana
    </button>
    <button v-if="isMenuActive" class="menu-item left" @click="action('Left')">
      Kiwi
    </button>
    <button
      v-if="isMenuActive"
      class="menu-item right"
      @click="action('Right')"
    >
      Grape
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isMenuActive = ref(false);

const toggleMenu = () => {
  isMenuActive.value = !isMenuActive.value;
};

const action = (direction) => {
  alert(`Button clicked: ${direction}`);
};
</script>

<style scoped>
#menu-container {
  position: relative;
  width: 200px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
}

#menu-btn {
  width: 80px;
  height: 80px;
  background-color: black;
  border-radius: 10%;
  position: relative;
  cursor: pointer;
}
/* using a class allows me to make a general styling for all the menu items but then below I can call the specific "instances" to style them individually - this makes for less repetitive code :D */
.menu-item {
  position: absolute;
  width: 70px;
  height: 60px;
  background-color: black;
  border-radius: 10%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

/* Positioning for the 4 buttons individually*/
.top {
  top: -30px;
}

.bottom {
  bottom: -30px;
}

.left {
  left: -30px;
}

.right {
  right: -30px;
}
</style>
