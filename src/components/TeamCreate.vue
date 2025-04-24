<template>
  <form @submit.prevent="submitTeamCreate">
    <div class="space-y-10 px-4">
      <!-- Top -->
      <div class="bg-white/30 backdrop-blur-sm rounded-xl p-6 border border-white/20 shadow-sm">
        <div class="flex items-center mb-6">
          <svg class="w-7 h-7 text-indigo-500 mr-3" viewBox="0 0 20 20" fill="currentColor">
            <path
              fill-rule="evenodd"
              d="M10 2a8 8 0 100 16 8 8 0 000-16zm0 14a6 6 0 110-12 6 6 0 010 12zm-1-5a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1zm0-4a1 1 0 011-1h2a1 1 0 110 2h-2a1 1 0 01-1-1z"
              clip-rule="evenodd"
            />
          </svg>
          <span class="text-2xl font-semibold text-gray-900">填写队伍信息</span>
        </div>
        <p class="text-sm text-gray-600 mb-8">
          您创建的队伍将会在赛事板块中展示，创建成功后您可以随时修改队伍信息
        </p>

        <div class="mt-6 grid gap-x-8 gap-y-6 grid-cols-6">
          <!-- 标题 -->
          <div class="col-span-full">
            <div class="flex items-center">
              <div class="flex items-center shrink-0">
                <img src="../assets/img/idea.svg" alt="title" class="h-6 w-6 mr-2" />
                <div for="username" class="block text-lg font-bold leading-6 text-gray-900">
                  队伍标题
                </div>
              </div>
              <div
                class="flex ml-3 bg-yellow-100/80 items-center px-3 py-1 rounded-lg backdrop-blur-sm overflow-hidden"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="stroke-current shrink-0 h-4 w-4 mr-2"
                  fill="none"
                  viewBox="0 0 24 22"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"
                  />
                </svg>
                <span class="text-sm text-gray-700 whitespace-nowrap"
                  >标题格式建议：[目标角色 + 数量] / [目标角色 + 数量] / [目标角色 +
                  数量]......</span
                >
              </div>
            </div>
            <div class="mt-3">
              <input
                type="text"
                name="team-title"
                v-model="team_title"
                id="team-title"
                class="block w-full rounded-lg border-0 py-2 px-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300/50 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600/50 bg-white/50 backdrop-blur-sm text-sm leading-6 transition-all duration-200"
                maxlength="50"
                placeholder="例如：美术设计 1 名 / 程序员 2 名 / 策划 1 名"
              />
            </div>
          </div>

          <!-- 目标 -->
          <div class="col-span-full">
            <div class="flex items-center">
              <img src="../assets/img/goal.svg" alt="goal" class="h-6 w-6 mr-2" />
              <div for="username" class="block text-lg font-bold leading-6 text-gray-900">目标</div>
            </div>
            <div class="mt-3">
              <input
                type="text"
                name="team-goal"
                id="team-goal"
                v-model="team_goal"
                class="block w-full rounded-lg border-0 py-2 px-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300/50 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600/50 bg-white/50 backdrop-blur-sm text-sm leading-6 transition-all duration-200"
                maxlength="50"
                placeholder="例如：冲击国赛金牌！"
              />
            </div>
          </div>
        </div>
      </div>

      <!-- 技能需求 -->
      <div class="bg-white/30 backdrop-blur-sm rounded-xl p-6 border border-white/20 shadow-sm">
        <div class="flex items-center mb-6">
          <img src="../assets/img/honor.svg" alt="skills" class="h-7 w-7 mr-3" />
          <h2 class="text-2xl font-semibold text-gray-900">技能需求</h2>
        </div>
        <p class="text-sm text-gray-600 mb-8">
          请为每个岗位添加所需的技能要求，这将帮助其他用户更好地了解您的团队需求
        </p>
        <div class="mt-6 space-y-8">
          <!-- 岗位列表 -->
          <div
            v-for="(job, jobIndex) in team_jobs"
            :key="jobIndex"
            class="backdrop-blur-md bg-white/70 border border-white/30 rounded-xl p-6 shadow-lg hover:shadow-xl transition-all duration-300 relative"
          >
            <!-- 删除岗位按钮 -->
            <button
              type="button"
              @click="remove_job(jobIndex)"
              class="absolute top-3 right-3 p-1.5 rounded-lg bg-white/50 shadow-[4px_4px_8px_rgba(0,0,0,0.1),-4px_-4px_8px_rgba(255,255,255,0.8)] hover:shadow-[2px_2px_4px_rgba(0,0,0,0.1),-2px_-2px_4px_rgba(255,255,255,0.8)] active:shadow-[inset_2px_2px_4px_rgba(0,0,0,0.1),inset_-2px_-2px_4px_rgba(255,255,255,0.8)] text-gray-600 hover:text-red-600 transition-all duration-200"
              title="删除岗位"
            >
              <svg class="w-4 h-4" viewBox="0 0 20 20" fill="currentColor">
                <path
                  fill-rule="evenodd"
                  d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>
            <!-- 岗位标题 -->
            <div class="flex items-center mb-6">
              <div class="flex items-center">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                    <svg class="w-5 h-5 text-indigo-500" viewBox="0 0 20 20" fill="currentColor">
                      <path
                        d="M13 6a3 3 0 11-6 0 3 3 0 016 0zM18 8a2 2 0 11-4 0 2 2 0 014 0zM14 15a4 4 0 00-8 0v1h8v-1zM6 8a2 2 0 11-4 0 2 2 0 014 0zM16 18v-1a5.972 5.972 0 00-.75-2.906A3.005 3.005 0 0119 15v1h-3zM4.75 12.094A5.973 5.973 0 004 15v1H1v-1a3 3 0 013.75-2.906z"
                      />
                    </svg>
                  </div>
                  <input
                    type="text"
                    v-model="job.name"
                    class="block w-48 h-10 rounded-lg border-0 py-2 pl-10 pr-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300/50 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600/50 bg-white/50 backdrop-blur-sm sm:text-sm sm:leading-6 transition-all duration-200"
                    placeholder="请输入岗位名称"
                  />
                </div>
              </div>
            </div>
            <!-- 技能列表 -->
            <div class="space-y-4">
              <div
                v-for="(skill, skillIndex) in job.skills"
                :key="skillIndex"
                class="grid grid-cols-12 gap-4 items-center"
              >
                <div class="col-span-5">
                  <div class="relative">
                    <div
                      class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none"
                    >
                      <svg class="w-5 h-5 text-emerald-500" viewBox="0 0 20 20" fill="currentColor">
                        <path
                          fill-rule="evenodd"
                          d="M3 4a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zm0 4a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zm0 4a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zm0 4a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
                          clip-rule="evenodd"
                        />
                      </svg>
                    </div>
                    <select
                      v-model="skill.category"
                      @change="handle_category_change(jobIndex, skillIndex)"
                      class="block w-full h-10 rounded-lg border-0 py-2 pl-10 pr-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300/50 focus:ring-2 focus:ring-inset focus:ring-indigo-600/50 bg-white/50 backdrop-blur-sm sm:text-sm sm:leading-6 transition-all duration-200"
                      :class="{ 'text-gray-400': !skill.category }"
                    >
                      <option value="" disabled selected hidden>选择分类</option>
                      <option
                        v-for="category in skill_categories"
                        :key="category.value"
                        :value="category.value"
                      >
                        {{ category.label }}
                      </option>
                    </select>
                  </div>
                </div>
                <div class="col-span-5">
                  <div class="relative">
                    <div
                      class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none"
                    >
                      <svg class="w-5 h-5 text-amber-500" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M10 12a2 2 0 100-4 2 2 0 000 4z" />
                        <path
                          fill-rule="evenodd"
                          d="M.458 10C1.732 5.943 5.522 3 10 3s8.268 2.943 9.542 7c-1.274 4.057-5.064 7-9.542 7S1.732 14.057.458 10zM14 10a4 4 0 11-8 0 4 4 0 018 0z"
                          clip-rule="evenodd"
                        />
                      </svg>
                    </div>
                    <select
                      v-model="skill.skill"
                      class="block w-full h-10 rounded-lg border-0 py-2 pl-10 pr-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300/50 focus:ring-2 focus:ring-inset focus:ring-indigo-600/50 bg-white/50 backdrop-blur-sm sm:text-sm sm:leading-6 transition-all duration-200"
                      :class="{ 'text-gray-400': !skill.skill }"
                      :disabled="!skill.category"
                    >
                      <option value="" disabled selected hidden>选择技能</option>
                      <option
                        v-for="skill_name in skill_names[skill.category] || []"
                        :key="skill_name.value"
                        :value="skill_name.value"
                      >
                        {{ skill_name.label }}
                      </option>
                    </select>
                  </div>
                </div>
                <div class="col-span-2 flex items-center justify-end">
                  <button
                    type="button"
                    @click="remove_skill_from_job(jobIndex, skillIndex)"
                    class="p-1.5 rounded-lg bg-white/50 shadow-[4px_4px_8px_rgba(0,0,0,0.1),-4px_-4px_8px_rgba(255,255,255,0.8)] hover:shadow-[2px_2px_4px_rgba(0,0,0,0.1),-2px_-2px_4px_rgba(255,255,255,0.8)] active:shadow-[inset_2px_2px_4px_rgba(0,0,0,0.1),inset_-2px_-2px_4px_rgba(255,255,255,0.8)] text-gray-600 hover:text-gray-800 transition-all duration-200"
                    title="删除技能"
                  >
                    <svg class="w-4 h-4" viewBox="0 0 20 20" fill="currentColor">
                      <path
                        fill-rule="evenodd"
                        d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </button>
                </div>
              </div>
              <!-- 添加技能按钮 -->
              <button
                type="button"
                @click="add_skill_to_job(jobIndex)"
                class="w-full px-3 py-2.5 rounded-lg border border-dashed border-gray-300 hover:border-indigo-400 text-gray-500 hover:text-indigo-600 transition-all duration-200 inline-flex items-center justify-center text-sm font-medium mt-2 bg-transparent hover:bg-indigo-50/50"
              >
                <svg class="w-4 h-4 mr-1" viewBox="0 0 20 20" fill="currentColor">
                  <path
                    d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z"
                  />
                </svg>
                添加技能
              </button>
            </div>
          </div>
          <button
            type="button"
            @click="add_job"
            class="w-full px-4 py-3.5 rounded-lg border border-dashed border-gray-300 hover:border-indigo-400 text-gray-500 hover:text-indigo-600 transition-all duration-200 inline-flex items-center justify-center text-sm font-medium bg-transparent hover:bg-indigo-50/50 backdrop-blur-sm"
          >
            <svg class="w-4 h-4 mr-1" viewBox="0 0 20 20" fill="currentColor">
              <path
                d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z"
              />
            </svg>
            添加岗位
          </button>
        </div>
      </div>

      <!-- Bottom -->
      <div class="bg-white/30 backdrop-blur-sm rounded-xl p-6 border border-white/20 shadow-sm">
        <div class="flex items-center mb-6">
          <img src="../assets/img/note.svg" alt="description" class="h-7 w-7 mr-3" />
          <h2 class="text-2xl font-semibold text-gray-900">队伍详细介绍</h2>
        </div>
        <p class="text-sm text-gray-600 mb-8">
          请详细描述您的队伍情况，包括队伍现状、项目背景、团队优势、期望的队友特点等，这将帮助其他用户更好地了解您的团队
        </p>

        <RichText :description="description" @update-content="description_update" />
        <div class="error-message mt-3 ml-1">{{ error_message }}</div>
      </div>
    </div>
    <!-- Button -->
    <div class="mt-6 flex items-center justify-end mr-2">
      <button
        type="submit"
        class="rounded-lg bg-indigo-600 px-4 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 transition-all duration-200 transform hover:scale-105 active:scale-95"
      >
        提交
      </button>
    </div>
  </form>
