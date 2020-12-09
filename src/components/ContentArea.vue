<template>
  <div class="content">
    <header>
      <div class="selected-member" :style='{ backgroundImage: "url(" + selected.backgroundImg + ")", }'>
        <img src="@/assets/images/big-normal-member.svg" alt="">
        <h3>{{ selected.title }}</h3>
        <p>{{ selected.info[0] }}</p>
        <p class="deadline">{{ selected.deadline }}</p>
        <img class="icon" :src="selected.icon" alt="">
      </div>
    </header>
    <ul class="member-list">
      <div class="list-layer" v-for="item in options" :key="item.title" >
        <li @click="showButton(item.title)" class="member-card" :style='{ backgroundImage: "url(" + item.backgroundImg + ")", }'>
          <div>
            <h3>{{ item.title }}</h3>
            <p v-for="(paragragh, index) in item.info" :key="index">{{ paragragh }}</p>
            <img :src="item.icon" alt="">
          </div>
          <div>
            <div class="price" :class="{ 'price-up': item.title === buttonShowTitle }">&yen;{{ item.price }}</div>
            <button class="submit" v-if="item.title === buttonShowTitle" @click="select(item.title, item.price)">立即加入</button>
          </div>
        </li>
      </div>
    </ul>
    <button class="service"><img src="@/assets/images/server.svg" alt=""></button>
    <Modal
      :price="price"
      :title="title"
      @closeModal="closeModal"
      @submit="submit"
    ></Modal>
  </div>
</template>

<script>
import Modal from './Model.vue';

import normalMemberImg from '@/assets/images/member-04.png';
import silverMemberImg from '@/assets/images/member-06.png';
import goldenMemberImg from '@/assets/images/member-02.png';
import platinumMemberImg from '@/assets/images/member-03.png';
import diamondMemberImg from '@/assets/images/member-01.png';
import gloryMemberImg from '@/assets/images/member-05.png';
import honorMemberImg from '@/assets/images/member-07.png';

import normalIcon from '@/assets/images/mon50.svg';
import silverIcon from '@/assets/images/mon47.svg';
import goldenIcon from '@/assets/images/mon36.svg';
import platinumIcon from '@/assets/images/mon42.svg';
import diamondIcon from '@/assets/images/mon33.svg';
import gloryIcon from '@/assets/images/mon40.svg';
import honorIcon from '@/assets/images/mon44.svg';

export default {
  name: 'contentArea',
  components: {
    Modal
  },
  data() {
    return {
      selectedTitle: '普通会员',
      buttonShowTitle: '',
      price: '',
      title: '',
      memberList: [
        {
          title: '普通会员',
          info: ['每日可领取3次任务'],
          price: '330.00',
          deadline: '2020.08.11止',
          bottonIsShow: false,
          backgroundImg: normalMemberImg,
          icon: normalIcon
        },
        {
          title: '白银会员',
          info: ['每日可领取10次任务', '[1.20元/条]'],
          price: '330.00',
          deadline: '2020.08.30止',
          bottonIsShow: false,
          backgroundImg: silverMemberImg,
          icon: silverIcon
        },
        {
          title: '黄金会员',
          info: ['每日可领取19次任务'],
          price: '330.00',
          deadline: '2020.08.24止',
          bottonIsShow: false,
          backgroundImg: goldenMemberImg,
          icon: goldenIcon
        },
        {
          title: '铂金会员',
          info: ['每日可领取28次任务'],
          price: '330.00',
          deadline: '2020.08.18止',
          bottonIsShow: false,
          backgroundImg: platinumMemberImg,
          icon: platinumIcon
        },
        {
          title: '钻石会员',
          info: ['每日可领取99次任务'],
          price: '330.00',
          deadline: '2020.08.18止',
          bottonIsShow: false,
          backgroundImg: diamondMemberImg,
          icon: diamondIcon
        },
        {
          title: '荣耀会员',
          info: ['每日可领取228次任务'],
          price: '330.00',
          deadline: '2020.08.18止',
          bottonIsShow: false,
          backgroundImg: gloryMemberImg,
          icon: gloryIcon
        },
        {
          title: '尊耀会员',
          info: ['每日可领取338次任务'],
          price: '330.00',
          deadline: '2020.08.18止',
          bottonIsShow: false,
          backgroundImg: honorMemberImg,
          icon: honorIcon
        }
      ]
    }
  },
  methods: {
    showButton(title) {
      if (this.buttonShowTitle === title) {
        this.buttonShowTitle = '';
        return;
      }
      this.buttonShowTitle = title;
    },
    select(title, price) {
      this.price = price;
      this.title = title;
    },
    closeModal(payload) {
      this.price = '';
      this.title = '';
    },
    submit(title) {
      this.selectedTitle = title;
      this.price = '';
      this.title = '';
    }
  },
  computed: {
    selected() {
      return this.memberList.find(item => item.title === this.selectedTitle);
    },
    options() {
      return this.memberList
      .filter(item => item.title !== this.selectedTitle)
    }
  }
}
</script>

<style scoped>
.content {
  position: relative;
  height: 84vh;
  overflow: scroll;
  background-color: #352641;
  padding-bottom: 100px;
}

.selected-member {
  background-color: #8A56AC;
  padding: 16px 0 24px 0;
  border-radius: 0 0 0 70px;
  color: #FFFFFF;
  text-align: center;
  background-size: cover;
  position: relative;
}

.selected-member img {
  margin-bottom: 10px;
}

.selected-member .icon {
  position: absolute;
  top: 65px;
  left: 25px;
  /* transform: translateX(-20px); */
}

.selected-member h3 {
  font: bold 26px/24px Microsoft JhengHei;
  margin-bottom: 10px;
}

.selected-member p {
  color: #ffffff88;
  font: 14px/22px Microsoft YaHei;
}

.member-card {
  display: flex;
  justify-content: space-between;
  color: #FFFFFF88;
  padding: 24px 0;
  border-radius: 0 0 0 70px;
  background-size: cover;
}

.list-layer:nth-child(even) {
  background-color:  #352641;
}

.list-layer:nth-child(even) .member-card {
  background-color: #1d1524;
  
}

.list-layer:nth-child(odd) {
  background-color: #1d1524;
}

.list-layer:nth-child(odd) .member-card {
  background-color: #352641;
}

.member-card {
  position: relative;
  overflow: hidden;
}

.member-card h3 {
  font: bold 26px/24px Microsoft JhengHei;
  margin-bottom: 6px;
}

.member-card p {
  font: 14px/22px Microsoft JhengHei;
}

.member-card .price {
  margin-top: 24px;
  font: bold 20px/44px Arial;
  width: 100px;
}

.member-card > div:first-child {
  padding-left: 56px;
}

.member-card > div:last-child {
  padding-right: 30px;
  text-align: center;
}

.member-card img {
  position: absolute;
  top: -5px;
  left: 25px;
}

.price-up {
  margin-top: -10px;
}

.submit {
  border-radius: 30px;
  padding: 10px 20px;
  color: #8A56AC;
  font-size: 16px;
}

.service {
  position: fixed;
  width: 52px;
  height: 52px;
  border-radius: 999999px;
  background-color: #8A56AC;
  z-index: 99;
  bottom: 100px;
  right: 16px;
  box-shadow: 0px 2px 4px #00000066;
}
</style>