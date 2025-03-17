<template>
  <section class="flex flex-col md:flex-row h-screen items-center">
    <div class="hidden lg:block w-full md:w-1/2 xl:w-2/3 h-screen">
      <img
        src="../assets/img/fusion-sky-skyscrapers.png"
        alt=""
        class="w-full h-full object-cover"
      />
    </div>

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
        <h1 class="text-2xl font-bold text-center text-gray-800 mb-4">登录</h1>
        <p class="text-center text-gray-600 mb-8">使用您的Fusion账号</p>

        <form class="mt-6 bg-white p-8 rounded-lg shadow-md" @submit.prevent="login">
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
                v-model="username"
                type="text"
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
                v-model="password"
                type="password"
                placeholder="密码"
                class="w-full pl-10 pr-4 py-3 border-b border-gray-300 focus:border-blue-500 focus:outline-none bg-transparent transition-colors duration-200"
              />
            </div>
            <p class="text-xs text-gray-500 mt-1 ml-1">8-16位字符</p>
          </div>

          <div class="text-right mb-4">
            <a
              href="#"
              class="text-sm font-medium text-blue-600 hover:text-blue-800 transition-colors duration-200"
              >忘记密码?</a
            >
          </div>

          <div class="bg-red-50 border border-red-200 rounded-md p-3 mb-6" v-if="error_message">
            <p class="text-sm text-red-600">{{ error_message }}</p>
          </div>

          <div class="flex justify-between items-center mt-8">
            <router-link
              :to="{ name: 'register' }"
              class="text-sm font-medium text-blue-600 hover:text-blue-800 transition-colors duration-200"
              >注册账号</router-link
            >
            <button
              type="submit"
              class="px-6 py-2.5 bg-blue-600 hover:bg-blue-700 focus:bg-blue-700 text-white font-medium rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-all duration-200 transform hover:scale-105"
              @click="login"
            >
              登录
            </button>
          </div>
        </form>

        <div class="mt-8 text-center">
          <button
            type="button"
            class="inline-flex items-center px-4 py-2.5 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 transition-all duration-200"
          >
            <svg
              class="h-5 w-5 mr-2"
              viewBox="0 0 24 24"
              width="24"
              height="24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <g transform="matrix(1, 0, 0, 1, 27.009001, -39.238998)">
                <path
                  fill="#4285F4"
                  d="M -3.264 51.509 C -3.264 50.719 -3.334 49.969 -3.454 49.239 L -14.754 49.239 L -14.754 53.749 L -8.284 53.749 C -8.574 55.229 -9.424 56.479 -10.684 57.329 L -10.684 60.329 L -6.824 60.329 C -4.564 58.239 -3.264 55.159 -3.264 51.509 Z"
                />
                <path
                  fill="#34A853"
                  d="M -14.754 63.239 C -11.514 63.239 -8.804 62.159 -6.824 60.329 L -10.684 57.329 C -11.764 58.049 -13.134 58.489 -14.754 58.489 C -17.884 58.489 -20.534 56.379 -21.484 53.529 L -25.464 53.529 L -25.464 56.619 C -23.494 60.539 -19.444 63.239 -14.754 63.239 Z"
                />
                <path
                  fill="#FBBC05"
                  d="M -21.484 53.529 C -21.734 52.809 -21.864 52.039 -21.864 51.239 C -21.864 50.439 -21.724 49.669 -21.484 48.949 L -21.484 45.859 L -25.464 45.859 C -26.284 47.479 -26.754 49.299 -26.754 51.239 C -26.754 53.179 -26.284 54.999 -25.464 56.619 L -21.484 53.529 Z"
                />
                <path
                  fill="#EA4335"
                  d="M -14.754 43.989 C -12.984 43.989 -11.404 44.599 -10.154 45.789 L -6.734 42.369 C -8.804 40.429 -11.514 39.239 -14.754 39.239 C -19.444 39.239 -23.494 41.939 -25.464 45.859 L -21.484 48.949 C -20.534 46.099 -17.884 43.989 -14.754 43.989 Z"
                />
              </g>
            </svg>
            使用Google登录
          </button>
        </div>

        <p class="text-sm text-gray-500 mt-12 text-center">
          &copy; 2023 SHNU CoderSky - All Rights Reserved.
        </p>
      </div>
    </div>
  </section>
</template>

<script>
import { ref } from 'vue'
import { useStore } from 'vuex'
import router from '@/router/index'

export default {
  name: 'LoginView',
  components: {},
  setup() {
    const store = useStore()
    let username = ref('')
    let password = ref('')
    let error_message = ref('')

    const checkInput = () => {
      const username_len = username.value.length
      const password_len = password.value.length
      if (username_len >= 6 && username_len <= 32 && password_len >= 8 && password_len <= 16) {
        return true
      }
      return false
    }

    const login = () => {
      error_message.value = ''
      if (!checkInput()) {
        // 换行 输出用户名为 6-32 位，密码为 8-16 位
        error_message.value = '用户名或密码格式错误\n用户名为 6 - 32 位，密码为 8 - 16 位'
        password.value = ''
        return
      }
      store.dispatch('login', {
        username: username.value,
        password: password.value,
        success() {
          router.push({ name: 'home' })
        },
        error() {
          error_message.value = '用户名或密码错误'
        }
      })
    }

    return {
      username,
      password,
      error_message,
      login
    }
  }
}
</script>

<style scoped>
.error-message {
  white-space: pre-line;
}
</style>
