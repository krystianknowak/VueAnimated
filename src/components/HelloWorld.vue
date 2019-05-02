<template>
  <div class="hello">
    <h1>Skills</h1>
    <draggable v-model="myArray" ghost-class="ghost" @end="onEnd">
      <transition-group type="transition" name="flip-list">
        <div class="sortable" :id="element.id" v-for="element in myArray" :key="element.id">
          <strong>{{element.name}}</strong>
          <span>{{element.id}}</span>
        </div>
      </transition-group>
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'HelloWorld',
  components: {
    draggable
  },
  props: {
    msg: String
  },
  data() {
    return {
      myArray: [
        {name: "Angular", id:0},
        {name: "React", id:1},
        {name: "Vue", id:2},
        {name: "Html", id:3},
        {name: "CSS", id:4},
        {name: "Sass", id:5},
      ],
      oldIndex: '',
      newIndex: ''
    }
  },
  methods: {
    onEnd: function(evt) {
      console.log(evt);
      this.oldIndex = evt.oldIndex;
      this.newIndex = evt.newIndex;
    }
  }
}
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
</style>
