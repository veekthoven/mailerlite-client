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
            <nuxt-link to="/fields/create" type="button" class="inline-flex items-center justify-center rounded-md border border-transparent bg-primary px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 sm:w-auto">Add Field +</nuxt-link>
          </div>
        </div>
        <hr class="mt-4">
        <div class="mt-8 flex flex-col" v-if="fields.length">
          <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
              <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
                <datatable :columns="columns" :data="fields"></datatable>
              </div>
            </div>
          </div>
        </div>
        <div v-else class="mt-5 text-gray-500">
          There are no fields.
        </div>
      </div>

      <!-- /End replace -->
    </div>
  </div>
</template>

<script>
export default {
  layout: 'default',
  name: 'fields',
  async asyncData({ $axios }) {
    const response = await $axios.$get('/fields')
    return { 
      fields: response.fields
    }
  },
  data() {
    return {
      columns: [
        {label: 'Title', field: 'title'},
        {label: 'Type', field: 'type'},
      ]
    }
  }
}
</script>
