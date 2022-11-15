<template>
  <v-card>
    <v-card-title class="align-start">
      <span class="font-weight-semibold">사용 현황</span>
      <v-spacer></v-spacer>
      <v-btn
        icon
        small
        class="me-n3 mt-n2"
      >
      </v-btn>
    </v-card-title>

    <v-card-text>
      <v-row>
        <v-col
          v-for="data in statisticsData"
          :key="data.title"
          cols="6"
          md="3"
          class="d-flex align-center"
        >
          <v-avatar
            size="44"
            :color="resolveStatisticsIconVariation (data.title).color"
            rounded
            class="elevation-1"
          >
            <v-icon
              dark
              color="white"
              size="30"
            >
              {{ resolveStatisticsIconVariation (data.title).icon }}
            </v-icon>
          </v-avatar>
          <div class="ms-3">
            <p class="text-xs mb-0">
              {{ data.title }}
            </p>
            <h3 class="text-xl font-weight-semibold">
              {{ data.total }}
            </h3>
          </div>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
// eslint-disable-next-line object-curly-newline
import { mdiAccountOutline, mdiCurrencyUsd, mdiTrendingUp, mdiDotsVertical, mdiLabelOutline } from '@mdi/js'
import axios from 'axios'

export default {
  

  mounted: function () {
    console.log("마운트");
  },

  setup(){
    const statisticsData = [
      {
        title: '누적 이용자',
        total: '245k',
      },
      {
        title: '오늘 이용자',
        total: '12.5k',
      },
      {
        title: '완성된 지도 갯수',
        total: '1.54k',
      },
      {
        title: '유저당 평균 생성량',
        total: '$88k',
      },
    ]

    const resolveStatisticsIconVariation = data => {
      if (data === '누적 이용자') return { icon: mdiTrendingUp, color: 'primary' }
      if (data === '오늘 이용자') return { icon: mdiAccountOutline, color: 'success' }
      if (data === '완성된 지도 갯수') return { icon: mdiLabelOutline, color: 'warning' }
      if (data === '유저당 평균 생성량') return { icon: mdiCurrencyUsd, color: 'info' }

      return { icon: mdiAccountOutline, color: 'success' }
    }

    return {
      statisticsData,
      resolveStatisticsIconVariation,

      // icons
      icons: {
        mdiDotsVertical,
        mdiTrendingUp,
        mdiAccountOutline,
        mdiLabelOutline,
        mdiCurrencyUsd,
      },
    }
  }

}
</script>
