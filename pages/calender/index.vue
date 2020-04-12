<template>
  <div class="root">
    <div class="form-container">
      <form>
        <input id="year" class="data-input" />年
        <input id="month" class="data-input" />月
        <input id="date" class="data-input" />日
        <input id="show" type="button" value="表示" />
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
      </table>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({})
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
</style>
