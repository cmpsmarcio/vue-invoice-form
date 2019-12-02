<template>
  <div class="invoice-box">
    <table cellpadding="0" cellspacing="0">
      <tr class="top">
        <td colspan="4">
          <table>
            <tr>
              <td class="title">
                <img
                  src="https://www.sparksuite.com/images/logo.png"
                  style="width:100%; max-width:300px;"
                />
              </td>

              <td>
                Invoice #: 123
                <br />Created: January 1, 2015
                <br />Due: February 1, 2015
              </td>
            </tr>
          </table>
        </td>
      </tr>

      <tr class="information">
        <td colspan="4">
          <table>
            <tr>
              <td>
                Sparksuite, Inc.
                <br />12345 Sunny Road
                <br />Sunnyville, CA 12345
              </td>

              <td>
                Acme Corp.
                <br />John Doe
                <br />john@example.com
              </td>
            </tr>
          </table>
        </td>
      </tr>

      <tr class="heading">
        <td colspan="2">Payment Method</td>
        <td colspan="2">Check #</td>
      </tr>

      <tr class="details">
        <td colspan="2">Check</td>
        <td colspan="2">1000</td>
      </tr>

      <tr class="heading">
        <td>Item</td>
        <td>quantity</td>
        <td>Price</td>
        <td>total</td>
      </tr>

      <tr class="item" v-for="item in items" :key="item.id">
        <td>
          <input v-model="item.description" />
        </td>

        <td>
          $
          <input type="number" v-model="item.price" />
        </td>

        <td>
          <input type="number" v-model="item.quantity" />
        </td>
        <td>$ {{item.price * item.quantity | currency}}</td>
      </tr>

      <tr class="total">
        <td colspan="2"></td>

        <td colspan="2">Total: $385.00</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "InvoiceForm",
  data() {
    return {
      items: [{ id: 1, description: "Website Design", quantity: 1, price: 300 }]
    };
  },
  computed: {
    total() {
      return this.items.reduce(
        (acc, item) => acc + item.price * item.quantity,
        0
      );
    }
  },
  methods: {
    addRow() {
      this.items.push({
        description: "",
        quantity: 1,
        price: 0
      });
    },
    filters: {
      currency(value) {
        return value.toFixed(2);
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.invoice-box {
  max-width: 800px;
  margin: auto;
  padding: 30px;
  border: 1px solid #eee;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
  font-size: 16px;
  line-height: 24px;
  font-family: "Helvetica Neue", "Helvetica", Helvetica, Arial, sans-serif;
  color: #555;
}

.invoice-box table {
  width: 100%;
  line-height: inherit;
  text-align: left;
}

.invoice-box table td {
  padding: 5px;
  vertical-align: top;
}

.invoice-box table tr td:nth-child(2) {
  text-align: right;
}

.invoice-box table tr.top table td {
  padding-bottom: 20px;
}

.invoice-box table tr.top table td.title {
  font-size: 45px;
  line-height: 45px;
  color: #333;
}

.invoice-box table tr.information table td {
  padding-bottom: 40px;
}

.invoice-box table tr.heading td {
  background: #eee;
  border-bottom: 1px solid #ddd;
  font-weight: bold;
}

.invoice-box table tr.details td {
  padding-bottom: 20px;
}

.invoice-box table tr.item td {
  border-bottom: 1px solid #eee;
}

.invoice-box table tr.item.last td {
  border-bottom: none;
}

.invoice-box table tr.total td:nth-child(2) {
  border-top: 2px solid #eee;
  font-weight: bold;
}

@media only screen and (max-width: 600px) {
  .invoice-box table tr.top table td {
    width: 100%;
    display: block;
    text-align: center;
  }

  .invoice-box table tr.information table td {
    width: 100%;
    display: block;
    text-align: center;
  }
}

/** RTL **/
.rtl {
  direction: rtl;
  font-family: Tahoma, "Helvetica Neue", "Helvetica", Helvetica, Arial,
    sans-serif;
}

.rtl table {
  text-align: right;
}

.rtl table tr td:nth-child(2) {
  text-align: left;
}
</style>
