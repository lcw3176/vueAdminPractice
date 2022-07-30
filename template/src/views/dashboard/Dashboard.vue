<template>
  <v-row>
    <v-col
      cols="12"
    >
      <dashboard-statistics-card></dashboard-statistics-card>
    </v-col>

    <v-col
      cols="6"
    >
      <dashboard-weekly-overview></dashboard-weekly-overview>
    </v-col>

      <v-col
      cols="6"
    >
      <dashboard-weekly-map-overview></dashboard-weekly-map-overview>
    </v-col>

  </v-row>
</template>

<script>
// eslint-disable-next-line object-curly-newline
import { mdiPoll, mdiLabelVariantOutline, mdiCurrencyUsd, mdiHelpCircleOutline } from '@mdi/js'

// demos
import DashboardStatisticsCard from './DashboardStatisticsCard.vue'
import DashboardWeeklyOverview from './DashboardWeeklyOverview.vue'
import DashboardWeeklyMapOverview from './DashboardWeeklyMapOverview.vue'

export default {
  components: {
    DashboardStatisticsCard,
    DashboardWeeklyOverview,
    DashboardWeeklyMapOverview,
  },
  setup() {

  },
}
</script>
