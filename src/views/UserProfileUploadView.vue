<template>
  <div>
    <NavBar />
    <form class="min-w-[1310px] px-80" @submit.prevent="submitForm">
      <div class="border-b border-gray-900/10 pb-12 min-w-full">
        <h2 class="text-base font-semibold leading-7 text-gray-900 pt-10">用户档案</h2>
        <p class="mt-1 text-sm leading-6 text-gray-600">
          上传用户档案，包括手机号、个人介绍、QQ 号码、微信号码、技能列表、所获荣誉列表
        </p>

        <div class="mt-10 grid gap-x-6 gap-y-8 grid-cols-6">
          <div class="col-span-3 col-start-1">
            <label class="block text-sm font-medium leading-6 text-gray-900"
              ><span class="text-red-500">*</span>手机号码</label
            >
            <div class="mt-2">
              <input
                type="text"
                v-model="user_profile_info.user_info.mobile_phone"
                name="mobile_phone"
                id="mobile_phone"
                autocomplete="address-level2"
                class="block w-1/2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm leading-6 pl-2"
                required
              />
            </div>
          </div>

          <div class="col-span-3">
            <label class="block text-sm font-medium leading-6 text-gray-900">QQ号码</label>
            <div class="mt-2">
              <input
                type="text"
                v-model="user_profile_info.qq_number"
                name="qq_number"
                id="qq_number"
                autocomplete="address-level1"
                class="block w-1/2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm leading-6 pl-2"
              />
            </div>
          </div>

          <div class="col-span-3">
            <label class="block text-sm font-medium leading-6 text-gray-900">微信号码</label>
            <div class="mt-2">
              <input
                type="text"
                v-model="user_profile_info.wechat_number"
                name="wechat_number"
                id="wechat_number"
                autocomplete="wechat_number"
                class="block w-1/2 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm leading-6 pl-2"
              />
            </div>
          </div>
          <div class="col-span-full">
            <label class="block text-sm font-medium leading-6 text-gray-900"
              ><span class="text-red-500">*</span>个人介绍</label
            >
            <div class="mt-2">
              <textarea
                id="introduction"
                v-model="user_profile_info.introduction"
                name="introduction"
                class="py-1.5 min-h-[200px] block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm leading-6 pl-2"
                required
              />
            </div>
            <p class="mt-3 text-sm leading-6 text-gray-600">介绍一下自己的能力和特长</p>
          </div>

          <!-- 技能列表部分 -->
          <div class="col-span-full">
            <label class="block text-sm font-medium leading-6 text-gray-900">技能列表</label>

            <!-- 已添加的技能 -->
            <div class="mt-4 grid grid-cols-1 md:grid-cols-2 gap-4">
              <div
                v-for="(skills, category) in groupedSkills"
                :key="category"
                class="bg-gray-50 rounded-lg p-4"
              >
                <h3
                  class="text-sm font-semibold text-indigo-700 mb-2 border-b border-indigo-100 pb-1"
                >
                  {{ category }}
                </h3>
                <div
                  v-for="skill in skills"
                  :key="skill.skill"
                  class="mb-2 flex items-center justify-between"
                >
                  <div class="flex items-center">
                    <div class="w-2 h-2 rounded-full bg-indigo-500 mr-2"></div>
                    <span class="text-sm text-gray-800">{{ skill.skill }}</span>
                  </div>
                  <div class="flex items-center">
                    <span
                      class="text-xs bg-indigo-100 text-indigo-800 px-2 py-1 rounded-full mr-2"
                      >{{ skill.proficiency }}</span
                    >
                    <img
                      src="../assets/img/reduce.svg"
                      alt="remove"
                      @click="
                        removeSkill(
                          user_profile_info.user_skills.findIndex(
                            (s) => s.skill === skill.skill && s.category === skill.category
                          )
                        )
                      "
                      class="h-4 w-4 cursor-pointer transition-transform transform active:scale-90"
                    />
                  </div>
                </div>
              </div>
            </div>

            <!-- 如果没有技能，显示提示信息 -->
            <div
              v-if="!user_profile_info.user_skills || user_profile_info.user_skills.length === 0"
              class="mt-2 text-sm text-gray-500 italic"
            >
              暂无技能信息，请添加技能
            </div>

            <!-- 添加技能表单 -->
            <div class="mt-4 p-4 bg-gray-50 rounded-lg border border-gray-200">
              <h3 class="text-sm font-medium text-gray-700 mb-3">添加新技能</h3>
              <div class="flex flex-wrap items-center gap-3">
                <select
                  v-model="selectedCategory"
                  @change="onCategoryChange"
                  class="py-1.5 w-40 block rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-indigo-600 leading-6 pl-2 text-sm"
                >
                  <option value="" disabled>选择分类</option>
                  <option v-for="category in skillCategories" :key="category" :value="category">
                    {{ category }}
                  </option>
                </select>

                <select
                  v-model="selectedSkill"
                  class="py-1.5 w-40 block rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-indigo-600 leading-6 pl-2 text-sm"
                  :disabled="!selectedCategory"
                >
                  <option value="" disabled>选择技能</option>
                  <option v-for="skill in availableSkills" :key="skill" :value="skill">
                    {{ skill }}
                  </option>
                </select>

                <select
                  v-model="selectedProficiency"
                  class="py-1.5 w-32 block rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-indigo-600 leading-6 pl-2 text-sm"
                >
                  <option value="" disabled>熟练度</option>
                  <option v-for="level in proficiencyLevels" :key="level" :value="level">
                    {{ level }}
                  </option>
                </select>

                <button
                  @click="addSkill"
                  type="button"
                  class="inline-flex items-center px-3 py-1.5 text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                >
                  <svg
                    class="h-4 w-4 mr-1"
                    fill="none"
                    stroke="currentColor"
                    viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M12 6v6m0 0v6m0-6h6m-6 0H6"
                    ></path>
                  </svg>
                  添加技能
                </button>
              </div>
            </div>

            <p class="mt-3 text-sm leading-6 text-gray-600">添加自己掌握的技能和熟练程度</p>
          </div>

          <div class="col-span-full">
            <label class="block text-sm font-medium leading-6 text-gray-900">荣誉列表</label>
            <p
              class="mt-2 text-sm leading-6 text-gray-600 flex items-center"
              v-for="honor in user_profile_info.honors"
              :key="honor.id"
            >
              <img src="../assets/img/honor.svg" alt="goal" class="h-6 w-6 mr-3" />
              <span class="pt-1">{{ honor }}</span>
              <img
                src="../assets/img/reduce.svg"
                alt="goal"
                @click="user_profile_info.honors.splice(user_profile_info.honors.indexOf(honor), 1)"
                class="h-4 w-4 ml-3 cursor-pointer transition-transform transform active:scale-90"
              />
            </p>
            <div class="mt-2 flex items-center gap-4">
              <input
                type="text"
                id="honors"
                v-model="honor"
                name="honors"
                class="py-1.5 w-96 block rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 leading-6 pl-2"
              />
              <span
                @click="add_honor"
                class="link-hover cursor-pointer link-accent transition-transform transform active:scale-90"
                >+ 添加荣誉</span
              >
            </div>
            <p class="mt-3 text-sm leading-6 text-gray-600">介绍一下自己曾获得的荣誉</p>
          </div>
        </div>
      </div>
      <div class="block mt-8 min-h-[100px] min-w-[200px]">
        <div class="float-right">
          <router-link
            type="button"
            class="text-sm font-semibold leading-6 text-gray-900"
            :to="{
              name: 'userprofile',
              params: { user_id: store.state.user.user_info.user_id }
            }"
          >
            Cancel
          </router-link>

          <button
            type="submit"
            class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 ml-4"
          >
            Save
          </button>
        </div>
      </div>
    </form>
    <div class="mb-20"></div>
  </div>
