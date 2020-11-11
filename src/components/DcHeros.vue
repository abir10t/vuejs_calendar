<template>
  <div class="w-full flex">
    <div class="m-auto">
      <AppHeader />
      <ul>
        <li class="flex justify-between" v-for="(hero, index) in dc" :key="index">
          <div>
            {{ hero.name }}
            <button @click="remove(index)">x</button>
          </div>
        </li>
      </ul>
      <form class="mt-10" @submit.prevent="addhero()">
        <input class="border-rounded bg-orange-100" v-model="newhero" placeholder="Type item here" />
        <button class="border-rounded bg-gray-600" type="submit">Add hero</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newhero: "xy",

      dc: [
        { name: "a" },
        { name: "b" },
        { name: "c" },
        { name: "d" },
        { name: "e" },
        { name: "f" },
      ],
    };
  },
    computed: {
    heroscount() {
      return this.dc.length;
    },
  },
  methods: {
    addhero() {
      if (this.newhero != "") {
        this.dc.push({ name: this.newhero });
        this.newhero = "";
      }
    },
    remove(index) {
      this.dc = this.dc.filter((hero, i) => i != index);
    },
  },

  

}
</script>

<style>

</style>