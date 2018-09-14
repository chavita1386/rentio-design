<template>
  <div class="modal" @keyup.esc="modalClick()">
    <div class="modal-wrapper">
      <h4 class="modal__title">Add new customer</h4>
      <table class="table-modal" @keyup.enter="add()">
        <tbody>
          <tr>
            <td colspan="2">
              <!-- eslint-disable-next-line -->
              <input type="text" id="txtCustomer" class="input" placeholder="Customer" v-model.trim="client.customer" ref="customer" required tabindex="1">
            </td>
          </tr>
          <tr>
            <td colspan="2">
              <!-- eslint-disable-next-line -->
              <input type="date" id="txtTransactionDate" class="input" placeholder="Transaction date" v-model.trim="client.transactionDate" required tabindex="2">
            </td>
          </tr>
          <tr>
            <td colspan="2">
              <!-- eslint-disable-next-line -->
              <input type="number" id="txtAmount" class="input" placeholder="Amount" min="1" v-model.number="client.amount" required tabindex="3">
            </td>
          </tr>
          <tr>
            <td colspan="2">
              <!-- eslint-disable-next-line -->
              <input type="checkbox" id="chkStatus" class="checkbox" v-model="client.isPaid">
              <!-- eslint-disable-next-line -->
              <label for="chkStatus" tabindex="4" @keyup.space="client.isPaid = !client.isPaid"></label>
              <span class="label">Paid</span>
            </td>
          </tr>
          <tr>
            <td class="center">
              <!-- eslint-disable-next-line -->
              <button class="button button--primary" type="button" @click="add()" tabindex="5">Accept</button>
            </td>
            <td>
              <button class="button" @click="closeModal()" tabindex="6">Cancel</button>
            </td>
          </tr>
          <tr>
            <td colspan="2" class="center">Press ESC to cancel</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="modal-errors" :class="{active:errors.length > 0}">
      <p v-for="(error,index) in errors" :key="index">
        {{error}}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.$refs.customer.focus();
  },
  data() {
    return {
      errors: [],
      client: {
        id: 0,
        customer: '',
        transactionDate: '',
        amount: 0,
        isPaid: false,
        selected: false,
      },
    };
  },
  methods: {
    add() {
      if (this.client.transactionDate.trim() !== '' && this.client.customer.trim() !== '' && this.client.amount > 1) {
        this.$emit('add-customer', this.client);
      }

      this.errors = [];

      if (this.client.customer.trim() === '') {
        this.errors.push('Customer is required');
      }

      if (this.client.transactionDate.trim() === '') {
        this.errors.push('Transaction Date is required');
      }

      if (this.client.amount < 1) {
        this.errors.push('The amount has to be greater than five');
      }
    },
    closeModal() {
      this.errors = [];
      // this.$emit('close-modal');
    },
    modalClick() {
      this.$emit('close-modal');
    },
  },
};
</script>
