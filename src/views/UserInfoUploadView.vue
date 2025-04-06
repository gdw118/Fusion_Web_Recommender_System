<template>
  <section class="bg-gray-50">
    <section class="flex flex-col md:flex-row h-screen items-center">
      <!-- 填写昵称、真实姓名、性别、学院、专业、QQ 账号、微信号 -->
      <div
        class="bg-gray-50 w-full md:max-w-md lg:max-w-full md:mx-auto md:w-1/2 xl:w-1/3 h-screen px-6 lg:px-16 xl:px-12 flex items-center justify-center"
      >
        <div class="w-full max-w-md mx-auto">
          <div class="text-center mb-8">
            <svg
              class="mx-auto"
              width="240"
              height="80"
              viewBox="0 0 240 80"
              xmlns="http://www.w3.org/2000/svg"
            >
              <!-- Fusion 文字部分 -->
              <text
                x="120"
                y="52"
                font-family="Arial"
                font-size="42"
                font-weight="bold"
                text-anchor="middle"
              >
                <tspan fill="#4285F4">F</tspan>
                <tspan fill="#DB4437">u</tspan>
                <tspan fill="#F4B400">s</tspan>
                <tspan fill="#0F9D58">i</tspan>
                <tspan fill="#4285F4">o</tspan>
                <tspan fill="#DB4437">n</tspan>
              </text>
              <!-- 装饰性元素 -->
              <circle cx="30" cy="40" r="3" fill="#4285F4" opacity="0.6" />
              <circle cx="210" cy="40" r="3" fill="#DB4437" opacity="0.6" />
            </svg>
          </div>
          <h1 class="text-2xl font-bold text-center text-gray-800 mb-4">完善个人信息</h1>
          <p class="text-center text-gray-600 mb-8">请填写您的基本资料以完成注册</p>

          <form class="mt-6 bg-white p-8 rounded-lg shadow-md" @submit.prevent>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <!-- 昵称 -->
              <div class="col-span-1">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5 text-gray-400"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </div>
                  <input
                    type="text"
                    v-model="nickname"
                    placeholder="昵称 *"
                    class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                  />
                </div>
                <p class="text-xs text-gray-500 mt-1 ml-1">3-10个字符</p>
              </div>

              <!-- 真实姓名 -->
              <div class="col-span-1">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5 text-gray-400"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-6-3a2 2 0 11-4 0 2 2 0 014 0zm-2 4a5 5 0 00-4.546 2.916A5.986 5.986 0 005 10a6 6 0 0012 0c0-.35-.035-.691-.1-1.02A5 5 0 0010 11z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </div>
                  <input
                    type="text"
                    v-model="realname"
                    placeholder="真实姓名 *"
                    class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                  />
                </div>
              </div>

              <!-- 性别 -->
              <div class="col-span-1">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5 text-gray-400"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </div>
                  <select
                    v-model="gender"
                    class="w-full pl-10 pr-8 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent appearance-none transition-colors duration-200"
                  >
                    <option value="0" selected disabled hidden>性别 *</option>
                    <option value="1">男</option>
                    <option value="2">女</option>
                  </select>
                  <div
                    class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none"
                  >
                    <svg
                      class="w-4 h-4 text-gray-400"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M19 9l-7 7-7-7"
                      ></path>
                    </svg>
                  </div>
                </div>
              </div>

              <!-- 入学年份 -->
              <div class="col-span-1">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5 text-gray-400"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M6 2a1 1 0 00-1 1v1H4a2 2 0 00-2 2v10a2 2 0 002 2h12a2 2 0 002-2V6a2 2 0 00-2-2h-1V3a1 1 0 10-2 0v1H7V3a1 1 0 00-1-1zm0 5a1 1 0 000 2h8a1 1 0 100-2H6z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </div>
                  <input
                    type="text"
                    v-model="enrollmentYear"
                    placeholder="入学年份 *"
                    class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                  />
                </div>
                <p class="text-xs text-gray-500 mt-1 ml-1">如：2021</p>
              </div>

              <!-- 手机号 -->
              <div class="col-span-1">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5 text-gray-400"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        d="M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z"
                      />
                    </svg>
                  </div>
                  <input
                    type="text"
                    v-model="mobilePhone"
                    placeholder="手机号码 *"
                    class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                  />
                </div>
              </div>

              <!-- 学院 -->
              <div class="col-span-1">
                <div class="relative">
                  <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5 text-gray-400"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        d="M10.394 2.08a1 1 0 00-.788 0l-7 3a1 1 0 000 1.84L5.25 8.051a.999.999 0 01.356-.257l4-1.714a1 1 0 11.788 1.838L7.667 9.088l1.94.831a1 1 0 00.787 0l7-3a1 1 0 000-1.838l-7-3zM3.31 9.397L5 10.12v4.102a8.969 8.969 0 00-1.05-.174 1 1 0 01-.89-.89 11.115 11.115 0 01.25-3.762zM9.3 16.573A9.026 9.026 0 007 14.935v-3.957l1.818.78a3 3 0 002.364 0l5.508-2.361a11.026 11.026 0 01.25 3.762 1 1 0 01-.89.89 8.968 8.968 0 00-5.35 2.524 1 1 0 01-1.4 0zM6 18a1 1 0 001-1v-2.065a8.935 8.935 0 00-2-.712V17a1 1 0 001 1z"
                      />
                    </svg>
                  </div>
                  <select
                    v-model="college"
                    class="w-full pl-10 pr-8 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent appearance-none transition-colors duration-200"
                  >
                    <option value="" selected disabled hidden>学院 *</option>
                    <option value="人文学院">人文学院</option>
                    <option value="教育学院">教育学院</option>
                    <option value="学前教育学院">学前教育学院</option>
                    <option value="哲学与法政学院">哲学与法政学院</option>
                    <option value="马克思主义学院">马克思主义学院</option>
                    <option value="外国语学院">外国语学院</option>
                    <option value="商学院">商学院</option>
                    <option value="对外汉语学院">对外汉语学院</option>
                    <option value="旅游学院">旅游学院</option>
                    <option value="音乐学院">音乐学院</option>
                    <option value="美术学院">美术学院</option>
                    <option value="影视传媒学院">影视传媒学院</option>
                    <option value="体育学院">体育学院</option>
                    <option value="数理学院">数理学院</option>
                    <option value="生命科学学院">生命科学学院</option>
                    <option value="化学与材料科学学院">化学与材料科学学院</option>
                    <option value="环境与地理科学学院">环境与地理科学学院</option>
                    <option value="信息与机电工程学院">信息与机电工程学院</option>
                    <option value="建筑工程学院">建筑工程学院</option>
                    <option value="上海退役军人学院">上海退役军人学院</option>
                    <option value="继续教育学院">继续教育学院</option>
                  </select>
                  <div
                    class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none"
                  >
                    <svg
                      class="w-4 h-4 text-gray-400"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M19 9l-7 7-7-7"
                      ></path>
                    </svg>
                  </div>
                </div>
              </div>
            </div>

            <div
              class="bg-red-50 border border-red-200 rounded-md p-3 mt-6 mb-4"
              v-if="error_message"
            >
              <p class="text-sm text-red-600">{{ error_message }}</p>
            </div>

            <div class="flex justify-between items-center mt-8">
              <router-link
                :to="{ name: 'login' }"
                class="text-sm font-medium text-blue-600 hover:text-blue-800 transition-colors duration-200"
                >返回登录</router-link
              >
              <button
                type="submit"
                class="px-6 py-2.5 bg-blue-600 hover:bg-blue-700 focus:bg-blue-700 text-white font-medium rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-all duration-200 transform hover:scale-105"
                @click="user_info_upload"
              >
                提交信息
              </button>
            </div>
          </form>

          <p class="text-sm text-gray-500 mt-12 text-center">
            &copy; 2025 SHNU CoderSky - All Rights Reserved.
          </p>
        </div>
      </div>

      <div class="hidden lg:block w-full md:w-1/2 h-screen">
        <img
          src="../assets/img/fusion-sky-skyscrapers.png"
          alt=""
          class="w-full h-full object-cover"
        />
      </div>
    </section>
  </section>
