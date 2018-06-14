<template>
<div class="hello">
  <button @click="increase($event, 2)">
    Increase by 2
  </button>
  <div>
    {{ counter }}
  </div>
  <p @mousemove="updateCoordinates($event)">
    {{`Coordinates ${x}/${y}`}}
    <span @mousemove.stop="noop()">Stops Propagation</span>
    <span @mousemove.prevent="noop()">Prevents Default Browser Behavior</span>
  </p>

  <input type="text" @keyup.enter.space="updateOnEnterAndSpace($event)">
  <p>
    {{ inputMessage }}
  </p>

  <input type="text" v-model="twoWay">
  <p>
    {{twoWay}}
  </p>

  <p :class="{
      'red': attachRed,
      blue
    }"
    @mouseover="attachRed = !attachRed"
    @mouseup="blue = !blue"
  >
    {{output}}
  </p>

  <input type="text" 
    placeholder="input class to bind to below element here"
    v-model="color"
  >
  <div :class="[color, {blue, red: attachRed}]">
    Type yellow in the input above to change this element to yellow
    And Click on 22 above to toggle blue class this to blue
  </div>
  
  <div :style="
    [ 
      styleObj, 
      {'background-color': color}
    ]
  ">
    Type yellow in the input above to change this element to yellow
    And Click on 22 above to toggle blue class this to blue
  </div>

  <button @click="show = !show">{{`show = ${show}`}}</button>
  <button @click="show2 = !show2">{{`show2 = ${show2}`}}</button>
  <p v-if="show"> v-if Here</p>
  <p v-else-if="show2">If v-if satisfies this won't render</p>
  <p v-else>If any v-if or v-else-if satisfies this doen't render</p>

  <p v-show="show">display none rather than detach like v-if</p>

  <ul>
    <li v-for="(person, index) of lists" :key="person.id">
      {{person}}
      {{index}}

      <div v-for="(value, key, index) of person" :key="index">
        {{`${key}: ${value}`}}
      </div>
    </li>
  </ul>

  <div v-for="n in 10" :key="n">
    {{n}}
  </div>

  <button @click="mount()">mount</button>
  <button @click="destroy()">Destroy</button>


</div>
</template>

<script>
export default {
  data: function() {
    return {
      counter: 0,
      x: 0,
      y: 0,
      inputMessage: ``,
      twoWay: ``,
      attachRed: false,
      blue: false,
      color: ``,
      styleObj: {
        background: `grey`,
        color: `blue`
      },
      show: true,
      show2: true,
      lists: [
        {
          id: 0,
          name: "David",
          sex: "male"
        },
        {
          id: 1,
          name: "D"
        }
      ]
    };
  },

  computed: {
    output() {
      return this.twoWay + 22;
    }
  },

  watch: {
    counter(counterValue) {
      console.log(counterValue);
      setTimeout(() => {
        this.counter = 0;
      }, 2000);
    }
  },

  methods: {
    increase(event, step) {
      this.counter = this.counter + step;
    },
    updateCoordinates(event) {
      this.x = event.clientX;
      this.y = event.clientY;
    },
    noop() {},
    updateOnEnterAndSpace(event) {
      this.inputMessage = event.target.value;
    },

    destroy() {
      this.$destroy();
    },

    mount() {
      this.$mount();
    }
  },

  beforeCreate() {
    console.log(`beforeCreate`);
  },
  created() {
    console.log(`created`);
  },
  beforeMount() {
    console.log(`beforeMount`);
  },
  mounted() {
    console.log(`mounted`);
  },
  beforeUpdate() {
    console.log(`beforeUpdate`);
  },
  updated() {
    console.log(`update`);
  },
  beforeDestroy() {
    console.log(`beforeDestroy`);
  },
  destroyed() {
    console.log(`destroyed`);
  }
};
</script>

<style scoped>
.red {
  background: red;
}
.blue {
  background: blue;
}
.yellow {
  background: yellow;
}
</style>
