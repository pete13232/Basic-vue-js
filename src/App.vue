<template>
  <section>
    <img :src="picture" alt="pic" :width="size" :height="size" ref="imageEl" />
    <h1>ชื่อ-นามสกุล : {{ getFullName }}</h1>
    <h1>อายุ : {{ age }}</h1>
    <h1>เงินเดือน : {{ salary }} บาท</h1>
    <h1>รายได้ต่อปี : {{ getIncome }} บาท</h1>
    <h1>ตำแหน่งงาน : {{ getDepartment }}</h1>
    <button @click="addSalary(5000)">เพิ่มเงินเดือน</button>
    <button @click="toggleVisible">
      {{ isVisble ? "ซ่อน" : "แสดง" }}รายละเอียด
    </button>
    <article v-show="isVisble">
      <p>ที่อยู่ : <span v-html="address"></span></p>
      <p><a :href="social" target="_blank">Social</a></p>
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก :</p>
        <ul>
          <li v-for="(item, index) in hobby" :key="index">
            {{ index }}-{{ item }}
          </li>
        </ul>
      </div>
      <p>ข้อมูลพื้นฐาน</p>
      <ul>
        <li v-for="(item, key) in general" :key="key">
          {{ key }} : {{ item }}
        </li>
      </ul>
    </article>
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
      hobby: ["ทำสวน", "เล่นเกม", "ฟังเพลง", "ทำอาหาร", "เลี้ยงแมว"],
      general: {
        gender: "ชาย",
        weight: "70.4",
        height: "170",
        status: false,
      },
      isVisble: false,
      salary: 20000,
    };
  },
  methods: {
    toggleVisible() {
      this.isVisble = !this.isVisble;
    },
    addSalary(value) {
      this.salary += value;
    },
  },
  computed: {
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    getIncome() {
      return this.salary * 12;
    },
    getDepartment() {
      return this.salary >= 35000 ? "Project manager" : "Programmer";
    },
  },
  watch: {
    salary(value) {
      if (value > 50000) {
        alert("เงินเดือนไม่ควรเกิน 50,000 บาท");
        setTimeout(()=>{
          this.salary = 50000
        },100)
      }
    },
  },
};
</script>

<style>
</style>
