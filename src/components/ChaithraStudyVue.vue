<template>
  <div>
    <!-- <h6 class="user">ref : {{ users }}</h6> -->
    <h6 class="user">reactive : {{ reactiveUser.name }}</h6>
    <!-- <h6 class="user">ref : {{ user.name }}</h6> -->

    <!--
    <h6 class="user">Computed : {{ computedData }}</h6>
    -->
    <!-- <h6 class="user">Watch : {{ watchData }}</h6> -->
    <!-- <input type="text" placeholder="enter name" v-model="compUser" /> -->
    <button @click="setName">Methods : SetName</button>
  </div>
</template>

<script>
import { ref, reactive, watch, computed } from 'vue';

export default {
  name: 'Mentlu Code',
  components: {},
  props: [],
  setup() {
    // 'this' keyword cannot be used in setup
    console.log(' chaithra setup created');
    const users = ref(['chaithra', 'chaitanya']);
    const user = ref({
      name: 'thanu',
      age: -2,
    });

    //computed
    const compUser = ref('');

    // watch
    const watchData = ref('thanu');

    // reactive

    const reactiveUser = reactive({
      name: 'thanu',
      age: 27,
    });
    console.log('ref value', users.value);
    // setTimeout(() => {
    //   users.value = users.value.map((value) => value + ' loose');

    //   //reactiveUser
    //   reactiveUser.name = reactiveUser.name + ' mentlu';
    //   reactiveUser.age = 28;

    //   // refUser
    //   user.value.name = user.value.name + ' Hahaha';
    // }, 2000);

    // const computedValue: computed(()=>{
    //   return reactiveUser.

    // })

    // watch;
    watch(reactiveUser.name, function (newValue, oldValue) {
      console.log('old value', oldValue);
      console.log('new value', newValue);
    });

    //methods

    function setName() {
      console.log('clicked');
      // user.value.name = 'thanu';
      reactiveUser.name = 'chaithra';
    }
    // function setOnChange(event) {
    //   compUser.value = event.target.value;
    // }

    // computed
    // computed properties are read only.. cannot able to overwrite the value

    const computedData = computed(function () {
      return compUser.value;
    });
    console.log('userdata', computedData);

    // setup return
    return {
      users,
      reactiveUser,
      user,
      setName,
      compUser,
      computedData,
      watchData,
    };
  },
};
</script>
<style scoped>
.user {
  background-color: white;
  color: blue;
}
</style>
