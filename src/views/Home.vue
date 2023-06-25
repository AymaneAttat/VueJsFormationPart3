<template>
  <h1 ref="header">Home Page</h1>  
  <p>my name {{name}} - my age is {{age}}</p>
  <p>{{person1.name}} </p>
  <p>{{person2.name}} </p>
  <button @click="age++">Inc Age</button>
  <button @click="sayHello">Salam</button>
  <hr>
  <input type="text" v-model="search">
  {{search}}
  <div v-for="course in result">{{course}} </div>
  <hr>
  <button @click="handleWatch">Stop</button>
</template>

<script>
import { computed, reactive, ref, watch, watchEffect } from 'vue'

export default {
  name: 'Home',
  setup() {
    let header = ref(null);
    //My data
    //let name = "Aymane Attat"; variable non réactive
    //let age = 23; variable non réactive
    let name = ref("Aymane Attat");
    let age = ref(23);
    let person1 = ref({name: "brahim Idbrahimi", age: 2});
    let person2 = reactive({name: "Walid Idbrahim", age: 2});

    const search = ref('');
    const courses = ref(['angular', 'reactjs', 'vuejs', 'nodejs', 'laravel', 'spring boot']);

    //Computed
    const result = computed(() => {
      return courses.value.filter(course => course.includes(search.value))
    });

    //Watch & WatchEffect
    const stopWatch = watch(search, () => {
      console.log('I watch ', search.value)
    })

    const stopWatchEffect = watchEffect(() => {
      console.log('watch effect', search.value)
    })

    //My methods
    const sayHello = () => {
      console.log(header.value)
      header.value.classList.add('my-4')
      header.value.textContent = 'Welcome to bright codinig'
      name.value = "Walid"
      person1.value.name = "Khalid"
      person2.name = "Said"
    }

    const handleWatch = () => {
      stopWatch()
      stopWatchEffect()
    }

    //return {name: name, age: age} ou
    return {name, age, sayHello, header, person1, person2, courses, search, result, handleWatch}
  }
}
</script>
