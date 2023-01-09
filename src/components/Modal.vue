<template lang="">
  <div v-if="modalClicked">
    <div class="w-full h-full bg-slate-700">
      <div class="flex justify-center pt-[100px] items-center">
        <div class="w-[500px] h-[500px] bg-white rounded-md">
          <div class="bg-blue-300 flex justify-end text-gray-200"><button class="p-3 hover:text-white" @click="() => $emit('modalX')">X</button></div>

          <div class="justify-center items-center flex pt-10">{{ datas[getNumber] }}</div>
          <div class="flex mt-10 items-center px-4">
            <span class="absolute text-lg pl-3">Write:</span>
            <input placeholder="Write your memo." class="border py-7 px-20 mr-5 w-full rounded-md shadow-sm text-lg" v-model="modifiedMeMo" type="text" />
            <button class="bg-blue-400 text-white w-32 shadow-sm rounded-md hover:bg-blue-500 py-7" @click="() => $emit('modifyaMemo', modifiedMeMo)">Click</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "ModalBoard",
  props: { datas: Array, modalClicked: Boolean, getNumber: Number },
  data() {
    {
      return {
        modifiedMeMo: "",
      };
    }
  },
};
</script>
<style lang=""></style>