</template>

<script setup>
import RichText from './RichText.vue'
import { ref, onMounted } from 'vue'
import $ from 'jquery'
import { server_url, team_create_url } from '../constants/constants'
import { useStore } from 'vuex'
import router from '../router'

const store = useStore()

const props = defineProps({
  initial_team_info: {
    type: Object,
    required: true
  }
})

const error_message = ref('')
const team_title = ref('')
const team_goal = ref('')
const description = ref('')
const team_jobs = ref([])

// 技能分类选项
const skill_categories = ref([
  { value: '开发技能', label: '开发技能' },
  { value: '人工智能', label: '人工智能' },
  { value: '设计', label: '设计' },
  { value: '商业技能', label: '商业技能' },
  { value: '工程技能', label: '工程技能' },
  { value: '其他', label: '其他' }
])

// 技能名称选项
const skill_names = ref({
  开发技能: [
    { value: 'React', label: 'React' },
    { value: 'Vue', label: 'Vue' },
    { value: 'Node.js', label: 'Node.js' },
    { value: 'Spring', label: 'Spring' },
    { value: 'Django', label: 'Django' },
    { value: 'Flutter', label: 'Flutter' },
    { value: 'Arduino', label: 'Arduino' },
    { value: '树莓派', label: '树莓派' },
    { value: '嵌入式系统', label: '嵌入式系统' }
  ],
  人工智能: [
    { value: 'TensorFlow', label: 'TensorFlow' },
    { value: 'PyTorch', label: 'PyTorch' },
    { value: '自然语言处理', label: '自然语言处理' },
    { value: '计算机视觉', label: '计算机视觉' },
    { value: '强化学习', label: '强化学习' }
  ],
  设计: [
    { value: 'UI设计', label: 'UI设计' },
    { value: 'UX设计', label: 'UX设计' },
    { value: '平面设计', label: '平面设计' },
    { value: '3D建模', label: '3D建模' },
    { value: '动画设计', label: '动画设计' },
    { value: '视频剪辑', label: '视频剪辑' },
    { value: 'CAD制图', label: 'CAD制图' },
    { value: '工业设计', label: '工业设计' }
  ],
  商业技能: [
    { value: '市场调研', label: '市场调研' },
    { value: '用户画像分析', label: '用户画像分析' },
    { value: '营销策划', label: '营销策划' },
    { value: '计划书撰写', label: '计划书撰写' }
  ],
  工程技能: [
    { value: '机械设计', label: '机械设计' },
    { value: '3D打印', label: '3D打印' },
    { value: '电路设计', label: '电路设计' },
    { value: '机器人编程', label: '机器人编程' }
  ],
  其他: [
    { value: '演讲与答辩', label: '演讲与答辩' },
    { value: 'PPT制作', label: 'PPT制作' },
    { value: '文案写作', label: '文案写作' },
    { value: '社会调查', label: '社会调查' },
    { value: '法律基础', label: '法律基础' },
    { value: '教育设计', label: '教育设计' }
  ]
})

