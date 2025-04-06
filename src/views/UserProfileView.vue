<template>
  <div
    class="min-h-screen bg-gradient-to-br from-indigo-50 via-blue-50 to-purple-50 relative overflow-hidden"
  >
    <NavBar />

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

    <section class="relative py-12 px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <!-- 顶部信息栏 -->
        <div
          class="backdrop-blur-lg bg-gradient-to-r from-blue-500/80 to-indigo-600/80 rounded-2xl shadow-2xl mb-10 overflow-hidden border border-white/20"
        >
          <div class="flex flex-col md:flex-row items-center justify-between p-8">
            <div class="flex items-center mb-6 md:mb-0">
              <div
                class="w-16 h-16 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center mr-6 shadow-inner"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-8 w-8 text-white"
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
              <h1 class="text-4xl font-bold text-white">个人档案</h1>
            </div>

            <router-link
              v-if="isCurrentUser"
              class="inline-flex items-center rounded-xl border border-white/30 px-6 py-3 text-lg font-medium text-white transition-all duration-300 hover:bg-white/20 hover:shadow-xl focus:outline-none focus:ring-2 focus:ring-white/50 backdrop-blur-sm transform hover:scale-105"
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

          <!-- 波浪装饰 -->
          <div
            class="h-12 bg-gradient-to-r from-blue-400/30 to-indigo-500/30 relative overflow-hidden"
          >
            <svg
              class="absolute bottom-0 w-full h-12"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 1440 320"
            >
              <path
                fill="#ffffff"
                fill-opacity="0.2"
                d="M0,224L48,213.3C96,203,192,181,288,181.3C384,181,480,203,576,202.7C672,203,768,181,864,181.3C960,181,1056,203,1152,208C1248,213,1344,203,1392,197.3L1440,192L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"
              ></path>
            </svg>
          </div>
        </div>

        <!-- 主要内容区域 -->
        <div
          class="backdrop-blur-lg bg-white/70 rounded-2xl shadow-xl overflow-hidden border border-white/50 relative"
        >
          <!-- 卡片右上角装饰 -->
          <div class="absolute top-0 right-0 w-32 h-32 overflow-hidden">
            <div
              class="absolute top-0 right-0 w-16 h-16 bg-indigo-100/70 transform rotate-45 translate-x-8 -translate-y-8"
            ></div>
          </div>

          <!-- 基本信息部分 -->
          <div class="border-b border-gray-200/50 p-8 relative">
            <h2
              class="text-2xl font-bold text-indigo-700 inline-block mb-8 border-b-2 border-indigo-500 pb-1 flex items-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 mr-2"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M5.121 17.804A13.937 13.937 0 0112 16c2.5 0 4.847.655 6.879 1.804M15 10a3 3 0 11-6 0 3 3 0 016 0zm6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              基础信息
            </h2>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
              <!-- 左侧信息 -->
              <div class="space-y-6">
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    真实姓名
                  </p>
                  <p
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    {{ user_profile_info.user_info.realname || '未设置' }}
                  </p>
                </div>
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    入学年份
                  </p>
                  <p
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    {{ user_profile_info.user_info.enrollment_year || '未设置' }} 级
                  </p>
                </div>
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    所属学院
                  </p>
                  <p
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    {{ user_profile_info.user_info.college || '未设置' }}
                  </p>
                </div>
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    手机号码
                  </p>
                  <p
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    {{ user_profile_info.user_info.mobile_phone || '未设置' }}
                  </p>
                </div>
              </div>
              <!-- 中间信息 -->
              <div class="space-y-6">
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    性别
                  </p>
                  <p
                    v-if="user_profile_info.user_info.gender == 1"
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    男
                  </p>
                  <p
                    v-else-if="user_profile_info.user_info.gender == 2"
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    女
                  </p>
                  <p
                    v-else
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    未设置
                  </p>
                </div>
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    QQ号码
                  </p>
                  <p
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    {{ user_profile_info.qq_number || '未设置' }}
                  </p>
                </div>
                <div class="group">
                  <p class="text-sm font-medium text-indigo-600 mb-1 flex items-center">
                    <span class="w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2"></span>
                    微信号码
                  </p>
                  <p
                    class="mt-1 text-lg font-medium text-gray-800 pl-3.5 group-hover:text-indigo-700 transition-colors"
                  >
                    {{ user_profile_info.wechat_number || '未设置' }}
                  </p>
                </div>
              </div>

              <!-- 右侧头像 -->
              <div class="flex flex-col items-center justify-center">
                <!-- 头像部分 -->
                <div v-if="isCurrentUser" class="relative">
                  <input type="file" id="avatarUpload" @change="avatarUpload" class="sr-only" />
                  <label for="avatarUpload" class="cursor-pointer">
                    <div
                      class="relative w-[180px] h-[180px] mx-auto rounded-full overflow-hidden border-4 border-white shadow-lg group"
                    >
                      <img
                        v-if="user_profile_info.user_info.avatar_url"
                        :src="user_profile_info.user_info.avatar_url"
                        class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                      />
                      <img
                        v-else
                        src="../assets/img/defaultAvatar.svg"
                        class="w-full h-full object-cover bg-gray-100 transition-transform duration-500 group-hover:scale-110"
                      />
                      <div
                        class="absolute inset-0 bg-gradient-to-t from-indigo-900/70 to-transparent flex items-end justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300"
                      >
                        <p class="text-white font-medium pb-4">点击上传头像</p>
                      </div>
                    </div>
                  </label>
                  <div class="mt-4 text-center">
                    <p class="text-xl font-semibold text-indigo-700">
                      {{ user_profile_info.user_info.nickname || '未设置昵称' }}
                    </p>
                    <p class="text-sm text-gray-500 mt-1">
                      {{ user_profile_info.user_info.username }}
                    </p>
                  </div>
                </div>

                <!-- 当不是当前用户时，仅显示图片 -->
                <div v-else>
                  <div
                    class="relative w-[180px] h-[180px] mx-auto rounded-full overflow-hidden border-4 border-white shadow-lg"
                  >
                    <img
                      :src="
                        user_profile_info.user_info.avatar_url || '../assets/img/defaultAvatar.svg'
                      "
                      class="w-full h-full object-cover"
                      alt="用户头像"
                    />
                    <div
                      class="absolute inset-0 bg-gradient-to-t from-indigo-900/30 to-transparent"
                    ></div>
                  </div>
                  <div class="mt-4 text-center">
                    <p class="text-xl font-semibold text-indigo-700">
                      {{ user_profile_info.user_info.nickname || '未设置昵称' }}
                    </p>
                    <p class="text-sm text-gray-500 mt-1">
                      {{ user_profile_info.user_info.username }}
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- 个人介绍部分 -->
          <div
            class="p-8 border-b border-gray-200/50 bg-gradient-to-r from-blue-50/50 to-indigo-50/50"
          >
            <h2
              class="text-2xl font-bold text-indigo-700 inline-block mb-6 border-b-2 border-indigo-500 pb-1 flex items-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 mr-2"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
                />
              </svg>
              个人介绍
            </h2>

            <div
              class="backdrop-blur-sm bg-white/50 rounded-xl p-6 shadow-inner border border-white/80"
            >
              <p class="text-gray-700 leading-relaxed whitespace-pre-line">
                {{ user_profile_info.introduction || '该用户暂未填写个人介绍' }}
              </p>
            </div>
          </div>

          <!-- 技能列表部分 -->
          <div class="p-8 border-b border-gray-200/50">
            <h2
              class="text-2xl font-bold text-indigo-700 inline-block mb-6 border-b-2 border-indigo-500 pb-1 flex items-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 mr-2"
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
              技能列表
            </h2>

            <div
              v-if="Object.keys(groupedSkills).length > 0"
              class="grid grid-cols-1 md:grid-cols-2 gap-6"
            >
              <div
                v-for="(skills, category) in groupedSkills"
                :key="category"
                class="backdrop-blur-md bg-gradient-to-br from-white/60 to-indigo-50/60 rounded-xl p-5 border border-white/50 shadow-lg"
              >
                <h3
                  class="text-lg font-semibold text-indigo-700 mb-4 pb-2 border-b border-indigo-100 flex items-center"
                >
                  <span class="w-2 h-2 bg-indigo-500 rounded-full mr-2"></span>
                  {{ category }}
                </h3>
                <div class="grid grid-cols-1 gap-3">
                  <div
                    v-for="skill in skills"
                    :key="skill.skill"
                    class="flex items-center justify-between bg-white/70 backdrop-blur-sm rounded-lg p-3 shadow-sm hover:shadow-md transition-all duration-300 border border-indigo-100/50"
                  >
                    <div class="flex items-center">
                      <div class="w-2 h-2 rounded-full bg-indigo-500 mr-2"></div>
                      <span class="text-gray-800">{{ skill.skill }}</span>
                    </div>
                    <span class="text-xs bg-indigo-100 text-indigo-800 px-3 py-1 rounded-full">
                      {{ skill.proficiency }}
                    </span>
                  </div>
                </div>
              </div>
            </div>

            <!-- 如果没有技能，显示提示信息 -->
            <div
              v-if="!user_profile_info.user_skills || user_profile_info.user_skills.length === 0"
              class="backdrop-blur-md bg-white/40 rounded-xl p-8 text-center border border-dashed border-indigo-200 shadow-inner"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-12 mx-auto text-indigo-300 mb-3"
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
              <p class="text-indigo-500 font-medium">暂无技能信息</p>
            </div>
          </div>

          <!-- 荣誉列表部分 -->
          <div class="p-8 bg-gradient-to-r from-indigo-50/50 to-blue-50/50">
            <h2
              class="text-2xl font-bold text-indigo-700 inline-block mb-6 border-b-2 border-indigo-500 pb-1 flex items-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 mr-2"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"
                />
              </svg>
              荣誉列表
            </h2>

            <div
              v-if="
                user_profile_info.honors &&
                user_profile_info.honors.length > 0 &&
                user_profile_info.honors[0]
              "
              class="grid grid-cols-1 gap-4"
            >
              <div
                v-for="(honor, index) in user_profile_info.honors"
                :key="index"
                v-show="honor && honor.trim()"
                class="backdrop-blur-md bg-white/60 rounded-xl p-5 border border-white/50 shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1"
              >
                <div class="flex items-start">
                  <div
                    class="flex-shrink-0 w-12 h-12 bg-indigo-100 rounded-full flex items-center justify-center mr-4"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-6 w-6 text-indigo-600"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"
                      />
                    </svg>
                  </div>
                  <div class="flex-1">
                    <h3 class="text-lg font-semibold text-indigo-700">{{ honor }}</h3>
                  </div>
                </div>
              </div>
            </div>

            <!-- 如果没有荣誉，显示提示信息 -->
            <div
              v-if="
                !user_profile_info.honors ||
                user_profile_info.honors.length === 0 ||
                (user_profile_info.honors.length === 1 && !user_profile_info.honors[0])
              "
              class="backdrop-blur-md bg-white/40 rounded-xl p-8 text-center border border-dashed border-indigo-200 shadow-inner"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-12 mx-auto text-indigo-300 mb-3"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"
                />
              </svg>
              <p class="text-indigo-500 font-medium">暂无荣誉信息</p>
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

.infotemplate {
  @apply text-sm font-medium text-indigo-600 mb-1 flex items-center;
}
.infotemplate::before {
  content: '';
  @apply w-1.5 h-1.5 bg-indigo-500 rounded-full mr-2;
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
