<template>
  <div>
    <b-button variant="outline-primary" class="mr-2" @click="sortByPrice">เรียงตามราคา</b-button>
    <b-button variant="outline-primary" @click="sortByRemain">เรียงตามจำนวนคงเหลือ</b-button>
    <h1 class="mt-4">{{msg === '' ? 'เริ่มต้น': msg}}</h1>
    <div>
      <b-table :fields="fields" striped hover :items="data"></b-table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async mounted() {
    const { data } = await axios.get("http://localhost:3002");
    this.data = data.result;
  },
  data: () => ({
    data: [],
    fields: [
      { key: "id", label: "ลำดับที่" },
      { key: "code", label: "รหัสสินค้า" },
      { key: "name", label: "ชื่อ" },
      { key: "price", label: "ราคา(บาท)" },
      { key: "remain", label: "จำนวนคงเหลือ(ชิ้น )" }
    ],
    msg: ""
  }),
  methods: {
    async sortByPrice() {
      this.msg = "เรียงตามราคา";
      this.data.sort((a, b) => a.price - b.price);
    },
    async sortByRemain() {
      this.msg = "เรียงตามจำนวนคงเหลือ";
      this.data.sort((a, b) => a.remain - b.remain);
    }
  }
};
</script>

<style>
</style>
