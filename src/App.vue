<template>
  <section>
    <img :src="picture" alt="pic" :width="size" :height="size" ref="imageEl" />
    <form @submit.prevent="submitForm">
      <label>ป้อนชื่อเล่น:</label>
      <input type="text" ref="nickNameEl" />
      <button type="submit">บันทึก</button>
    </form>
    <h1>ชื่อ-นามสกุล : {{ getFullName() }}</h1>
    <h1>ชื่อเล่น : {{ nickName }}</h1>
    <h1>อายุ : {{ age }}</h1>
    <p>ที่อยู่ : <span v-html="address"></span></p>
    <p><a :href="social" target="_blank">Social</a></p>
    <p>งานอดิเรก</p>
    <ul>
      <li>{{ hobby[0] }}</li>
      <li>{{ hobby[1] }}</li>
      <li>{{ hobby[2] }}</li>
    </ul>
    <p>ข้อมูลพื้นฐาน</p>
    <ul>
      <li>เพศ: {{ general.gender }}</li>
      <li>น้ำหนัก: {{ general.weight }} กิลโลกรัม</li>
      <li>ความสูง: {{ general.height }} cm.</li>
      <li>โรคประจำตัว: {{ general.status }}</li>
    </ul>
    <button @click="showData()">คลิกเพื่อดูข้อมูล</button>
    <button @click.ctrl="increment(10)">เพิ่ม</button>
    <button @click.middle="decrement(5)">ลด</button>
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "KongRuksiam",
      lastName: "Studio",
      nickName: "",
      age: 15,
      address: "<i>กรุงเทพมหานคร</i>",
      picture:
        "https://as2.ftcdn.net/v2/jpg/02/29/75/83/1000_F_229758328_7x8jwCwjtBMmC6rgFzLFhZoEpLobB6L8.jpg",
      size: 50,
      social: "https://www.facebook.com/kongruksiamtutorial",
      hobby: ["ทำสวน", "เล่นเกม", "ฟังเพลง"],
      general: {
        gender: "ชาย",
        weight: "70.4",
        height: "170",
        status: false,
      },
    };
  },
  methods: {
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    showData() {
      alert(this.firstName);
    },
    increment(value) {
      this.age += value;
    },
    decrement(value) {
      this.age -= value;
    },
    submitForm() {
      this.nickName = this.$refs.nickNameEl.value;
    },
  },
};
</script>

<style>
</style>
