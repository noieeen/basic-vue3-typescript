<template>
  <div>
    <h1>{{ title }}</h1>
    <form>
      <label for="">Username</label>
      <input
        type="text"
        name="username"
        id=""
        v-model="states.account.username"
      />
      <br />
      <label for="">Password</label>
      <input
        type="text"
        name="password"
        id=""
        v-model="states.account.password"
      />
      <br />
      <button type="button" @click="onClickSubmit">Submit</button><button type="button" @click="onClickClear">Clear</button>
      <hr />
      <div>{{ states.account }}</div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, reactive } from "vue";

export default defineComponent({
    emits:['submitLogin'],
  props: ["title"],

  setup(props,{emit}) {
    const states = reactive({ account: { username: "", password: "" } });

    const onClickClear = () => {
      states.account={ username: "", password: "" }
    };

    const onClickSubmit = () => {
        emit('submitLogin')
    }

    onMounted(() => {
      console.log(props.title);
    });
    return {
      states,
      onClickClear,
      onClickSubmit
    };
  },
});
</script>
