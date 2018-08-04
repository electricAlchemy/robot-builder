<template>
  <div>
    <h1>{{ msg }}</h1>
    <div style="padding-top: 2%">
    <div class="top-row">
        <!-- <div class="robot-name">{{selectedRobot.head.title}}</div>
        <img v-bind:src="selectedRobot.head.src" title="head"/> -->
       <PartSelector :parts="availableParts.heads"
                     position="top"
        />
      </div>
    </div>
    <div class="middle-row">
      <PartSelector :parts="availableParts.arms" 
                    position="left"
      />
      <PartSelector :parts="availableParts.torsos" 
                    position="center"
      />
      <PartSelector :parts="availableParts.arms" 
                    position="right"
      />
    </div>
    <div class="bottom-row">
      <PartSelector :parts="availableParts.bases"
                    position="bottom"
      />
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts';
import createdHook from '../mixins/created-hook-mixin';
import PartSelector from './PartSelector.vue';

export default {
  name: 'Robot-Builder',
  components: { PartSelector },
  mixins: [createdHook],
  data() {
    return {
      availableParts,
    };
  },
  computed: {
    selectedRobot(){
      return {
        head: {},
        leftArm: {},
        torso: {},
        rightArm: {},
        base: {},
      }
    }
  },
  methods: {
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.part {
  position: relative;
  width:165px;
  height:165px;
  border: 3px solid #aaa;
}
.part img {
  width:165px;
}
.top-row {
  display:flex;
  justify-content: space-around;
}
.middle-row {
  display:flex;
  justify-content: center;
}
.bottom-row {
  display:flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector, .center .next-selector {
  opacity:0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}

</style>
