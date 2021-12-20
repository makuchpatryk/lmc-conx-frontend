<template>
  <div class="fleet-manager">
    <div class="list">
      <ul>
        <li v-for='item in activeMachine' :key="item" @click="showDeets(item)" v-bind:class="{active: isMachineDeetActive(item)}">
          <div class="make" v-text="item.make"></div>
          <div class="type" v-text="item.type"></div>
        </li>
      </ul>
    </div>
    <div class="details">
      <fleetDetail
            v-for="machine in activeMachine"
            :key="machine"
            :machine="machine" v-show="isMachineDeetActive(machine)"
        />
      <span class="no-selection" v-if="!machineDeet">
          no selection
      </span>
    </div>    
  </div>
</template>

<script>
import machines from '../api/mockApi.js'
import fleetDetail from './fleetDetail.vue'

export default {
  name: 'FleetManager',
  components: { fleetDetail },
  data: function ()
  {
    return {
      'machinesList': machines,
      'machineDeet': null
    }
  },
  computed: {
    activeMachine() {
      return this.machinesList.filter(product => product.active);
    }
  },
  methods: {
    isMachineDeetActive: function(item)
    {
      if(item == this.machineDeet)
      {
        return true;
      }
      return false;
    },
    showDeets: function(item)
    {
      if(this.machineDeet == item)
      {
        this.machineDeet = null;
      }
      else
      {
      this.machineDeet = item;
      }
    }
  }
}
</script>

<style scoped>
.list, .details {
  display: inline-block;
  margin: 20px;
  vertical-align: top;
}
.details {
  min-width: 400px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
  padding: 10px 20px;
  cursor: pointer;
}
li.active {
  background-color: #ddd;
}
.make {
  font-weight: 600;
}
.type {
  color: #777;
}
.no-selection {
  display: block;
  padding: 20px;
}
</style>
