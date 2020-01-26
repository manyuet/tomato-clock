<template>
  <div class="app-container">
    <div v-if="user">
      <el-row :gutter="20">

        <!--        <el-col :span="6" :xs="24">-->
        <user-card :user="user" />

        <el-card style="margin-bottom: 20px">
          <panel-group :amount="amount" :panel-group-title="panelGroupTitle" />
        </el-card>

        <el-card>
          <div slot="header">
            <span>时间轴</span>
          </div>
          <timeline />

        </el-card>
        <!--        </el-col>-->

        <!--        <el-col :span="18" :xs="24">-->
        <!--          <el-card>-->
        <!--            <el-tabs v-model="activeTab">-->
        <!--              <el-tab-pane label="Activity" name="activity">-->
        <!--                <activity />-->
        <!--              </el-tab-pane>-->
        <!--              <el-tab-pane label="Timeline" name="timeline">-->
        <!--                <timeline />-->
        <!--              </el-tab-pane>-->
        <!--              <el-tab-pane label="Account" name="account">-->
        <!--                <account :user="user" />-->
        <!--              </el-tab-pane>-->
        <!--            </el-tabs>-->
        <!--          </el-card>-->
        <!--        </el-col>-->

      </el-row>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import UserCard from './components/UserCard'
// import Activity from './components/Activity'
import Timeline from './components/Timeline'
import Account from './components/Account'
import PanelGroup from '../dashboard/admin/components/PanelGroup'

export default {
  name: 'Profile',
  components: { PanelGroup, UserCard, Timeline, Account },
  data() {
    return {
      user: {},
      activeTab: 'timeline',
      amount: [10, 5, 6, 24],
      panelGroupTitle: ['完成目标', '进行目标', '获得成就', '好友人数']
    }
  },
  computed: {
    ...mapGetters([
      'name',
      'avatar',
      'roles',
      'idiograph'
    ])
  },
  created() {
    this.getUser()
  },
  methods: {
    getUser() {
      this.user = {
        name: this.name,
        role: this.roles.join(' | '),
        email: 'admin@test.com',
        idiograph: 'Anyway, to be happy is the most important.',
        avatar: this.avatar
      }
    }
  }
}
</script>
