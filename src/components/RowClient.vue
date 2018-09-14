<template>
  <tr :class="{ selected:client.selected }">
    <td class="center">
      <!-- eslint-disable-next-line -->
      <input type="checkbox" :id="'chkCustomer'+client.id" class="checkbox" v-model="client.selected">
      <label :for="'chkCustomer'+client.id" class="checkbox-label" @click="select()"></label>
    </td>
    <td>{{client.customer}}</td>
    <td>{{transactionDateFormat}}</td>
    <td>${{client.amount}}</td>
    <td>
      <span class="status" :class="{ paid:client.isPaid }"></span>
      {{client.isPaid ? 'Paid':'Unpaid'}}
    </td>
  </tr>
</template>

<script>
import moment from 'moment';

export default {
  props: ['client'],
  data() {
    return {
    };
  },
  computed: {
    transactionDateFormat() {
      return moment(this.client.transactionDate).format('MMM Do, YYYY');
    },
  },
  methods: {
    select() {
      this.client.selected = !this.client.selected;
      this.$emit('test');
    },
  },
};
</script>
