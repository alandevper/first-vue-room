<template>
  <div class="black-bg">
    <div class="white-bg">
      <img class="room-img" :src="room.image" />
      <h4>{{room.title}}</h4>
      <p>{{room.content}}</p>
      <p>{{room.price}} 원</p>
      <button @click="$emit('closeRoomModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'RoomModal',
    props: {
        room : Object,
    }
}
</script>

<style>

</style>