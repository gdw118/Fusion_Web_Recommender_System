<template>
  <div>
    <NavBar />
    <section class="relative">
      <!-- 背景装饰元素 -->
      <div class="absolute inset-0 overflow-hidden pointer-events-none">
        <div
          class="absolute top-20 left-10 w-64 h-64 bg-indigo-300 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-blob"
        ></div>
        <div
          class="absolute top-40 right-10 w-72 h-72 bg-blue-300 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-blob animation-delay-2000"
        ></div>
        <div
          class="absolute bottom-40 left-1/4 w-80 h-80 bg-purple-300 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-blob animation-delay-4000"
        ></div>
        <div
          class="absolute -bottom-20 right-1/3 w-60 h-60 bg-pink-300 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-blob"
        ></div>
      </div>

      <div
        class="min-h-screen min-w-[1400px] w-full bg-gradient-to-b from-blue-400 to-transparent relative"
      >
        <!-- 顶部装饰图案 -->
        <div
          class="absolute top-0 inset-x-0 h-40 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQ0MCIgaGVpZ2h0PSIyMjAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGRlZnM+PHBhdGggZD0iTTAgMGgxNDQwdjE4OGMtMzYuOCAyMS4zLTgxLjcgMzItMTM0LjcgMzJDMTE3NC45IDIyMCAxMDU3IDEzMCA5MTkgMTMwYy0xMzguMSAwLTI1NS45IDkwLTM2Ni45IDkwLTExMSAwLTIzMC45LTkwLTM2OS45LTkwLTEzOC4xIDAtMTgyLjEgOTAtMTgyLjEgOTBWMHoiIGlkPSJhIi8+PC9kZWZzPjx1c2UgZmlsbD0iI2VmZjZmZiIgZmlsbC1vcGFjaXR5PSIuNSIgeGxpbms6aHJlZj0iI2EiIHRyYW5zZm9ybT0icm90YXRlKDE4MCAxNDQwIDExMCkiLz48L3N2Zz4=')]"
        ></div>

        <div class="mx-auto min-w-[980px] w-2/3 flex justify-between pt-10 relative z-10">
          <div
            class="justify-start h-32 rounded-lg col-span-2 pl-14 text-4xl font-bold text-white flex items-center"
          >
            个人档案
            <div
              class="ml-4 w-10 h-10 bg-white bg-opacity-20 rounded-full flex items-center justify-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 text-white"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"
                />
              </svg>
            </div>
          </div>
          <div class="justify-end h-32 pr-14 rounded-lg flex items-center">
            <router-link
              v-if="isCurrentUser"
              class="inline-flex items-center rounded-md border border-white px-6 py-3 text-lg font-medium text-white transition hover:bg-white hover:bg-opacity-10 hover:shadow-xl focus:outline-none focus:ring-2 focus:ring-white focus:ring-opacity-50"
              :to="{ name: 'userprofileupload' }"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5 mr-2"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z"
                />
              </svg>
              编辑档案
            </router-link>
          </div>
        </div>

        <div
          class="mx-auto min-w-[980px] pt-10 px-20 rounded-lg bg-white w-2/3 shadow-xl mb-20 relative"
        >
          <!-- 卡片右上角装饰 -->
          <div class="absolute top-0 right-0 w-32 h-32 overflow-hidden">
            <div
              class="absolute top-0 right-0 w-16 h-16 bg-indigo-100 transform rotate-45 translate-x-8 -translate-y-8"
            ></div>
          </div>

          <!-- 基本信息部分 -->
          <div class="border-b border-gray-200 pb-8 relative">
            <h1
              class="text-2xl font-bold text-gray-800 inline-block pt-10 mb-6 border-b-2 border-indigo-500 pb-1 items-center"
            >
              <span class="w-2 h-8 bg-indigo-500 rounded-sm mr-3"></span>
              基础信息
            </h1>

            <div class="grid grid-cols-3 gap-6">
              <div class="space-y-6">
                <div>
                  <p class="infotemplate">真实姓名</p>
                  <p class="mt-1 text-lg font-medium text-gray-800">
                    {{ user_profile_info.user_info.realname || '未设置' }}
                  </p>
                </div>
                <div>
                  <p class="infotemplate">入学年份</p>
                  <p class="mt-1 text-lg font-medium text-gray-800">
                    {{ user_profile_info.user_info.enrollment_year || '未设置' }} 级
                  </p>
                </div>
                <div>
                  <p class="infotemplate">所属学院</p>
                  <p class="mt-1 text-lg font-medium text-gray-800">
                    {{ user_profile_info.user_info.college || '未设置' }}
                  </p>
                </div>
                <div>
                  <p class="infotemplate">手机号码</p>
                  <p class="mt-1 text-lg font-medium text-gray-800">
                    {{ user_profile_info.user_info.mobile_phone || '未设置' }}
                  </p>
                </div>
              </div>

              <div class="space-y-6">
                <div>
                  <p class="infotemplate">性别</p>
                  <p
                    v-if="user_profile_info.user_info.gender == 1"
                    class="mt-1 text-lg font-medium text-gray-800"
                  >
                    男
                  </p>
                  <p
                    v-else-if="user_profile_info.user_info.gender == 2"
                    class="mt-1 text-lg font-medium text-gray-800"
                  >
                    女
                  </p>
                  <p v-else class="mt-1 text-lg font-medium text-gray-800">未设置</p>
                </div>
                <div>
                  <p class="infotemplate">QQ号码</p>
                  <p class="mt-1 text-lg font-medium text-gray-800">
                    {{ user_profile_info.qq_number || '未设置' }}
                  </p>
                </div>
                <div>
                  <p class="infotemplate">微信号码</p>
                  <p class="mt-1 text-lg font-medium text-gray-800">
                    {{ user_profile_info.wechat_number || '未设置' }}
                  </p>
                </div>
              </div>

              <div class="text-center">
                <!-- 头像部分 -->
                <div v-if="isCurrentUser" class="relative">
                  <input type="file" id="avatarUpload" @change="avatarUpload" class="sr-only" />
                  <label for="avatarUpload" class="cursor-pointer">
                    <div
                      class="relative w-[170px] h-[170px] mx-auto rounded-full overflow-hidden border-4 border-white shadow-lg"
                    >
                      <img
                        v-if="user_profile_info.user_info.avatar_url"
                        :src="user_profile_info.user_info.avatar_url"
                        class="w-full h-full object-cover"
                      />
                      <img
                        v-else
                        src="../assets/img/defaultAvatar.svg"
                        class="w-full h-full object-cover bg-gray-100"
                      />
                      <div
                        class="absolute inset-0 bg-black bg-opacity-0 flex items-center justify-center opacity-0 hover:bg-opacity-50 hover:opacity-100 transition-opacity"
                      >
                        <p class="text-white font-medium">点击上传头像</p>
                      </div>
                    </div>
                  </label>
                  <p class="mt-3 text-gray-600 font-medium">
                    {{ user_profile_info.user_info.nickname || '未设置昵称' }}
                  </p>
                </div>

                <!-- 当不是当前用户时，仅显示图片 -->
                <div v-else>
                  <div
                    class="w-[170px] h-[170px] mx-auto rounded-full overflow-hidden border-4 border-white shadow-lg"
                  >
                    <img
                      :src="
                        user_profile_info.user_info.avatar_url || '../assets/img/defaultAvatar.svg'
                      "
                      class="w-full h-full object-cover"
                      alt="用户头像"
                    />
                  </div>
                  <p class="mt-3 text-gray-600 font-medium">
                    {{ user_profile_info.user_info.nickname || '未设置昵称' }}
                  </p>
                </div>
              </div>
            </div>
          </div>

          <!-- 个人介绍部分 -->
          <div class="py-8 border-b border-gray-200 relative">
            <h1
              class="text-2xl font-bold text-gray-800 inline-block mb-6 border-b-2 border-indigo-500 pb-1 items-center"
            >
              <span class="w-2 h-8 bg-indigo-500 rounded-sm mr-3"></span>
              个人介绍
            </h1>
            <div class="bg-gray-50 rounded-lg p-6 shadow-sm relative">
              <!-- 装饰引号 -->
              <div
                class="absolute -top-3 -left-3 w-8 h-8 bg-indigo-100 rounded-full flex items-center justify-center"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4 text-indigo-500"
                  fill="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h3.983v10h-9.983z"
                  />
                </svg>
              </div>
              <p class="text-gray-700 leading-relaxed">
                {{ user_profile_info.introduction || '暂无个人介绍' }}
              </p>
            </div>
          </div>

          <!-- 技能列表部分 -->
          <div class="py-8 border-b border-gray-200 relative">
            <h1
              class="text-2xl font-bold text-gray-800 inline-block mb-6 border-b-2 border-indigo-500 pb-1 items-center"
            >
              <span class="w-2 h-8 bg-indigo-500 rounded-sm mr-3"></span>
              技能列表
            </h1>

            <!-- 分类技能展示 -->
            <div class="mt-4 grid grid-cols-1 md:grid-cols-2 gap-6">
              <div
                v-for="(skills, category) in groupedSkills"
                :key="category"
                class="bg-gray-50 rounded-lg p-6 shadow-sm hover:shadow-md transition-shadow relative overflow-hidden"
              >
                <!-- 卡片装饰 -->
                <div
                  class="absolute -top-4 -right-4 w-16 h-16 bg-indigo-100 rounded-full opacity-50"
                ></div>

                <h3
                  class="text-lg font-semibold text-indigo-700 mb-4 border-b border-indigo-200 pb-2 flex items-center relative z-10"
                >
                  <span class="w-2 h-2 bg-indigo-500 rounded-full mr-2"></span>
                  {{ category }}
                </h3>
                <div v-for="skill in skills" :key="skill.skill" class="mb-4 relative z-10">
                  <div class="flex justify-between items-center mb-2">
                    <span class="text-gray-800 font-medium">{{ skill.skill }}</span>
                    <span class="text-sm bg-indigo-100 text-indigo-800 px-2 py-1 rounded-full">{{
                      skill.proficiency
                    }}</span>
                  </div>
                  <div class="w-full bg-gray-200 rounded-full h-2.5">
                    <div
                      class="bg-indigo-600 h-2.5 rounded-full transition-all duration-500"
                      :style="{ width: getProficiencyWidth(skill.proficiency) }"
                    ></div>
                  </div>
                </div>
              </div>
            </div>

            <!-- 如果没有技能，显示提示信息 -->
            <div
              v-if="!user_profile_info.user_skills || user_profile_info.user_skills.length === 0"
              class="mt-4 bg-gray-50 rounded-lg p-8 text-center relative overflow-hidden"
            >
              <!-- 装饰元素 -->
              <div
                class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-indigo-300 via-blue-300 to-purple-300"
              ></div>

              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-12 mx-auto text-gray-400 mb-3"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"
                />
              </svg>
              <p class="text-gray-500 italic">暂无技能信息</p>
              <p v-if="isCurrentUser" class="text-sm text-gray-500 mt-2">
                点击"编辑档案"添加您的技能
              </p>
            </div>
          </div>

          <!-- 荣誉列表部分 -->
          <div class="py-8 pb-16 relative">
            <h1
              class="text-2xl font-bold text-gray-800 inline-block mb-6 border-b-2 border-indigo-500 pb-1 items-center"
            >
              <span class="w-2 h-8 bg-indigo-500 rounded-sm mr-3"></span>
              荣誉列表
            </h1>

            <div class="bg-gray-50 rounded-lg p-6 shadow-sm relative overflow-hidden">
              <!-- 装饰元素 -->
              <div
                class="absolute -bottom-8 -right-8 w-24 h-24 bg-indigo-100 rounded-full opacity-50"
              ></div>
              <div
                class="absolute top-0 right-0 w-20 h-1 bg-gradient-to-l from-indigo-300 to-transparent"
              ></div>

              <ul class="space-y-3 relative z-10">
                <li
                  v-for="(honor, index) in user_profile_info.honors"
                  :key="index"
                  class="flex items-center text-gray-700"
                  v-show="honor && honor.trim()"
                >
                  <div
                    class="flex-shrink-0 w-8 h-8 bg-indigo-100 rounded-full flex items-center justify-center mr-3"
                  >
                    <img src="../assets/img/honor.svg" alt="荣誉" class="h-5 w-5" />
                  </div>
                  <span class="font-medium">{{ honor }}</span>
                </li>
              </ul>

              <!-- 如果没有荣誉，显示提示信息 -->
              <div
                v-if="
                  !user_profile_info.honors ||
                  user_profile_info.honors.length === 0 ||
                  (user_profile_info.honors.length === 1 && !user_profile_info.honors[0])
                "
                class="text-center py-6 relative z-10"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-12 w-12 mx-auto text-gray-400 mb-3"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"
                  />
                </svg>
                <p class="text-gray-500 italic">暂无荣誉信息</p>
                <p v-if="isCurrentUser" class="text-sm text-gray-500 mt-2">
                  点击"编辑档案"添加您的荣誉
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
import { useRouter } from 'vue-router'
import { useRoute } from 'vue-router'
import { useStore } from 'vuex'
import { reactive, computed } from 'vue'
import $ from 'jquery'
import NavBar from '../components/NavBar.vue'
import {
  server_url,
  get_user_profile_url,
  web_user_profile_upload_url,
  web_user_profile_upload_relative_url,
  user_profile_upload_url,
  utils_upload_img_url
} from '../constants/constants'
export default {
  name: 'UserProfileView',
  components: {
    NavBar
  },
  setup() {
    const router = useRouter()
    const route = useRoute()
    const store = useStore()

    const user_profile_info = reactive({
      introduction: '',
      qq_number: '',
      wechat_number: '',
      honors: [''],
      user_skills: [],
      user_info: {
        user_id: 0,
        gender: 0,
        enrollment_year: 0,
        mobile_phone: '',
        college: '',
        nickname: '',
        realname: '',
        avatar_url: '',
        has_profile: false
      }
    })

    const user_profile_url = get_user_profile_url(route.params.user_id)

    const getUserProfileInfo = () => {
      $.ajax({
        url: `${server_url}${user_profile_url}`,
        type: 'GET',
        headers: {
          Authorization: `Bearer ${store.state.user.token}`
        },
        success: function (resp) {
          if (resp.status_code == 0) {
            Object.assign(user_profile_info, resp.user_profile_info)
            if (
              resp.user_profile_info.user_info.user_id == store.state.user.user_info.user_id &&
              !resp.user_profile_info.user_info.has_profile
            ) {
              // 如果是自己的 profile 界面，并且没有创建 profile，则跳转到创建 profile 的界面
              router.push({
                name: 'userprofileupload'
              })
            }
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

    const avatarUpload = (event) => {
      if (user_profile_info.user_info.user_id != store.state.user.user_info.user_id) {
        alert('您没有权限修改他人的头像')
        return
      }
      const file = event.target.files[0]
      if (!file) {
        return // 如果没有文件被选中，则不执行任何操作
      }

      const formData = new FormData()
      formData.append('file', file)

      // 使用 $.ajax 发送请求
      $.ajax({
        url: `${server_url}${utils_upload_img_url}`, // 替换为你的服务器端点
        type: 'POST',
        data: formData,
        headers: {
          Authorization: `Bearer ${store.state.user.token}`
        },
        processData: false, // 告诉jQuery不要处理发送的数据
        contentType: false, // 告诉jQuery不要设置内容类型
        success: function (resp) {
          if (resp.status_code == 0) {
            updateAvatarUrl(resp.image_url)
          } else {
            alert(resp.status_msg)
          }
        },
        error: function (xhr, status, error) {
          alert(error)
        }
      })
    }

    const updateAvatarUrl = (image_url) => {
      let new_user_profile_info = user_profile_info
      new_user_profile_info.user_info.avatar_url = image_url
      $.ajax({
        url: `${server_url}${user_profile_upload_url}`,
        type: 'POST',
        data: JSON.stringify({
          user_id: store.state.user.user_info.user_id,
          user_profile_info: new_user_profile_info
        }),
        headers: {
          'Content-Type': 'application/json',
          Authorization: `Bearer ${store.state.user.token}`
        },
        success: function (resp) {
          // 处理成功的响应
          console.log(resp)
          if (resp.status_code != 0) {
            alert(resp.status_msg)
            return
          }
          user_profile_info.user_info.avatar_url = image_url
          store.dispatch('get_user_info', {
            user_id: store.state.user.user_info.user_id,
            token: store.state.user.token,
            success: () => {}
          })
        },
        error: function (xhr, status, error) {
          // 处理错误
          alert(error)
        }
      })
    }

    const isCurrentUser = computed(() => {
      return user_profile_info.user_info.user_id === store.state.user.user_info.user_id
    })

    const groupedSkills = computed(() => {
      const skills = user_profile_info.user_skills
      const grouped = {}
      skills.forEach((skill) => {
        if (!grouped[skill.category]) {
          grouped[skill.category] = []
        }
        grouped[skill.category].push(skill)
      })
      return grouped
    })

    const getProficiencyWidth = (proficiency) => {
      switch (proficiency) {
        case '一般':
          return '25%'
        case '良好':
          return '50%'
        case '熟练':
          return '75%'
        case '精通':
          return '100%'
        default:
          return '0%'
      }
    }

    return {
      user_profile_info,
      getUserProfileInfo,
      server_url,
      web_user_profile_upload_url,
      avatarUpload,
      user_profile_url,
      user_profile_upload_url,
      store,
      web_user_profile_upload_relative_url,
      isCurrentUser,
      updateAvatarUrl,
      utils_upload_img_url,
      groupedSkills,
      getProficiencyWidth
    }
  }
}
</script>

<style scoped>
.infotemplate {
  color: gray;
  font-size: 15px;
}

/* 动画效果 */
@keyframes blob {
  0% {
    transform: translate(0px, 0px) scale(1);
  }
  33% {
    transform: translate(30px, -50px) scale(1.1);
  }
  66% {
    transform: translate(-20px, 20px) scale(0.9);
  }
  100% {
    transform: translate(0px, 0px) scale(1);
  }
}

.animate-blob {
  animation: blob 7s infinite;
}

.animation-delay-2000 {
  animation-delay: 2s;
}

.animation-delay-4000 {
  animation-delay: 4s;
}
</style>