</template>

<script>
import { ref } from 'vue'
import router from '@/router/index'
import { useStore } from 'vuex'

export default {
  setup() {
    const store = useStore()
    // user info 内容
    let nickname = ref('')
    let realname = ref('')
    let gender = ref('')
    let mobilePhone = ref('')
    let college = ref('')
    let qqAccount = ref('')
    let weChatAccount = ref('')
    let enrollmentYear = ref('')
    let error_message = ref('')

    let checkoutUserInfo = () => {
      const phonePattern = /^1[3-9]\d{9}$/ // 手机号正则表达式
      const yearPattern = /^[1-9]\d{3}$/ // Matches a 4-digit number starting with a non-zero

      if (!nickname.value.trim() || nickname.value.length < 3 || nickname.value.length > 10) {
        error_message.value = '昵称长度应在 3 到 10 个字符之间'
        return false
      } else if (!realname.value.trim()) {
        error_message.value = '真实姓名不能为空'
        return false
      } else if (!gender.value) {
        error_message.value = '性别不能为空'
        return false
      } else if (!mobilePhone.value.trim() || !phonePattern.test(mobilePhone.value)) {
        error_message.value = '请输入有效的手机号码'
        return false
      } else if (!college.value.trim()) {
        error_message.value = '学院不能为空'
        return false
      } else if (!yearPattern.test(enrollmentYear.value)) {
        error_message.value = '入学年份格式错误，仅需填写四位年份数字'
        return false
      } else {
        error_message.value = ''
        return true
      }
    }

    let user_info_upload = () => {
      error_message.value = ''
      if (checkoutUserInfo()) {
        store.dispatch('user_info_upload', {
          token: store.state.user.token,
          user_info: {
            user_id: 0,
            gender: parseInt(gender.value),
            enrollment_year: parseInt(enrollmentYear.value),
            mobile_phone: mobilePhone.value,
            college: college.value,
            nickname: nickname.value,
            realname: realname.value,
            has_profile: false
          },
          success() {
            router.push({ name: 'home' })
          },
          error(msg) {
            error_message.value = msg
          }
        })
      }
      return
    }

    return {
      error_message,
      checkoutUserInfo,
      nickname,
      realname,
      gender,
      mobilePhone,
      college,
      qqAccount,
      weChatAccount,
      enrollmentYear,
      user_info_upload
    }
  }
}
</script>

<style scoped>
.error-message {
  white-space: pre-line;
}
</style>