</template>
    
<script setup>
import { useStore } from 'vuex'
import { reactive, ref, computed } from 'vue'
import $ from 'jquery'
import NavBar from '../components/NavBar.vue'
import { server_url, user_profile_upload_url, get_user_profile_url } from '../constants/constants'
import router from '@/router/index'

const user_profile_info = reactive({
  introduction: '',
  qq_number: '',
  wechat_number: '',
  user_skills: [],
  honors: [''],
  user_info: {
    user_id: 0,
    gender: 0,
    enrollment_year: 0,
    mobile_phone: '',
    college: '',
    nickname: '',
    realname: '',
    avatar_url: '',
    has_profile: true
  }
})

// 技能分类和技能数据
const skillCategories = ['开发技能', '人工智能', '设计', '商业技能', '工程技能', '其他']

const skillsMap = {
  开发技能: [
    'React',
    'Vue',
    'Node.js',
    'Spring',
    'Django',
    'Flutter',
    'Arduino',
    '树莓派',
    '嵌入式系统'
  ],
  人工智能: ['TensorFlow', 'PyTorch', '自然语言处理', '计算机视觉', '强化学习'],
  设计: ['UI设计', 'UX设计', '平面设计', '3D建模', '动画设计', '视频剪辑', 'CAD制图', '工业设计'],
  商业技能: ['市场调研', '用户画像分析', '营销策划', '计划书撰写'],
  工程技能: ['机械设计', '3D打印', '电路设计', '机器人编程'],
  其他: ['演讲与答辩', 'PPT制作', '文案写作', '社会调查', '法律基础', '教育设计']
}

