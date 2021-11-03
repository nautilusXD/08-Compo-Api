<template>
  <div class="home">
    <h1>Reactive vs Ref</h1>

    <h2>{{ ironman }}</h2>
    <h2>{{ hulk }}</h2>

    <button @click="changeIronman">Cambiar Ironman</button>
    <button @click="changeHulk">Cambiar Hulk</button>

    <h2>{{ ironmanIsALive }}</h2>
    <h2>{{ hulkIsAlive }}</h2>
    <button @click="changeStatus">Change Status</button>
  </div>
</template>

<script>
import { ref, reactive } from "vue";
// @ is an alias to /src

export default {
  name: "Home",

  setup() {
    const ironman = ref({ name: "Tony", age: 50 });
    const hulk = reactive({ name: "Bruce", age: 50 });

    const ironmanIsALive = reactive(false);
    const hulkIsAlive = ref(true);

    const changeStatus = () => {
      hulkIsAlive.value = !hulkIsAlive.value;
    };

    return {
      ironman,
      hulk,
      ironmanIsALive,
      hulkIsAlive,
      changeStatus,
      changeIronman: () => {
        ironman.value.name = "Tony Stark";
        ironman.value.age = 55;
      },
      changeHulk: () => {
        hulk.name = "Bruce Banner";
        hulk.age = 45;
      },
    };
  },
};
</script>
