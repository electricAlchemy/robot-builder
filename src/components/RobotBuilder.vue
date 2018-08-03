<template>
  <div>
    <h1>{{ msg }}</h1>
    <div>
    <div class="top-row">
      <div class="top part">
        <img v-bind:src="availableParts.heads[selectedHeadIndex].src" title="head"/>
        <button v-on:click="selectPrevHead()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img v-bind:src="availableParts.arms[selectedLeftArmIndex].src" title="left arm"/>
        <button v-on:click="selectPrevLeftArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img v-bind:src="availableParts.torsos[selectedTorsoIndex].src" title="torso"/>
        <button v-on:click="selectPrevTorso()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img v-bind:src="availableParts.arms[selectedRightArmIndex].src" title="right arm"/>
        <button v-on:click="selectPrevRightArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img v-bind:src="availableParts.bases[selectedBaseIndex].src" title="base"/>
        <button v-on:click="selectPrevBase()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextBase()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>

  </div>
</template>

<script>
import availableParts from '../data/parts';

function getPreviousValidIndex( index, length ){
  const decrementedIndex = index - 1;
  return (decrementedIndex <  0) ? length - 1 : decrementedIndex;
}
function getNextValidIndex ( index, length ) {
  const incrementedIndex = index + 1;
  return (incrementedIndex > length - 1) ? 0 : incrementedIndex;
}
export default {
  name: 'Robot-Builder',
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedLeftArmIndex: 0,
      selectedRightArmIndex: 0,
      selectedTorsoIndex: 0,
      selectedBaseIndex: 0
    };
  },
  methods: {
    selectNextHead() {
      this.selectedHeadIndex = getNextValidIndex(this.selectedHeadIndex, availableParts.heads.length);
      console.log('this.selectedHeadIndex', this.selectedHeadIndex)
    },
    selectPrevHead() {
      this.selectedHeadIndex = getPreviousValidIndex(this.selectedHeadIndex, availableParts.heads.length);
      console.log('this.selectedHeadIndex', this.selectedHeadIndex);
    },
    selectNextLeftArm(){
      this.selectedLeftArmIndex++
    },
    selectPrevLeftArm(){
      this.seletedLeftArmIndex--
    },
    selectNextRightArm(){
      this.selectedRightArmIndex++
    },
    selectPrevRightArm(){
      this.selectedRightArmIndex--
    },
    selectNextTorso(){
      this.selectedTorsoIndex++
    },
    selectPrevTorso(){
      this.selectedTorsoIndex--
    },
    selectNextBase(){
      this.selectedBaseIndex++
    },
    selectPrevBase(){
      this.selectedBaseIndex--
    }

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
