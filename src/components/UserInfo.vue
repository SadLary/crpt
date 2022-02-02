<template>
  <div class="user-info container">
    <div>
      <p>Имя: <span>{{ user.name }}</span></p>
      <p>Адрес: <span>{{ user.addres }}</span></p>
      <p>Статус: <span :class="user.flag">{{ status }}</span></p>
    </div>
    <div>
      <p>Тикер: <span>{{ user.ticker }}</span></p>
      <p>Баланс: <span>{{ user.balance }}</span> р</p>
      <p>Дата последнего пополнения: <span>{{ user.lastPaymentDate }}</span></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserInfo',
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      status: ''
    }
  },
  mounted () {
    this.getRuStatus();
  },
  methods: {
    getRuStatus () {
      switch (this.user.flag) {
        case 'active':
          this.status = 'АКТИВЕН'
          break;
          case 'starting':
          this.status = 'СТАРТ'
          break;
          case 'error':
          this.status = 'ОШИБКА'
          break;
      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.user-info {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  border: 1px solid darkgray;
  border-radius: 12px;
  padding: 10px 20px;
}

.user-info > div {
  width: 48%;
}

.active {
  color: #02f302;
}

.starting {
  color: #fbfb00;
}

.error {
  color: #f11c1c;
}
</style>
