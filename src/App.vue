<template>
  <div id="app">
    <h1>Shape plotter APP</h1>
      <app-canvas>
        <circle v-bind:cx="cxIn" v-bind:cy="cyIn" v-bind:r="rIn" v-bind:fill="colorFill" stroke="black" stroke-width="1" />
        <rect v-bind:x="xIn" v-bind:y="yIn" v-bind:width="widthIn" v-bind:height="heightIn" v-bind:fill="colorFill" stroke="black" stroke-width="1" />
        <!-- <polygon v-bind:points="200,10 250,190 160,210" v-bind:fill="rColor"/> -->
      </app-canvas>
      <textarea class="commands" v-on:keyup="textApi" rows="4" cols="50"></textarea>
    <div class="circleIn">
      <h3>Circle Coordinates</h3>
      <div class=textIn><label>Circle cx</label><input type="text" v-model="cxIn"></div>
      <div class=textIn><label>Circle cy</label><input type="text" v-model="cyIn"></div>
      <div class=textIn><label>Circle r</label><input type="text" v-model="rIn"></div>
    </div>
    <div class="rectIn">
      <h3>Rectangle Coordinates</h3>
      <div class=textIn><label>Rectangle x</label><input type="text" v-model="xIn"></div>
      <div class=textIn><label>Rectangle y</label><input type="text" v-model="yIn"></div>
      <div class=textIn><label>Rectangle width</label><input type="text" v-model="widthIn"></div>
      <div class=textIn><label>Rectangle height</label><input type="text" v-model="heightIn"></div>
    </div>
    <div class="output">
      <h3>Output</h3>
      <p>{{ output }}</p>
    </div>
    <button @click="rColor">randomize Color</button>
  </div>
</template>

<script>
import canvas from './components/canvas'

export default {
  name: 'app',
  data:
    function () {
      return {
        cxIn: 125,
        cyIn: 125,
        rIn: 50,
        xIn: 30,
        yIn: 30,
        widthIn: 30,
        heightIn: 30,
        colorFill: '#000000',
        output: ' '
      }
    },
  computed: {

  },
  components: {
    'app-canvas': canvas
  },
  methods: {
    textApi: function (event) {
      if (event.key === 'r') {
        console.log('rectangle init')
        let vm = this
        let comment = 'rectangle init'
        vm.output = comment
        return vm.output
        // ...
      } else if (event.key === 'c') {
        console.log('circle init')
        let vm = this
        let comment = 'circle init'
        vm.output = comment
        return vm.output
        // ...
      } else if (event.key === 'p') {
        console.log('polygon init')
        let vm = this
        let comment = 'polygon init'
        vm.output = comment
        return vm.output
        // ...
      } else {
        console.log(`${event.key} was pressed!`)
        let vm = this
        let comment = `${event.key} was pressed!`
        vm.output = comment
        return vm.output
        // ...
      }
    },
    rColor: function () {
      var vm = this
      vm.colorFill = '#' + Math.floor(Math.random() * 16777215).toString(16)
      console.log(vm.colorFill)
      return vm.colorFill
    } // ,
    // async drawRec () {
    //   const ?? = await rectangle coordinates
    // }
    // ,
    // async drawCircle () {
    //   const ?? = await circle coordinates
    // }
    // ,
    // async drawPoly () {
    //   const ?? = await polygon coordinates
    // }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0d1218;
  margin-top: 60px;
}
.rectIn {
  display: inline-block;
  width: 50%
}
.circleIn {
  display: inline-block;
  width: 50%
}
.commands {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.textIn {
  display: block;
  padding: 5px;
}
label {
  text-align: left
}
</style>
