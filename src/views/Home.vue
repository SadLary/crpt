<template>
  <div class="home">
    <UserInfo :user="userData.userInfo"/>
    <ActivitiesTable :activities="userData.activites"/>
  </div>
</template>

<script>
// @ is an alias to /src
import UserInfo from '@/components/UserInfo.vue'
import ActivitiesTable from '@/components/ActivitiesTable.vue'

export default {
  name: 'Home',
  components: {
    UserInfo,
    ActivitiesTable
  },
  data () {
    return {
      apiUrl: 'https://jsonplaceholder.typicode.com/users',
      userData: {
        userInfo: {
          userId: 4,
          ticker: 'ticker',
          addres: 'some addres',
          name: 'John Doe',
          flag: 'error',
          balance: '2000',
          lastPaymentDate: '25.03.2077',
        },
        activites: [
          {
            currency: 'AZU',
            masterNode: 1,
            balance: {
              current: '1002',
              BTC: '0.000004',
              US: '3000',
              RUB: '300000'
            },
            deposit: {
              old: '70000',
              new: '100000',
              timeOldToNew: '42д 14ч 7мин'
            },
            profit: {
              current: '10',
              BTC: '0.000002',
              US: '30',
              RUB: '3000'
            },
            sellingRate: {
              current: '0.000004',
              persent: '-6.5%'
            },
            accumulated: {
              current: '11',
              BTC: '0.000003',
              US: '32',
              RUB: '3040'
            }
          },
          {
            currency: 'PNY',
            masterNode: 1,
            balance: {
              current: '1002',
              BTC: '0.000004',
              US: '3000',
              RUB: '300000'
            },
            deposit: {
              old: '70000',
              new: '100000',
              timeOldToNew: '42д 14ч 7мин'
            },
            profit: {
              current: '10',
              BTC: '0.000002',
              US: '30',
              RUB: '3000'
            },
            sellingRate: {
              current: '0.000004',
              persent: '-6.5%'
            },
            accumulated: {
              current: '11',
              BTC: '0.000003',
              US: '32',
              RUB: '3040'
            }
          },
          {
            currency: 'SAGA',
            masterNode: 1,
            balance: {
              current: '1002',
              BTC: '0.000004',
              US: '3000',
              RUB: '300000'
            },
            deposit: {
              old: '70000',
              new: '100000',
              timeOldToNew: '42д 14ч 7мин'
            },
            profit: {
              current: '10',
              BTC: '0.000002',
              US: '30',
              RUB: '3000'
            },
            sellingRate: {
              current: '0.000004',
              persent: '-6.5%'
            },
            accumulated: {
              current: '11',
              BTC: '0.000003',
              US: '32',
              RUB: '3040'
            }
          }
        ]
      }
    }
  },
  created () {
    this.fetchUserData();
  },
  methods: {

    fetchUserData () {
      fetch(this.apiUrl)
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        console.log(data);
      });
    }
  }
}
</script>
