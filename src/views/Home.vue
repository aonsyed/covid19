<template>
  <div class="home px-16 pt-32 pb-64 ">
    <div class="row flex flex-wrap">
      <div class="w-full lg:w-1/2 px-16 pb-32 text-blue-300">
        <div
          class="mb-16 text-24 font-medium"
          v-html="$t('views.home.title')"
        ></div>

        <div
          class="text-16"
          v-html="$t('views.home.description')"
        ></div>
      </div>

      <div class="flex flex-wrap w-full lg:w-1/2">
        <div class="flex-shrink-0 px-16 w-full sm:w-1/2 mb-32">
          <div class="border border-gray-100">
            <div class="flex items-center px-16 h-32 text-blue-300 font-medium text-16 border-b border-gray-100">
              {{ $t('views.home.cases') }}
            </div>

            <div class="flex flex-col justify-center items-center p-16 text-34 text-blue-200 font-bold">
              {{ getAppCases }}

              <div v-if="getAppCases !== 0 && getAppTotalCases !== 0 && getAppActive !== ''" class="text-12">
                {{ getAppTotalCases }} ({{ Math.round((getAppCases / getAppTotalCases) * 100) }}%)
              </div>
            </div>
          </div>
        </div>

        <div class="flex-shrink-0 px-16 w-full sm:w-1/2 mb-32">
          <div class="border border-gray-100">
            <div class="flex items-center px-16 h-32 text-blue-300 font-medium text-16 border-b border-gray-100">
              {{ $t('views.home.deaths') }}
            </div>

            <div class="flex flex-col justify-center items-center p-16 text-34 text-red-100 font-bold">
              {{ getAppDeaths }}

              <div v-if="getAppDeaths !== 0 && getAppTotalDeaths !== 0  && getAppActive !== ''" class="text-12">
                  {{ getAppTotalDeaths }} ({{ Math.round((getAppDeaths / getAppTotalDeaths) * 100) }}%)
              </div>
            </div>
          </div>
        </div>

        <div class="flex-shrink-0 px-16 w-full sm:w-1/2 mb-32">
          <div class="border border-gray-100">
            <div class="flex items-center px-16 h-32 text-blue-300 font-medium text-16 border-b border-gray-100">
              {{ $t('views.home.critical') }}
            </div>

            <div class="flex flex-col justify-center items-center p-16 text-34 text-orange-100 font-bold">
              {{ getAppCritical }}

              <div v-if="getAppCritical !== 0 && getAppTotalCritical !== 0  && getAppActive !== ''" class="text-12">
                  {{ getAppTotalCritical }} ({{ Math.round((getAppCritical / getAppTotalCritical) * 100) }}%)
              </div>
            </div>
          </div>
        </div>

        <div class="flex-shrink-0 px-16 w-full sm:w-1/2 mb-32">
          <div class="border border-gray-100">
            <div class="flex items-center px-16 h-32 text-blue-300 font-medium text-16 border-b border-gray-100">
              {{ $t('views.home.recovered') }}
            </div>

            <div class="flex flex-col justify-center items-center p-16 text-34 text-green-100 font-bold">
              {{ getAppRecovered }}

              <div v-if="getAppRecovered !== 0 && getAppTotalRecovered !== 0  && getAppActive !== ''" class="text-12">
                  {{ getAppTotalRecovered }} ({{ Math.round((getAppRecovered / getAppTotalRecovered) * 100) }}%)
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <charts-component />
    <!--<social-component />-->
  </div>
</template>

<script>

import { mapGetters } from 'vuex'

import Charts from '@/components/charts/Charts'
// import Social from '@/components/social/Social'

export default {
  name: 'home',
  computed: {
    ...mapGetters([
      'getAppActive',

      'getAppCases',
      'getAppTotalCases',

      'getAppDeaths',
      'getAppTotalDeaths',

      'getAppCritical',
      'getAppTotalCritical',

      'getAppRecovered',
      'getAppTotalRecovered'
    ])
  },
  components: {
    'charts-component': Charts
    // 'social-component': Social
  }
}

</script>