team_title.value = props.initial_team_info.title
team_goal.value = props.initial_team_info.goal
description.value = props.initial_team_info.description

// 将已有的技能信息按岗位分组
const init_team_jobs = () => {
  if (props.initial_team_info.team_skills && props.initial_team_info.team_skills.length > 0) {
    const grouped = {}
    props.initial_team_info.team_skills.forEach((skill) => {
      if (!grouped[skill.job]) {
        grouped[skill.job] = []
      }
      grouped[skill.job].push({
        category: skill.category,
        skill: skill.skill
      })
    })

    // 转换为 team_jobs 格式
    team_jobs.value = Object.entries(grouped).map(([job, skills]) => ({
      name: job,
      skills: skills
    }))
  }
}

// 在组件挂载时初始化
onMounted(() => {
  init_team_jobs()
})

const description_update = (content) => {
  description.value = content
}

// 添加岗位
const add_job = () => {
  team_jobs.value.push({
    name: '',
    skills: []
  })
}

// 删除岗位
const remove_job = (index) => {
  team_jobs.value.splice(index, 1)
}

// 添加技能到岗位
const add_skill_to_job = (jobIndex) => {
  team_jobs.value[jobIndex].skills.push({
    category: '',
    skill: ''
  })
}

// 从岗位中删除技能
const remove_skill_from_job = (jobIndex, skillIndex) => {
  team_jobs.value[jobIndex].skills.splice(skillIndex, 1)
}

