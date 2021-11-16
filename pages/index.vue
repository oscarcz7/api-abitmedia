<template>
  <div class="p-8 mx-20 rounded sm:p-3">
    <div class="mt-5 md:mt-0 md:col-span-2">
      <form @submit.prevent="payment">
        <div class="overflow-hidden transition duration-200 ease-in shadow rounded-3xl">
          <div class="px-4 py-5 bg-white dark:bg-gray-700 sm:p-6">
            <div class="p-3 m-3 text-center">
              <p class="text-2xl font-bold text-gray-800 dark:text-gray-100">
                CREAR NUEVA SOLICITUD DE PAGO
              </p>
            </div>
            <div class="grid grid-cols-6 gap-6">
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="companyType"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Tipo Empresa</label
                >
                <select
                  id="companyType"
                  name="companyType"
                  v-model="paymentCreate.companyType"
                  class="block w-full px-3 py-2 mt-1 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                >
                  <option
                    v-for="(item, company) in companies"
                    :key="company"
                    v-bind:value="item.value"
                  >
                    {{ item.text }}
                  </option>
                </select>
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="name"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Tipo Documento</label
                >
                <select
                  id="documentType"
                  name="documentType"
                  v-model="paymentCreate.documentType"
                  class="block w-full px-3 py-2 mt-1 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                >
                  <option
                    v-for="(item, documentType) in documentTypes"
                    :key="documentType"
                    v-bind:value="item.value"
                  >
                    {{ item.text }}
                  </option>
                </select>
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="document"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Identificaion</label
                >
                <input
                  type="number"
                  name="document"
                  v-model="paymentCreate.document"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="fullName"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Nombre</label
                >
                <input
                  type="text"
                  name="fullName"
                  v-model="paymentCreate.fullName"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="address"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Direccion</label
                >
                <input
                  type="text"
                  name="address"
                  v-model="paymentCreate.address"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="mobile"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Telf</label
                >
                <input
                  type="tel"
                  name="mobile"
                  v-model="paymentCreate.mobile"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="email"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Email</label
                >

                <input
                  type="email"
                  name="email"
                  v-model="paymentCreate.email"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="reference"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Referencia</label
                >

                <input
                  type="text"
                  name="reference"
                  v-model="paymentCreate.reference"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="description"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Descripcion</label
                >
                <input
                  type="text"
                  name="description"
                  v-model="paymentCreate.description"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="amount"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Monto</label
                >
                <input
                  type="number"
                  step="0.01"
                  name="amount"
                  v-model="paymentCreate.amount"
                  value="1.12"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="amountWithTax"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Monto Con Tax</label
                >
                <input
                  type="number"
                  step="0.01"
                  name="amountWithTax"
                  v-model="paymentCreate.amountWithTax"
                  value="0.5"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="amountWithoutTax"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Monto Sin Tax</label
                >

                <input
                  type="number"
                  step="0.01"
                  name="amountWithoutTax"
                  v-model="paymentCreate.amountWithoutTax"
                  value="0.5"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="tax"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Tax</label
                >
                <input
                  type="number"
                  step="0.01"
                  name="tax"
                  v-model="paymentCreate.tax"
                  value="0.12"
                  class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                />
              </div>
              <div class="col-span-6 sm:col-span-3">
                <label
                  for="name"
                  class="block text-lg font-medium text-gray-700 dark:text-gray-200"
                  >Pasarela de pago</label
                >
                <select
                  id="gateway"
                  name="gateway"
                  v-model="paymentCreate.gateway"
                  class="block w-full px-3 py-2 mt-1 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                >
                  <option
                    v-for="(item, gateway) in gateways"
                    :key="gateway"
                    v-bind:value="item.value"
                  >
                    {{ item.text }}
                  </option>
                </select>
              </div>
            </div>
            <Notification class="mt-2" :message="message" :type="typeM" v-if="message" />
          </div>
          <div class="px-4 py-3 text-right bg-gray-200 sm:px-6 dark:bg-gray-600">
            <button
              type="submit"
              class="inline-flex justify-center px-5 py-3 text-sm font-medium text-white bg-blue-600 border border-transparent rounded-md shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
            >
              CREAR
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "",
      typeM: "",
      paymentCreate: {
        companyType: "",
        document: "",
        documentType: "",
        fullName: "",
        address: "",
        mobile: "",
        email: "",
        reference: "",
        description: "",
        amount: 0,
        amountWithTax: 0,
        amountWithoutTax: 0,
        tax: 0,
        gateway: 0,
      },

      companies: [
        { text: "Persona Natural", value: "Persona Natural" },
        { text: "Empresa", value: "Empresa" },
      ],
      documentTypes: [
        { text: "Cédula de identidad", value: "01" },
        { text: "RUC, Pasaporte", value: "02" },
        { text: "ID del exterior", value: "03" },
      ],
      gateways: [
        { value: 1, text: "Alignet" },
        { value: 2, text: "Payphone" },
        { value: 3, text: "Datafast" },
        { value: 4, text: "Paymentez" },
      ],
    };
  },
  methods: {
    async payment() {
      try {
        let payment = await this.$axios.$post(
          "api/create-payment-request?access-token=2y-13-tx-zsjtggeehkmygjbtsf-51z5-armmnw-ihbuspjufwubv4vxok6ery7wozao3wmggnxjgyg",
          this.paymentCreate,
          {
            headers: { "Content-Type": "application/x-www-form-urlencoded" },
            progress: false,
          }
        );
        console.log(payment);
        console.log(this.paymentCreate);
        if (payment.status === 200) {
          this.message = payment.message + " " + payment.data.url;
          this.typeM = "success";
        } else {
          this.message = payment;
          this.typeM = "danger";
        }
      } catch (e) {
        this.message = e.message;
        this.typeM = "danger";
      }
    },
  },
};
</script>
