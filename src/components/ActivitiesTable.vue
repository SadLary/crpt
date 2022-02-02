<template>
  <div class="activities-table container">
    <div class="caption-row">
        <div class="caption-cell">Монета</div>
        <div class="caption-cell">Мастернод</div>
        <div class="caption-cell">Баланс</div>
        <div class="caption-cell">Депозит</div>
        <div class="caption-cell">Начисления</div>
        <div class="caption-cell">Курс</div>
        <div class="caption-cell">Накоплено</div>
    </div>
    <div v-for="active in activities" :key="active.id" class="data-row">
        <div class="data-cell">
            {{ active.currency }}
        </div>
        <div class="data-cell">{{ active.masterNode }}</div>
        <div class="data-cell">
            <p class="main-currency">{{ active.balance.current }} {{ active.currency }}</p>
            <p class="currency">{{ active.balance.BTC }} &#8383;</p>
            <p class="currency">{{ active.balance.US }} &#36;</p>
            <p class="currency">{{ active.balance.RUB }} &#8381;</p>
        </div>
        <div class="data-cell">
            <p>{{ active.deposit.old }}</p>
            <p>&rarr;{{ active.deposit.new }}</p>
            <p>{{ active.deposit.timeOldToNew }}</p>
        </div>
        <div class="data-cell">
            <p class="main-currency">{{ active.profit.current }} {{ active.currency }}</p>
            <p class="currency">{{ active.profit.BTC }} &#8383;</p>
            <p class="currency">{{ active.profit.US }} &#36;</p>
            <p class="currency">{{ active.profit.RUB }} &#8381;</p>
        </div>
        <div class="data-cell">
            <p class="main-currency">{{ active.sellingRate.current }}&#8383; <span>{{ active.sellingRate.persent }}</span></p>
        </div>
        <div class="data-cell">
            <p class="main-currency">{{ active.accumulated.current }} {{ active.currency }}</p>
            <p class="currency">{{ active.accumulated.BTC }} &#8383;</p>
            <p class="currency">{{ active.accumulated.US }} &#36;</p>
            <p class="currency">{{ active.accumulated.RUB }} &#8381;</p>
        </div>
    </div>
    <div class="final-row">
        <div class="caption-cell">Итог</div>
        <div class="caption-cell">{{ totalNodes }}</div>
        <div class="caption-cell">
            <p class="currency">{{ totalBalanceBTC }} &#8383;</p>
            <p class="currency">{{ totalBalanceUS }} &#36;</p>
            <p class="currency">{{ totalBalanceRub }} &#8381;</p>
        </div>
        <div class="caption-cell"></div>
        <div class="caption-cell">
            <p class="currency">{{ totalProfitBTC }} &#8383;</p>
            <p class="currency">{{ totalProfitUS }} &#36;</p>
            <p class="currency">{{ totalProfitRub }} &#8381;</p>
        </div>
        <div class="caption-cell"></div>
        <div class="caption-cell">
            <p class="currency">{{ totalAccumulatedBTC }} &#8383;</p>
            <p class="currency">{{ totalAccumulatedUS }} &#36;</p>
            <p class="currency">{{ totalAccumulatedRub }} &#8381;</p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ActivitiesTable',
  props: {
    activities: {
      type: Array,
      required: true
    }
  },
  data() {
      return {
          totalNodes: 0,
          totalBalanceCurr: 0,
          totalBalanceBTC: 0,
          totalBalanceUS: 0,
          totalBalanceRub: 0,
          totalAccumulatedCurr: 0,
          totalAccumulatedBTC: 0,
          totalAccumulatedUS: 0,
          totalAccumulatedRub: 0,
          totalProfitCurr: 0,
          totalProfitBTC: 0,
          totalProfitUS: 0,
          totalProfitRub: 0,
      }
  },
  mounted () {
    this.calcNodes();
    this.calcBalance();
    this.calcAccumulated();
    this.calcProfit();
  },
  methods: {
      calcNodes() {
          this.activities.forEach(item => {
              this.totalNodes += item.masterNode
          });
      },

      calcBalance() {
          this.activities.forEach(item => {
              this.totalBalanceCurr += Number(item.balance.current)
              this.totalBalanceBTC += Number(item.balance.BTC)
              this.totalBalanceUS += Number(item.balance.US)
              this.totalBalanceRub += Number(item.balance.RUB)
          });
      },
      calcAccumulated() {
          this.activities.forEach(item => {
              this.totalAccumulatedCurr += Number(item.accumulated.current)
              this.totalAccumulatedBTC += Number(item.accumulated.BTC)
              this.totalAccumulatedUS += Number(item.accumulated.US)
              this.totalAccumulatedRub += Number(item.accumulated.RUB)
          });
      },
      calcProfit() {
          this.activities.forEach(item => {
              this.totalProfitCurr += Number(item.profit.current)
              this.totalProfitBTC += Number(item.profit.BTC)
              this.totalProfitUS += Number(item.profit.US)
              this.totalProfitRub += Number(item.profit.RUB)
          });
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.activities-table {
    display: flex;
    flex-direction: column;
    width: 100%;
}
.caption-row, .data-row, .final-row {
    display: flex;
    width: 100%;
}
.caption-cell, .data-cell {
    width: 14%;
}

.caption-row, .final-row {
    box-sizing: border-box;
    background-color: darkgray;
    color: #fff;
    padding: 10px 0px;
}
.caption-cell {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 8px;
}
.data-row {
    box-sizing: border-box;
    border-left: 1px solid lightgray;
    border-right: 1px solid lightgray;
    border-bottom: 1px solid lightgray;
}
.data-cell {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 8px;
    border-right: 1px solid lightgray;
}
.data-cell:last-child {
    border-right: none;
}
.data-cell > p {
    margin: 0px 0px 5px 0px;
    font-size: 14px;
}
.main-currency {
    font-weight: bold;
    font-size: 16px;
    margin: 0px 0px 8px 0px;
}
.final-row > .caption-cell > p {
    margin: 0px 0px 5px 0px;
}
</style>
