<template>
  <div>
    <input v-model="question" type="number"/>
    <p>{{question}}</p>
    <ul>
      <li v-for="(book1,index) in books" v-bind:key="index">
        <a v-bind:style="{'fontSize':question+'px'}">{{book1.name}}:{{book1.author}}{{index}}</a>
      </li>
    </ul>
    <ul>
      <li v-for="n in evenNumbers" v-bind:key="n">{{ n }}</li>
    </ul>
    <button @click="onclick">dianji</button>
    <div style="width: 100%;height: 300px;border: 1px solid #00ffff">
      <p>{{total}}</p>
      <component2 v-on:increase="handle" v-on:reduce="handle"></component2>
    </div>
    <button-value :question1="test"></button-value>
    <h4>{{test}}</h4>
    <input type="number" v-model="test"/>
    <button-value :question2="test1"></button-value>
    <button-value></button-value>
  </div>

</template>

<script>
/* eslint-disable */
  import Component1 from './Component1'
  import Component2 from './Component2'
import bus from "./bus";

  export default {
    name: 'test1',
    components: {
      "button-value": Component1,
      Component2,
      Component3
    },
    data() {
      return {
        question: "3",
        numbers: [1, 2, 3, 4, 5],
        checkedNames: [],
        books: [
          {
            name: "Vue指南",
            author: "lilan"
          },
          {
            name: "Vue指南1",
            author: "lilan1"
          }
        ],
        test: 30,
        total:0,
        test1: [{
          data: "nihao",
          name: "lilan"
        },
          {
            data:"nihaoya",
            name:"lilan1"
          }
        ]
      }
    },
    methods: {
      onclick() {
        this.books.push({
          name: '123',
          author: '456'
        })
        console.log(this.checkedNames);
        this.test = this.test + 1;
      },
      handle(index){
        console.log(arguments);
        this.total=index;
      }
    },
    computed: {
      evenNumbers: function () {
        return this.numbers.filter(function (number) {
          return number % 2 === 0
        })
      }
    }
  }
</script>

<style scoped>

</style>
