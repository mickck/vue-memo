<template>
  <Modal
    :datas="datas"
    :modalClicked="modalClicked"
    :getNumber="getNumber"
    @modalX="modalClicked = false"
    @modifyaMemo="
      moMemo = $event;
      modifyMemo();
    "
  />
  <div class="max-w-2xl mx-auto">
    <Header />

    <div class="flex mt-10 items-center">
      <span class="absolute text-lg pl-3">Write:</span>
      <input placeholder="Write your memo." class="border py-7 px-20 mr-5 w-full rounded-md shadow-sm text-lg" v-model="input" type="text" />
      <button class="bg-blue-400 text-white w-32 shadow-sm rounded-md hover:bg-blue-500 py-7" @click="makeMemo">Click</button>
    </div>
    <div class="py-3 space-y-4 pt-5">
      <div class="" v-for="(data, i) in datas" :key="i">
        <div
          class="border border-gray-300 p-5 rounded-md cursor-pointer"
          @click="
            getNumber = i;
            modalClicked = true;
          "
        >
          {{ data }}
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/layout/Header.vue";
import Footer from "./components/layout/Footer.vue";
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: { Header, Footer, Modal },
  data() {
    {
      return {
        datas: ["Memo: 1", "Memo: 2", "Memo: 3", "Memo: 4", "Memo: 5", "Memo: 6"],
        input: "",
        modalClicked: false,
        getNumber: 0,
        moMemo: "",
      };
    }
  },
  methods: {
    makeMemo() {
      this.datas.push(this.input);
      this.input = "";
    },
    modifyMemo() {
      // this.datas.push(this.moMemo);
      this.datas.splice(this.getNumber, 1, this.moMemo);
      // splice(Where to fit the change value, Number to clear from array at that location, value, value,,,,)
      this.modalClicked = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  text-align: center;
  color: #2c3e50;
}
</style>