// 当分类改变时，重置技能名称
const handle_category_change = (jobIndex, skillIndex) => {
  team_jobs.value[jobIndex].skills[skillIndex].skill = ''
}

const submitTeamCreate = () => {
  error_message.value = ''
  if (team_title.value === '') {
    error_message.value = '队伍标题不能为空'
    return
  }
  if (team_goal.value === '') {
    error_message.value = '队伍目标不能为空'
    return
  }
  if (description.value === '') {
    error_message.value = '队伍介绍不能为空'
    return
  }
  if (team_jobs.value.length === 0) {
    error_message.value = '请至少添加一个岗位'
    return
  }
  for (let i = 0; i < team_jobs.value.length; i++) {
    if (team_jobs.value[i].name === '') {
      error_message.value = '请填写岗位名称'
      return
    }
    if (team_jobs.value[i].skills.length === 0) {
      error_message.value = '请为每个岗位添加至少一个技能需求'
      return
    }
    for (let j = 0; j < team_jobs.value[i].skills.length; j++) {
      if (
        team_jobs.value[i].skills[j].category === '' ||
        team_jobs.value[i].skills[j].skill === ''
      ) {
        error_message.value = '请完善技能需求信息'
        return
      }
    }
  }
  $.ajax({
    url: `${server_url}${team_create_url}`,
    type: 'POST',
    data: JSON.stringify({
      user_id: store.state.user.user_info.user_id,
      team_id: props.initial_team_info.team_id,
      title: team_title.value,
      goal: team_goal.value,
      description: description.value,
      team_skills: team_jobs.value.flatMap((job) =>
        job.skills.map((skill) => ({
          skill: skill.skill,
          category: skill.category,
          job: job.name
        }))
      ),
      contest_id: parseInt(props.initial_team_info.contest_id)
    }),
    headers: {
      'Content-Type': 'application/json',
      Authorization: `Bearer ${store.state.user.token}`
    },
    success: function (resp) {
      console.log(resp)
      if (resp.status_code == 0) {
        if (router.currentRoute.value.name === 'team') {
          location.reload()
          return
        }
        router.push({
          name: 'team',
          params: { team_id: resp.team_id }
        })
      } else {
        alert(resp.status_msg)
      }
    },
    error: function (error) {
      // 尝试解析 JSON 格式的错误响应
      try {
        var resp = JSON.parse(error.responseText)

        // 访问 status_msg 属性
        if (
          resp.status_msg ==
          'remote or network error[remote]: biz error: Error 3988 (HY000): Conversion from collation utf8mb3_general_ci into utf8mb4_0900_ai_ci impossible for parameter'
        ) {
          alert('您的描述中可能有暂不支持的字符')
        } else if (resp.status_msg !== undefined) {
          console.log('Status Message:', resp.status_msg)
          alert(resp.status_msg)
        }
      } catch (parseError) {
        console.error('Error parsing JSON:', parseError)
      }
    }
  })
}
</script>

<style scoped>
.error-message {
  color: red;
  white-space: pre-line;
}
</style>