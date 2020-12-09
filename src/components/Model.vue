<template>
  <transition name="fade">
    <div click="cancel" v-if="price" class="basic-layer">
      <section class="modal">
        <h3>提示</h3>
        <p>確定花費{{ price }}元<br/>成為12個月的{{ title }}嗎?</p>
        <div class="button-group">
          <button class="cancel" @click="cancel">取消</button>
          <button class="submit" @click="submit">確定</button>
        </div>
      </section>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    title: String,
    price: String
  },
  methods: {
    cancel() {
      this.$emit('closeModal');
    },
    submit() {
      this.$emit('submit', this.title);
    }
  }

}
</script>

<style scoped>
.basic-layer {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #000000cc;
  z-index: 9;
}

.modal {
  background-color: #fff;
  width: 80%;
  max-width: 500px;
  height: 205px;
  margin: 200px auto 0;
  border-radius: 20px 20px 0px 80px;
  padding: 24px 32px;
}

h3 {
  font: bold 26px/30px Microsoft JhengHei;
  margin-bottom: 10px;
}

p {
  color: #998FA2;
  font: 14px/20px Microsoft JhengHei;
}

.button-group {
  text-align: right;
}

.button-group button {
  margin-top: 28px;
  border-radius: 80px;
  padding: 12px 31px;
  color: #fff;
}

.cancel {
  background-color: #9599B3;
  margin-right: 10px;
}
.submit {
  background-color:#8A56AC;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.8s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>