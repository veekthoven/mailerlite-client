<template>
    <div>
        <div>
            <div class="relative z-40 md:hidden" role="dialog" aria-modal="true" v-if="openMenu">

              <div class="fixed inset-0 bg-gray-600 bg-opacity-75"></div>

              <div class="fixed inset-0 flex z-40">
                <div class="relative flex-1 flex flex-col max-w-xs w-full pt-5 pb-4 bg-primary">
                  <div class="absolute top-0 right-0 -mr-12 pt-2">
                    <button 
                        type="button"
                        class="ml-1 flex items-center justify-center h-10 w-10 rounded-full focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
                        @click="openMenu = false"
                    >
                      <span class="sr-only">Close sidebar</span>
                      <!-- Heroicon name: outline/x -->
                      <svg class="h-6 w-6 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                      </svg>
                    </button>
                  </div>

                  <div class="flex-shrink-0 flex items-center px-4">
                    
                  </div>
                  <div class="mt-5 flex-1 h-0 overflow-y-auto">
                    <nav class="px-2 space-y-1">
                        <nuxt-link to="/" class="text-green-100 hover:bg-green-600 group flex items-center px-2 py-2 text-sm font-medium rounded-md">
                          <svg class="mr-3 flex-shrink-0 h-6 w-6 text-green-300" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
                          </svg>
                            Subscribers
                        </nuxt-link>

                        <nuxt-link to="/fields" class="text-white group flex items-center px-2 py-2 text-sm font-medium rounded-md">
                            <svg xmlns="http://www.w3.org/2000/svg" class="mr-3 flex-shrink-0 h-6 w-6 text-green-300" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M4 5a1 1 0 011-1h14a1 1 0 011 1v2a1 1 0 01-1 1H5a1 1 0 01-1-1V5zM4 13a1 1 0 011-1h6a1 1 0 011 1v6a1 1 0 01-1 1H5a1 1 0 01-1-1v-6zM16 13a1 1 0 011-1h2a1 1 0 011 1v6a1 1 0 01-1 1h-2a1 1 0 01-1-1v-6z" />
                            </svg>
                            Fields
                        </nuxt-link>
                    </nav>
                  </div>
                </div>

                <div class="flex-shrink-0 w-14" aria-hidden="true"></div>
              </div>
            </div>

            <!-- Static sidebar for desktop -->
            <div class="hidden md:flex md:w-64 md:flex-col md:fixed md:inset-y-0">
              <div class="flex flex-col flex-grow pt-5 bg-primary overflow-y-auto">
                <div class="flex items-center flex-shrink-0 px-4">
                    <svg class="w-36 mx-auto" viewBox="0 0 437.42 110.29" xmlns="http://www.w3.org/2000/svg"><g fill="#fff"><path d="m135.5 424.25c-7.34 0-13.1 2.9-17.15 8.64a16.15 16.15 0 0 0 -14.52-8.64 18.67 18.67 0 0 0 -15 6.75v-1a5.4 5.4 0 0 0 -5.32-5.32 5.28 5.28 0 0 0 -5.22 5.32v40.32a5.28 5.28 0 0 0 10.55 0v-27.87c2.39-3.92 6-8.3 12.54-8.3 6.18 0 8.59 3 8.59 10.84v25.38a5.28 5.28 0 0 0 10.55 0v-27.92c2.39-3.92 6-8.3 12.54-8.3 6.18 0 8.59 3 8.59 10.84v25.38a5.28 5.28 0 0 0 10.55 0v-27.07c-.01-9.18-5.2-19.05-16.7-19.05z" transform="translate(-78.29 -365.78)"/><path d="m185.88 424.25a41.2 41.2 0 0 0 -16.64 3.46 4.7 4.7 0 0 0 -3.06 4.5 4.48 4.48 0 0 0 4.48 4.57 6.32 6.32 0 0 0 1.53-.24 36.41 36.41 0 0 1 12.19-2.21c8.15 0 11.52 3 11.59 10.41h-10.37c-14.16 0-22.62 6.07-22.62 16.23 0 9.91 8.21 15.1 16.32 15.1a24.86 24.86 0 0 0 16.7-5.84v.14a5.28 5.28 0 0 0 10.55 0v-26.6c-.02-9.72-6.41-19.52-20.67-19.52zm-3.38 42.3c-5.95 0-9-2.19-9-6.52 0-1.59 0-6.43 13.19-6.43h9.31v6.51c-2.79 3.04-7.86 6.44-13.5 6.44z" transform="translate(-78.29 -365.78)"/><rect height="11.96" rx="5.79" width="12.15" x="142.5" y="39.67"/><g transform="translate(-78.29 -365.78)"><path d="m226.77 424.72a5.22 5.22 0 0 0 -5.23 5.32v40.32a5.28 5.28 0 0 0 10.55 0v-40.36a5.27 5.27 0 0 0 -5.32-5.28z"/><path d="m253.47 404a5.22 5.22 0 0 0 -5.23 5.32v61a5.28 5.28 0 0 0 10.55 0v-61a5.27 5.27 0 0 0 -5.32-5.32z"/><path d="m295.2 424.25c-7.52 0-13.69 2.79-17.87 8.08-3.61 4.57-5.6 10.9-5.6 17.83 0 16.22 9.47 25.91 25.34 25.91 8.71 0 13-2 16.95-4.27a5.17 5.17 0 0 0 2.95-4.35 4.66 4.66 0 0 0 -4.76-4.67 4.44 4.44 0 0 0 -2.15.49 24.58 24.58 0 0 1 -12.23 2.8c-8.76 0-14-4.11-15.3-11.91h30.72a5.1 5.1 0 0 0 5.32-5.23c0-16.93-12.11-24.68-23.37-24.68zm0 9.24c4.36 0 11.77 2.5 12.82 11.72h-25.55c.94-8.09 6.96-11.72 12.73-11.72z"/><path d="m355.08 424.25h-.47c-5 0-9.61 2.36-13.76 7v-1.25a5.4 5.4 0 0 0 -5.32-5.32 5.28 5.28 0 0 0 -5.23 5.32v40.32a5.28 5.28 0 0 0 10.55 0v-28.22c3.39-4.89 8.2-7.58 13.57-7.58h.47a5 5 0 0 0 5.32-5 5.13 5.13 0 0 0 -5.13-5.27z"/><path d="m500.71 365.78h-106.43a15 15 0 0 0 -15 15v95.29l20.66-20.46h100.77a15 15 0 0 0 15-15v-59.83a15 15 0 0 0 -15-15zm-89.56 67.22a4 4 0 0 1 -8 0v-42.5a4 4 0 1 1 8 0zm18.6 0a4 4 0 0 1 -8 0v-28.1a4 4 0 1 1 8 0zm.59-40.93a4.34 4.34 0 0 1 -4.34 4.34h-.39a4.34 4.34 0 0 1 -4.34-4.34v-.26a4.34 4.34 0 0 1 4.34-4.34h.39a4.34 4.34 0 0 1 4.34 4.34zm28.13 43.93a13.8 13.8 0 0 1 -5.88 1.28c-6.91 0-10.56-3.33-10.56-9.64v-19.3h-3.65a2.2 2.2 0 0 1 -2.25-2.24 2.45 2.45 0 0 1 .95-1.88l8.85-8.66a2.62 2.62 0 0 1 1.81-.87 2.25 2.25 0 0 1 2.26 2.31v4.24h6.4a3.55 3.55 0 0 1 0 7.11h-6.4v18.78c0 2.72 1.35 2.93 3.26 2.93a8.18 8.18 0 0 0 2.34-.33 6 6 0 0 1 1.59-.26 3.41 3.41 0 0 1 3.36 3.36 3.46 3.46 0 0 1 -2.08 3.17zm24.53-6.25a16.84 16.84 0 0 0 8.38-1.92 3.42 3.42 0 0 1 1.64-.37 3.55 3.55 0 0 1 3.62 3.55 3.9 3.9 0 0 1 -2.21 3.29c-2.79 1.59-5.81 3-12 3-11.25 0-18-6.86-18-18.35 0-13.55 9-18.36 16.65-18.36 11.4 0 16.59 9.07 16.59 17.5a3.85 3.85 0 0 1 -4 3.95h-21c1.04 5.06 4.59 7.71 10.33 7.71z"/><path d="m481.21 407.65a8.41 8.41 0 0 0 -8.52 7.56h17.11a8.46 8.46 0 0 0 -8.59-7.56z"/></g></g></svg>
                </div>
                <div class="mt-5 flex-1 flex flex-col">
                  <nav class="flex-1 px-2 pb-4 space-y-1">
                    <nuxt-link to="/" class="text-green-100 hover:bg-green-600 group flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      <svg class="mr-3 flex-shrink-0 h-6 w-6 text-green-300" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
                      </svg>
                        Subscribers
                    </nuxt-link>

                    <nuxt-link to="/fields" class=" text-white group flex items-center px-2 py-2 text-sm font-medium rounded-md">
                        <svg xmlns="http://www.w3.org/2000/svg" class="mr-3 flex-shrink-0 h-6 w-6 text-green-300" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M4 5a1 1 0 011-1h14a1 1 0 011 1v2a1 1 0 01-1 1H5a1 1 0 01-1-1V5zM4 13a1 1 0 011-1h6a1 1 0 011 1v6a1 1 0 01-1 1H5a1 1 0 01-1-1v-6zM16 13a1 1 0 011-1h2a1 1 0 011 1v6a1 1 0 01-1 1h-2a1 1 0 01-1-1v-6z" />
                        </svg>
                        Fields
                    </nuxt-link>
                  </nav>
                </div>
              </div>
            </div>

            <div class="md:pl-64 flex flex-col flex-1">
              <div class="sticky top-0 z-10 flex-shrink-0 flex h-16 bg-white shadow">
                <button
                    type="button"
                    class="px-4 border-r border-gray-200 text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500 md:hidden"
                    @click="openMenu = true"
                >
                  <span class="sr-only">Open sidebar</span>
                  <!-- Heroicon name: outline/menu-alt-2 -->
                  <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h7" />
                  </svg>
                </button>
              </div>

              <main>
                <nuxt/>
              </main>
            </div>
          </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                openMenu: true
            }
        }   
    }
</script>