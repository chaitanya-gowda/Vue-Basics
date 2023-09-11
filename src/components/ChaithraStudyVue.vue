<template>
  <div>
    <!-- <h6 class="user">ref : {{ users }}</h6> -->
    <h6 class="user">reactive : {{ reactiveUser.name }}</h6>
    <h6 class="user">ref : {{ user.name }}</h6>
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
      name: 'chaithra',
      age: -2,
    });

    // reactive

    const reactiveUser = reactive({
      name: 'chaithra',
      age: 27,
    });
    console.log('ref value', users.value);
    setTimeout(() => {
      users.value = users.value.map((value) => value + ' loose');

      //reactiveUser
      reactiveUser.name = reactiveUser.name + ' mentlu';
      reactiveUser.age = 28;

      // refUser
      user.value.name = user.value.name + ' Hahaha';
    }, 2000);

    // const computedValue: computed(()=>{
    //   return reactiveUser.

    // })

    // watch(user.value, (oldValue, newValue) => {
    //   console.log('old value', oldValue);
    //   console.log('new value', newValue);
    // });
    return { users, reactiveUser, user };
  },
};
</script>
<style scoped>
.user {
  background-color: white;
  color: blue;
}
</style>
