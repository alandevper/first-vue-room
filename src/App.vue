<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i" >{{ menu }}</a>
  </div>

  <transition name="fade">
    <RoomModal :room="rooms[selectedRoomIdx]" 
                @closeRoomModal="isOpenRoomModal = false" 
                v-if="isOpenRoomModal"/>
  </transition>

   <div v-for="(room, i) in rooms" :key="i">
    <img class="room-img" :src="room.image" />
    <h4 class="room-title" @click="isOpenRoomModal = true;selectedRoomIdx = i;">{{ room.title }}</h4>
    <p>{{ room.price }}원</p>
   </div>
</template>

<script>

import rooms from './data/rooms.js';
import RoomModal from './components/room.vue';


export default {
  name: 'App',
  data() {
    return{
      rooms : rooms,
      selectedRoomIdx : 0,
      isOpenRoomModal : false,
      menus : [ 'Home', 'Product', 'About'],
    }
  },
  components: {
    RoomModal : RoomModal,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
.menu {
  background : darkslateblue;
  padding: 15px;
}

.menu a {
  padding: 15px;
  color: #ffffff;
}

.room-img {
  width: 100%;
  margin-top: 10px;
}
.room-title {
  cursor:pointer;
}

body {
  margin:0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width:100%;
  height:100%;
  background: rgba(0, 0, 0, 0.5);
  position:fixed;
  padding:20px;
}
.white-bg {
  width:100%;
  background: white;
  border-radius: 8px;
  padding:20px;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}
</style>
