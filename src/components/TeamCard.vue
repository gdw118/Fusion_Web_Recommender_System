<template>
  <div
    class="card pl-4 pt-5 pb-2 pr-2 hover:shadow-lg cursor-pointer transition-all duration-300 ease-in-out backdrop-blur-sm bg-white/80 border border-gray-100 rounded-xl mb-4"
  >
    <!-- Title -->
    <h2 class="text-xl font-semibold mb-3 flex items-center text-gray-800">
      <span class="text-gray-900">{{ team_brief_info.title }}</span>
    </h2>

    <!-- Tags with divider -->
    <div class="flex items-center text-sm text-gray-600 mb-4 mt-1">
      <div class="flex items-center">
        <span
          class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-blue-50 text-blue-700 border border-blue-100"
        >
          <svg class="w-4 h-4 mr-1.5" fill="currentColor" viewBox="0 0 20 20">
            <path
              d="M10 2a6 6 0 00-6 6v3.586l-.707.707A1 1 0 004 14h12a1 1 0 00.707-1.707L16 11.586V8a6 6 0 00-6-6zM10 18a3 3 0 01-3-3h6a3 3 0 01-3 3z"
            />
          </svg>
          目标：{{ team_brief_info.goal }}
        </span>
      </div>
      <div class="inline-block mx-3 h-4 bg-gray-200 w-px"></div>
      <div class="flex items-center">
        <span
          class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-green-50 text-green-700 border border-green-100"
        >
          <svg class="w-4 h-4 mr-1.5" fill="currentColor" viewBox="0 0 20 20">
            <path
              d="M13 6a3 3 0 11-6 0 3 3 0 016 0zM18 8a2 2 0 11-4 0 2 2 0 014 0zM14 15a4 4 0 00-8 0v1h8v-1zM6 8a2 2 0 11-4 0 2 2 0 014 0zM16 18v-1a5.972 5.972 0 00-.75-2.906A3.005 3.005 0 0119 15v1h-3zM4.75 12.094A5.973 5.973 0 004 15v1H1v-1a3 3 0 013.75-2.906z"
            />
          </svg>
          当前人数：{{ team_brief_info.cur_people_num }}
        </span>
      </div>
    </div>

    <!-- 技能需求 -->
    <div
      class="flex flex-wrap gap-2 mb-4"
      v-if="team_brief_info.team_skills && team_brief_info.team_skills.length > 0"
    >
      <div v-for="(skills, job) in groupSkillsByJob" :key="job" class="w-full">
        <div class="font-medium text-indigo-600 mb-2 flex items-center">
          <svg class="w-4 h-4 mr-1" fill="currentColor" viewBox="0 0 20 20">
            <path
              d="M10 2a6 6 0 00-6 6v3.586l-.707.707A1 1 0 004 14h12a1 1 0 00.707-1.707L16 11.586V8a6 6 0 00-6-6zM10 18a3 3 0 01-3-3h6a3 3 0 01-3 3z"
            />
          </svg>
          {{ job }}
        </div>
        <div class="flex flex-wrap gap-2 ml-5">
          <div
            v-for="skill in skills"
            :key="skill.skill"
            class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-indigo-50 text-indigo-700 border border-indigo-100 hover:bg-indigo-100 transition-colors duration-200"
          >
            <span>{{ skill.skill }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Creator -->
    <div class="flex items-center text-base text-gray-600 mt-4 pt-3 border-t border-gray-100">
      <div class="flex items-center">
        <div class="relative">
          <img
            v-if="team_brief_info.leader_info.avatar_url != ''"
            :src="team_brief_info.leader_info.avatar_url"
            class="h-8 w-8 rounded-full ring-2 ring-white"
          />
          <img
            v-else
            src="../assets/img/defaultAvatar.svg"
            class="h-8 w-8 rounded-full ring-2 ring-white"
          />
          <span
            class="absolute bottom-0 right-0 block h-2 w-2 rounded-full bg-green-400 ring-2 ring-white"
          ></span>
        </div>
        <div class="ml-3">
          <span class="font-medium text-gray-900">{{ team_brief_info.leader_info.nickname }}</span>
          <div class="flex items-center text-sm text-gray-500">
            <span>{{ team_brief_info.leader_info.enrollment_year }}级</span>
            <div class="inline-block mx-2 h-3 bg-gray-300 w-px"></div>
            <span>{{ team_brief_info.leader_info.college }}</span>
          </div>
        </div>
      </div>
      <div class="ml-auto text-sm text-gray-500" v-if="team_brief_info.created_time">
        创建于 {{ formattedCreatedTime }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    team_brief_info: {
      type: Object,
      default: () => ({
        team_id: null,
        title: '',
        goal: '',
        cur_people_num: 0,
        created_time: 0,
        leader_info: {
          user_id: null,
          nickname: '',
          college: '',
          avatar_url: '',
          gender: null,
          enrollment_year: 0,
          honors: []
        }
      })
    }
  },
  computed: {
    formattedCreatedTime() {
      if (!this.team_brief_info.created_time) return ''
      const date = new Date(this.team_brief_info.created_time * 1000) // 转换为毫秒
      const year = date.getFullYear()
      const month = date.getMonth() + 1 // 注意：getMonth() 是从 0 开始的
      const day = date.getDate()

      return `${year}年${month}月${day}日`
    }
  }
}
</script>
