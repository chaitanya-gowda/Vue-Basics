<template>
  <div>
    <h1>{{ userName }}</h1>
    <h2>{{ userAge }}</h2>
  </div>
</template>
<script>
import { computed, inject } from 'vue';
export default {
  name: 'UserData',
  props: ['firstName', 'lastName', 'userAgeData'],
  setup(props, context) {
    const user = computed(() => {
      return props.firstName + '' + props.lastName;
    });
    //inject
    const age = inject('user-age');
    console.log('ageee', age.value);
    // context.emit('add-data',data_value)
    console.log('context', context);
    return { userName: user, userAge: age.value.age };
  },
};
</script>
<style></style>
