<template>
  <div class="py-6">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-8">
      <h1 class="text-2xl font-semibold text-gray-900">Create Subscriber</h1>
    </div>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-8">
      <!-- Replace with your content -->
      <div class="py-4">
         <div class="pt-8 space-y-6 sm:pt-10 sm:space-y-5">
          <div class="space-y-6 sm:space-y-5">
            
            <form @submit="submitForm">
              <div class="sm:grid sm:grid-cols-3 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5">
                <label for="name" class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"> Name </label>
                <div class="mt-1 sm:mt-0 sm:col-span-2">
                  <input @keydown="errors = []" v-model="formData.name" id="name" type="text" :class="{'border-red-500': errors.hasOwnProperty('name')}" class="block max-w-lg w-full shadow-sm focus:ring-green-500 focus:border-green-500 sm:text-sm border-gray-300 rounded-md">
                  <span class="text-sm text-red-500" v-if="errors.hasOwnProperty('name')">{{ errors.name[0] }}</span>
                </div>
              </div>

              <div class="sm:grid sm:grid-cols-3 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5 mt-5">
                <label for="email" class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"> Email address </label>
                <div class="mt-1 sm:mt-0 sm:col-span-2">
                  <input @keydown="errors = []" v-model="formData.email" id="email" name="email" type="email" :class="{'border-red-500': errors.hasOwnProperty('email')}" class="block max-w-lg w-full shadow-sm focus:ring-green-500 focus:border-green-500 sm:text-sm border-gray-300 rounded-md">
                  <span class="text-sm text-red-500" v-if="errors.hasOwnProperty('email')">{{ errors.email[0] }}</span>
                </div>
              </div>

              <div class="sm:grid sm:grid-cols-3 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5 mt-5" v-for="(field, index) in formData.fields" :key="index">
                <label :for="field.key" class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"> {{ field.title }} </label>
                <div class="mt-1 sm:mt-0 sm:col-span-2">
                  <input @keydown="errors = []" v-model="field.value" :id="field.key" :type="getHtmlFieldType(field.type)" class="block max-w-lg w-full shadow-sm focus:ring-green-500 focus:border-green-500 sm:text-sm border-gray-300 rounded-md" v-if="getHtmlFieldType(field.type) !== 'boolean'">

                  <label v-else for="default-toggle" class="inline-flex relative items-center cursor-pointer">
                    <input @keydown="errors = []" type="checkbox" :id="field.key" class="sr-only peer" v-model="field.value" value="false">
                    <div @click="field.value = !field.value" class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-green-300 dark:peer-focus:ring-green-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-green-600 peer-checked:bg-green-600"></div>
                  </label>
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
  name: 'home',
    async asyncData({ $axios }) {
        const response = await $axios.$get('/fields')
        return { 
            tempFields: response.fields
        }
    },
    data() {
        return {
            formData: {
              name: "",
              email: "",
              fields: [],
            },
            errors: [],
            submitting: false
        }
    },
    methods: {
      getHtmlFieldType(type) {
        if (type === 'string') {
          return 'text'
        }

        if (type === 'boolean') {
          return 'boolean'
        }

        if (type === 'number') {
          return 'number'
        }

        if (type === 'date') {
          return 'date'
        }

        return 'text'
      },
      submitForm () {
        this.submitting = true;

        let data = JSON.parse(JSON.stringify(this.formData)) 

        data.fields.forEach(field => {
          delete field.title;
        });

        this.$axios.$post('/subscribers', data)
        .then(res => {
          this.$toast.success('Subscriber successfully created!')
          this.$router.push('/')
        })
        .catch(error => {
          this.errors = error.response.data.errors;
          this.$toast.error('Oops! an error occured.')
        })
        .finally(() => {
          this.submitting = false;
        })
      }
  },
  created() {
    this.tempFields.forEach(field => {
      this.formData.fields.push({
        title: field.title,
        key: field.key,
        value: "",
        type: field.type
      })
    });
  }
}
</script>
