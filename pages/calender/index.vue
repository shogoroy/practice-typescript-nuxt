<template>
  <div class="root">
    <div class="form-container">
      <form>
        <input id="year" v-model.number="year" class="data-input" />年
        <input id="month" v-model.number="month" class="data-input" />月
        <input id="date" v-model.number="date" class="data-input" />日
      </form>
    </div>
    <div>
      <table>
        <tr>
          <th>
            日
          </th>
          <th>
            月
          </th>
          <th>
            火
          </th>
          <th>
            水
          </th>
          <th>
            木
          </th>
          <th>
            金
          </th>
          <th>
            土
          </th>
        </tr>
        <tr v-for="week of weeks" :key="week.id">
          <td
            v-for="d of week.dates"
            :key="d"
            :class="{ targetDate: d === date }"
          >
            {{ d }}
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import moment from 'moment'

const today = moment()

export default Vue.extend({
  data: () => ({
    year: today.year(),
    month: today.month() + 1,
    date: today.date()
  }),
  computed: {
    weeks() {
      const targetMoment = moment([this.year, this.month, this.date])

      const endDate = targetMoment.endOf('month').date()
      let day = targetMoment.startOf('month').day()

      const weeks = []
      if (!isNaN(endDate) && !isNaN(day)) {
        let week = {
          id: 1,
          startDay: day,
          dates: new Array(day).fill(undefined)
        }

        for (let date = 1; date <= endDate; date++) {
          week.dates.push(date)
          day++

          if (day % 7 === 0) {
            weeks.push(week)
            day = 0
            week = {
              id: date + 1,
              startDay: 0,
              dates: []
            }
          }
        }
        weeks.push(week)
      }

      return weeks
    }
  }
})
</script>

<style scoped>
.root {
  background-color: #ffffff;
  color: #000;
  padding: 50px;
}

.form-container {
  margin-bottom: 50px;
}

input {
  border: solid 1px #000;
  margin: 0 10px;
}

th {
  height: 50px;
  width: 50px;
  border-radius: 25px;
  background-color: #303f9f;
  color: #ffffff;
}
td {
  height: 50px;
  width: 50px;
  border-radius: 25px;
  background-color: #ffffff;
  color: #000000;
  text-align: center;
}

td.targetDate {
  background-color: #303f9f;
  color: #ffffff;
}
</style>
