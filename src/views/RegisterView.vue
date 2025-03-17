<template>
  <section class="bg-gray-50">
    <section class="flex flex-col md:flex-row h-screen items-center">
      <!-- 填写用户名、密码、确认密码 -->
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
          <h1 class="text-2xl font-bold text-center text-gray-800 mb-4">创建账号</h1>
          <p class="text-center text-gray-600 mb-8">注册一个新的Fusion账号</p>

          <form class="mt-6 bg-white p-8 rounded-lg shadow-md" @submit.prevent>
            <div class="mb-6">
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
                  v-model="username"
                  placeholder="用户名"
                  class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                  autofocus
                />
              </div>
              <p class="text-xs text-gray-500 mt-1 ml-1">6-32位字符</p>
            </div>

            <div class="mb-6">
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
                      d="M5 9V7a5 5 0 0110 0v2a2 2 0 012 2v5a2 2 0 01-2 2H5a2 2 0 01-2-2v-5a2 2 0 012-2zm8-2v2H7V7a3 3 0 016 0z"
                      clip-rule="evenodd"
                    />
                  </svg>
                </div>
                <input
                  type="password"
                  v-model="password"
                  placeholder="密码"
                  class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                />
              </div>
              <p class="text-xs text-gray-500 mt-1 ml-1">8-16位字符</p>
            </div>

            <div class="mb-6">
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
                      d="M5 9V7a5 5 0 0110 0v2a2 2 0 012 2v5a2 2 0 01-2 2H5a2 2 0 01-2-2v-5a2 2 0 012-2zm8-2v2H7V7a3 3 0 016 0z"
                      clip-rule="evenodd"
                    />
                  </svg>
                </div>
                <input
                  type="password"
                  v-model="confirm_password"
                  placeholder="确认密码"
                  class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
                />
              </div>
              <p class="text-xs text-gray-500 mt-1 ml-1">请再次输入密码</p>
            </div>

            <div class="bg-red-50 border border-red-200 rounded-md p-3 mb-6" v-if="error_message">
              <p class="text-sm text-red-600">{{ error_message }}</p>
            </div>

            <div class="flex justify-between items-center mt-8">
              <router-link
                :to="{ name: 'login' }"
                class="text-sm font-medium text-blue-600 hover:text-blue-800 transition-colors duration-200"
                >已有账号？登录</router-link
              >
              <button
                type="submit"
                class="px-6 py-2.5 bg-blue-600 hover:bg-blue-700 focus:bg-blue-700 text-white font-medium rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-all duration-200 transform hover:scale-105"
                @click="register"
              >
                注册
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
import { useStore } from 'vuex'

export default {
  setup() {
    const store = useStore()
    // account 内容
    let username = ref('')
    let password = ref('')
    let confirm_password = ref('')
    let error_message = ref('')

    let checkoutUserAccount = () => {
      const username_len = username.value.length
      const password_len = password.value.length

      // 检查输入是否为空
      if (!username.value.trim() || !password.value.trim() || !confirm_password.value.trim()) {
        error_message.value = '用户名、密码或确认密码不能为空'
        password.value = ''
        confirm_password.value = ''
        return false
      } else if (username_len < 6 || username_len > 32 || password_len < 8 || password_len > 16) {
        error_message.value = '用户名或密码格式错误\n用户名为 6 - 32 位，密码为 8 - 16 位'
        password.value = ''
        confirm_password.value = ''
        return false
      } else if (password.value != confirm_password.value) {
        error_message.value = '两次输入的密码不一致'
        password.value = ''
        confirm_password.value = ''
        return false
      } else {
        error_message.value = ''
        return true
      }
    }

    let register = () => {
      error_message.value = ''
      if (checkoutUserAccount()) {
        store.dispatch('register', {
          username: username.value,
          password: password.value,
          error(msg) {
            error_message.value = msg
          }
        })
      }
      return
    }

    return {
      username,
      password,
      confirm_password,
      error_message,
      checkoutUserAccount,
      register
    }
  }
}
</script>

<style scoped>
.error-message {
  white-space: pre-line;
}
</style>