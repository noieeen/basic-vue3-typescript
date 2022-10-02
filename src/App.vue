<template>
  <div>
    <h1>Hello</h1>
    <h2>count1: {{ count1 }}</h2>
    <hr />
    <h2>count2: {{ count2 }}</h2>
    <button @click="onClickAdd1">Add 1</button>
    <button @click="onClickAdd2">Add 2</button>
    <hr />
    <h4>account: {{ states.account }}</h4>
    <button @click="onClickClear">Clear Account</button>

    <LoginForm/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive, onMounted } from "vue";
import LoginForm from '@/components/LoginForm.vue'

const defaultAcc = { username: "", password: "" };
export default defineComponent({
    setup() {
        let count1 = 10;
        const count2 = ref<number>(32);
        const states = reactive({
            account: { username: "admin", password: "1234" },
        });
        onMounted(() => {
            console.log("Ready");
        });
        const onClickAdd1 = () => {
            count1++;
            console.log(count1);
        };
        const onClickAdd2 = () => {
            count2.value++;
            console.log(count2.value);
        };
        const onClickClear = () => {
            // account.username=''
            // account.password=''
            states.account = defaultAcc;
            console.log(states.account);
        };
        return {
            count1,
            count2,
            onClickAdd1,
            onClickAdd2,
            states,
            onClickClear,
        };
    },
    components: { LoginForm }
});
</script>
