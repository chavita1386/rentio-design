<template>
  <div>
    <!-- :class="{ 'modal-bg':modalCustomer }" -->
    <!-- eslint-disable-next-line -->
    <client-modal v-if="modalCustomer" @add-customer="addCustomer" @close-modal="modalCustomer = false"></client-modal>
    <div class="toolbar">
      <div>
        <i class="fas fa-search icon--search"></i>
        <input type="text" class="toolbar__search" name="search" id="search" placeholder="Search">
      </div>
      <button class="button button--primary" @click="modalCustomer = true">Add New Customer</button>
    </div>
    <div class="filterbar">
      <h2 class="title">Clients
        <span class="info-clients">1,800 Total</span>
      </h2>
      <div class="filter-content">
        <button class="button button--filter button--left selected">Today</button>
        <button class="button button--filter button--center">Week</button>
        <button class="button button--filter button--right">Month</button>
      </div>
      <select name="sortBy" id="sortBy" class="button-check" v-model="sortBy">
        <option value="0" selected>Sort by</option>
        <option value="1">Paid</option>
        <option value="2">Unpaid</option>
      </select>
    </div>
    <div class="content">
      <table class="table" border="0">
        <thead>
          <tr>
            <th>
              <!-- eslint-disable-next-line -->
              <input type="checkbox" name="chkSelectAll" id="chkSelectAll" @click="selectAll()" class="checkbox" v-model="isSelectedAll">
              <label for="chkSelectAll" class="label"></label>
            </th>
            <th>Customer</th>
            <th>Transaction date</th>
            <th>Amount</th>
            <th>Status</th>
          </tr>
        </thead>
        <tbody>
          <!-- eslint-disable-next-line -->
          <row-client v-for="client in showClients" :key="client.id" :client="client" @test="test()"></row-client>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import RowClient from '../components/RowClient.vue';
import ClientModal from '../components/ClientModal.vue';

export default {
  components: { RowClient, ClientModal },
  data() {
    return {
      isSelectedAll: false,
      modalCustomer: false,
      sortBy: '0',
      Clients:
      [
        {
          id: 1,
          customer: 'Salvador Rocha',
          transactionDate: '10/23/2016',
          amount: 24.450,
          isPaid: false,
          selected: false,
        },
        {
          id: 2,
          customer: 'Pedrito Gutierrez',
          transactionDate: '08/14/2003',
          amount: 450124.450,
          isPaid: true,
          selected: false,
        },
        {
          id: 3,
          customer: 'Karla Perez',
          transactionDate: '01/20/2011',
          amount: 350690.450,
          isPaid: false,
          selected: false,
        },
      ],
    };
  },
  computed: {
    showClients() {
      if (this.sortBy === '0') {
        return this.Clients;
      }
      const sort = this.sortBy === '1';
      return this.Clients.filter(client => client.isPaid === sort);
    },
  },
  methods: {
    selectAll() {
      this.isSelectedAll = !this.isSelectedAll;
      this.Clients.forEach((clients) => {
      // eslint-disable-next-line
        clients.selected = this.isSelectedAll;
      });
    },
    test() {
      if (this.isSelectedAll === true) {
        this.isSelectedAll = false;
      }
    },
    addCustomer(client) {
      const autoID = (Math.floor(Math.random() * (99999 + 1)) + this.Clients.length);
      // eslint-disable-next-line
      client.id = autoID;
      this.Clients.push(client);
      this.modalCustomer = false;
    },
  },
};
</script>