const proficiencyLevels = ['一般', '良好', '熟练', '精通']

const selectedCategory = ref('')
const selectedSkill = ref('')
const selectedProficiency = ref('')

// 根据选择的分类获取可用的技能
const availableSkills = computed(() => {
  if (!selectedCategory.value) return []
  return skillsMap[selectedCategory.value] || []
})

// 当分类改变时重置选择的技能
const onCategoryChange = () => {
  selectedSkill.value = ''
}

// 添加技能
const addSkill = () => {
  if (!selectedCategory.value || !selectedSkill.value || !selectedProficiency.value) {
    alert('请选择技能分类、技能和熟练度')
    return
  }

  // 检查是否已存在相同技能
  const exists = user_profile_info.user_skills.some(
    (skill) => skill.category === selectedCategory.value && skill.skill === selectedSkill.value
  )

  if (exists) {
    alert('该技能已添加')
    return
  }

  user_profile_info.user_skills.push({
    user_id: store.state.user.user_info.user_id,
    category: selectedCategory.value,
    skill: selectedSkill.value,
    proficiency: selectedProficiency.value
  })

  // 重置选择
  selectedSkill.value = ''
  selectedProficiency.value = ''
}

// 移除技能
const removeSkill = (index) => {
  user_profile_info.user_skills.splice(index, 1)
}

const store = useStore()
const user_profile_url = get_user_profile_url(store.state.user.user_info.user_id)

const getUserProfileInfo = () => {
  //const token = store.state.user.token

  $.ajax({
    url: `${server_url}${user_profile_url}`,
    type: 'GET',
    headers: {
      Authorization: `Bearer ${store.state.user.token}`
    },
    success: function (resp) {
      if (resp.status_code == 0) {
        Object.assign(user_profile_info, resp.user_profile_info)
      } else {
        alert(resp.status_msg)
      }
    },
    error: function (xhr, status, error) {
      alert(error)
    }
  })
}

getUserProfileInfo()

const submitForm = () => {
  $.ajax({
    url: `${server_url}${user_profile_upload_url}`,
    type: 'POST',
    data: JSON.stringify({
      user_id: store.state.user.user_info.user_id,
      user_profile_info: user_profile_info
    }),
    headers: {
      Authorization: `Bearer ${store.state.user.token}`,
      'Content-Type': 'application/json'
    },
    success: function (resp) {
      // 处理成功的响应
      console.log(resp)
      if (resp.status_code != 0) {
        alert(resp.status_msg)
        return
      }
      store.dispatch('get_user_info', {
        user_id: store.state.user.user_info.user_id,
        token: store.state.user.token,
        success: () => {
          router.push({
            name: 'userprofile',
            params: { user_id: store.state.user.user_info.user_id }
          })
        }
      })
    },
    error: function (xhr, status, error) {
      // 处理错误
      alert(error)
    }
  })
}

const honor = ref('')
const add_honor = () => {
  if (honor.value.trim() === '') {
    return
  }
  user_profile_info.honors.push(honor.value)
  honor.value = ''
}

// 技能分组
const groupedSkills = computed(() => {
  const groups = {}
  user_profile_info.user_skills.forEach((skill) => {
    if (!groups[skill.category]) {
      groups[skill.category] = []
    }
    groups[skill.category].push(skill)
  })
  return groups
})
</script>

<style scoped>
</style>