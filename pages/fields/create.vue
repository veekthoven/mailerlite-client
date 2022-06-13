<template>
  <div class="py-6">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-8">
      <h1 class="text-2xl font-semibold text-gray-900">Create Field</h1>
    </div>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-8">
      <!-- Replace with your content -->
      <div class="py-4">
         <div class="pt-8 space-y-6 sm:pt-10 sm:space-y-5">
          <div class="space-y-6 sm:space-y-5">
            
            <form @submit="submitForm">
              <div class="sm:grid sm:grid-cols-3 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5">
                <label for="title" class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"> Title </label>
                <div class="mt-1 sm:mt-0 sm:col-span-2">
                  <input @keydown="errors = []" v-model="formData.title" id="title" type="text" :class="{'border-red-500': errors.hasOwnProperty('title')}" class="block max-w-lg w-full shadow-sm focus:ring-green-500 focus:border-green-500 sm:text-sm border-gray-300 rounded-md">
                  <span class="text-sm text-red-500" v-if="errors.hasOwnProperty('title')">{{ errors.title[0] }}</span>
                </div>
              </div>

              <div class="sm:grid sm:grid-cols-3 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5 mt-5">
                <label for="type" class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"> Type </label>
                <div class="mt-1 sm:mt-0 sm:col-span-2">
                  <select v-model="formData.type" id="type" :class="{'border-red-500': errors.hasOwnProperty('email')}" class="mt-1 block max-w-lg w-full  pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm rounded-md">
                    <option value="string">String</option>
                    <option value="date">Date</option>
                    <option value="boolean">Boolean</option>
                    <option value="number">Number</option>
                  </select>
                  <span class="text-sm text-red-500" v-if="errors.hasOwnProperty('type')">{{ errors.type[0] }}</span>
                </div>
              </div>

              <button @click="submitForm" type="button" :class="{'loader': submitting}" class="mt-5 inline-flex items-center justify-center rounded-md border border-transparent bg-primary px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 sm:w-auto">Submit</button>
            </form>
          </div>
        </div>
      </div>
      <!-- /End replace -->
    </div>
  </div>
</template>

<script>
export default {
  layout: 'default',
  name: 'create',
    data() {
        return {
            formData: {
              title: "",
              type: "",
            },
            errors: [],
            submitting: false
        }
    },
    methods: {
      submitForm () {
        this.submitting = true;

        this.$axios.$post('/fields', this.formData)
        .then(res => {
          this.$toast.success('Field successfully created!')
          this.$router.push('/fields')
        })
        .catch(error => {
          this.errors = error.response.data.errors;
          this.$toast.error('Oops! an error occured.')
        })
        .finally(() => {
          this.submitting = false;
        })
      }
    }
}
</script>
