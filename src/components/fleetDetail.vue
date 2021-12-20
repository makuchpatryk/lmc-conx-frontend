<template>
  <div class="detail">
      <span class="make">{{ machine.make }}</span>
      <span class="type">{{ machine.type }}</span>
      <div class="location" v-show="machine.location">
        <span class="cord">E <span v-text="machine.location.E"></span></span>
        <span class="cord">H <span v-text="machine.location.H"></span></span>
        <span class="cord">N <span v-text="machine.location.N"></span></span>
      </div>
  </div>
</template>

<script>

export default {
  name: 'fleetDetail',
  props: {
    machine: {
      type: Object,
    }
  },
}

</script>

<style scoped>
.detail {
  display: inline-block;
  padding: 20px;
}
.make {
  font-weight: 600;
  display: block;
}
.type {
  color: #777;
}
.location {
  color: #777;
  margin-top: 10px;
}
.location .cord {
  display: block;
}

</style>
