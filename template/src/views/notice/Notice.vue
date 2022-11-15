<template>
    <v-card id="account-setting-card">
        <!-- tabs -->
        <v-tabs v-model="tab" show-arrows>
            <v-tab v-for="tab in tabs" :key="tab.icon">
                <v-icon size="20" class="me-3">
                    {{ tab.icon }}
                </v-icon>
                <span>{{ tab.title }}</span>
            </v-tab>
        </v-tabs>

        <!-- tabs item -->
        <v-tabs-items v-model="tab">
            <v-tab-item>
                <account-settings-account :notice-data="noticeSettingData.write"></account-settings-account>
            </v-tab-item>

            <v-tab-item>
                <account-settings-security></account-settings-security>
            </v-tab-item>

            <v-tab-item>
                <account-settings-info :information-data="accountSettingData.information"></account-settings-info>
            </v-tab-item>
        </v-tabs-items>
    </v-card>
</template>
  
<script>
import { mdiAccountOutline, mdiLockOpenOutline, mdiInformationOutline } from '@mdi/js'
import { ref } from '@vue/composition-api'

// demos
import AccountSettingsAccount from './NoticeWrite.vue'
import AccountSettingsSecurity from './AccountSettingsSecurity.vue'
import AccountSettingsInfo from './AccountSettingsInfo.vue'

export default {
    components: {
        AccountSettingsAccount,
        AccountSettingsSecurity,
        AccountSettingsInfo,
    },
    setup() {
        const tab = ref('')

        // tabs
        const tabs = [
            { title: '작성', icon: mdiAccountOutline },
            { title: '수정', icon: mdiLockOpenOutline },
            { title: '삭제', icon: mdiInformationOutline },
        ]

        const noticeSettingData = {
            write: {
                title: '카카오 지도 패치',
                status: 'Active',
                content: "하이"
            },
            information: {
                bio: 'The name’s John Deo. I am a tireless seeker of knowledge, occasional purveyor of wisdom and also, coincidentally, a graphic designer. Algolia helps businesses across industries quickly create relevant 😎, scaLabel 😀, and lightning 😍 fast search and discovery experiences.',
                birthday: 'February 22, 1995',
                phone: '954-006-0844',
                website: 'https://themeselection.com/',
                country: 'USA',
                languages: ['English', 'Spanish'],
                gender: 'male',
            },
        }


        // account settings data
        const accountSettingData = {
            account: {
                title: '카카오 지도 패치',
                status: 'Active',
                content: "하이"
            },
            information: {
                bio: 'The name’s John Deo. I am a tireless seeker of knowledge, occasional purveyor of wisdom and also, coincidentally, a graphic designer. Algolia helps businesses across industries quickly create relevant 😎, scaLabel 😀, and lightning 😍 fast search and discovery experiences.',
                birthday: 'February 22, 1995',
                phone: '954-006-0844',
                website: 'https://themeselection.com/',
                country: 'USA',
                languages: ['English', 'Spanish'],
                gender: 'male',
            },
        }

        return {
            tab,
            tabs,
            noticeSettingData,
            accountSettingData,
            icons: {
                mdiAccountOutline,
                mdiLockOpenOutline,
                mdiInformationOutline,
            },
        }
    },
}
</script>
  