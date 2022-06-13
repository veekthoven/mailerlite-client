<template>
  <div class="py-6">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-8">
      <!-- Replace with your content -->
      <!-- This example requires Tailwind CSS v2.0+ -->
      <div class="px-4 sm:px-6 lg:px-8">
        <div class="sm:flex sm:items-center">
          <div class="sm:flex-auto">
            <h1 class="text-2xl font-semibold text-gray-900">Subscribers</h1>
            <p class="mt-2 text-sm text-gray-700">A list of all your subscribers</p>
          </div>
          <div class="mt-4 sm:mt-0 sm:ml-16 sm:flex-none">
            <nuxt-link to="/subscribers/create" type="button" class="inline-flex items-center justify-center rounded-md border border-transparent bg-primary px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 sm:w-auto">Add Subscriber +</nuxt-link>
          </div>
        </div>
        <hr class="mt-4">
        <div class="mt-8 flex flex-col" v-if="subscribers.length">
          <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
              <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
                <datatable :columns="columns" :data="rows"></datatable>
              </div>
            </div>
          </div>
        </div>
        <div v-else class="mt-5 text-gray-500">
          There are no subscribers.
        </div>
      </div>

      <!-- /End replace -->
    </div>
  </div>
</template>

<script>
export default {
  layout: 'default',
  name: 'home',
  async asyncData({ $axios }) {
    const response = await $axios.$get('/subscribers')
    return { 
      subscribers: response.subscribers
    }
  },
  data() {
    return {
      columns: [],
      rows: []
    }
  },
  created() {
    if (this.subscribers.length) {
      this.prepareColumns();

      this.prepareRows()
    }
  },
  methods: {
    prepareColumns() {
      delete this.subscribers[0].id
      delete this.subscribers[0].updated_at
      delete this.subscribers[0].created_at
      
      Object.keys(this.subscribers[0]).forEach(attr => {
        if (attr !== 'fields') {
          this.columns.push({
            label: attr.toLowerCase().replace(/ /g,'_').replace(/[^\w-]+/g,''),
            field: attr
          }) 
        }
      })

      this.subscribers[0].fields.forEach(field => {
        this.columns.push({
          label: field.key.toLowerCase().replace(/ /g,'_').replace(/[^\w-]+/g,''),
          field: field.key
        })
      })
    },
    prepareRows() {
      this.subscribers.forEach(subscriber => {
        let row = {
          name: subscriber.name,
          email: subscriber.email,
          state: subscriber.state,
        };

        subscriber.fields.forEach(field => {
          row[field.key] = field.value
        })

        this.rows.push(row)
      })
    }
  }
}
</script>
