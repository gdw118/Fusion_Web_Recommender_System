<template>
  <div>
    <header
      class="w-full"
      :class="[
        isUserProfilePage
          ? [
              'fixed top-0 z-50 transition-all duration-300',
              scrolled ? 'h-16 bg-white/80 backdrop-blur-lg shadow-lg' : 'h-24 bg-white'
            ]
          : 'h-24 bg-white shadow fixed top-0 z-50'
      ]"
    >
      <div
        class="w-full h-full"
        :class="[
          isUserProfilePage
            ? ['px-6 lg:px-8 transition-all duration-300', scrolled ? 'py-2' : 'py-4']
            : 'pb-2 pl-10 pr-2 pt-4 sm:pl-20'
        ]"
      >
        <div class="flex items-center justify-between h-full">
          <!-- 左边区域 -->
          <div
            class="text-center sm:text-left"
            :class="{
              'transition-all duration-300 transform scale-90': isUserProfilePage && scrolled
            }"
          >
            <h1
              class="text-2xl font-bold sm:text-3xl"
              :class="{ 'text-xl': isUserProfilePage && scrolled }"
            >
              {{ isUserProfilePage && scrolled ? 'Fusion' : 'Welcome to Fusion!' }}
            </h1>

            <p
              v-show="!isUserProfilePage || !scrolled"
              class="mt-1.5 text-sm text-gray-500"
              :class="{ 'transition-opacity duration-300': isUserProfilePage }"
            >
              This is a university competition team platform 🎉
            </p>
          </div>

          <!-- 右边区域 -->
          <div class="flex gap-4 justify-center sm:justify-end">
            <div v-if="$store.state.user.is_login">
              <!-- 已登录状态，显示用户下拉菜单 -->
              <div class="flex-none">
                <ul class="menu menu-horizontal pl-10">
                  <li>
                    <details class="group [&_summary::-webkit-details-marker]:hidden">
                      <summary
                        class="group flex items-center justify-between rounded-lg px-2 py-2 text-gray-500 hover:bg-gray-100 hover:text-gray-700"
                      >
                        <img
                          v-if="$store.state.user.user_info.avatar_url != ''"
                          :src="$store.state.user.user_info.avatar_url"
                          class="h-10 w-10 rounded-full object-cover"
                        />
                        <img
                          v-else
                          src="../assets/img/defaultAvatar.svg"
                          class="h-10 w-10 rounded-full object-cover"
                        />
                        <p
                          class="ms-2 text-left text-xs block mr-2 pb-1"
                          :class="{ hidden: isUserProfilePage && scrolled }"
                        >
                          <span class="block font-medium text-base">
                            <span class="align-middle">{{
                              $store.state.user.user_info.nickname
                            }}</span>

                            <!-- 当 gender 为 1 时，仅显示male图标 -->
                            <img
                              v-if="$store.state.user.user_info.gender == 1"
                              src="../assets/img/male.svg"
                              class="inline-block ml-1 h-4 w-4 align-middle"
                            />

                            <!-- 当 gender 不为 1 时，显示female图标 -->
                            <img
                              v-else
                              src="../assets/img/female.svg"
                              class="inline-block ml-1 h-4 w-4 align-middle"
                            />
                          </span>
                          <span class="text-gray-600 text-xs">
                            {{ $store.state.user.user_info.college }}
                          </span>
                        </p>
                      </summary>
                      <ul class="dropdown space-y-1 px-4 w-36 right-0">
                        <li>
                          <router-link
                            :to="{ name: 'home' }"
                            class="flex items-center gap-2 rounded-lg px-4 py-2 text-gray-700"
                          >
                            <img src="../assets/img/home.svg" class="w-5 h-5" />
                            <span class="text-sm font-medium"> Home </span>
                          </router-link>
                        </li>

                        <li>
                          <router-link
                            :to="{
                              name: 'userprofile',
                              params: { user_id: store.state.user.user_info.user_id }
                            }"
                            class="flex items-center gap-2 rounded-lg px-4 py-2 text-gray-700"
                          >
                            <img src="../assets/img/profile.svg" class="w-5 h-5" />
                            <span class="text-sm font-medium">Profile</span>
                          </router-link>
                        </li>

                        <li>
                          <div
                            @click="logout"
                            class="flex items-center gap-2 rounded-lg px-4 py-2 text-gray-700"
                          >
                            <img src="../assets/img/exit.svg" class="w-5 h-5" />
                            <span class="text-sm font-medium"> Logout </span>
                          </div>
                        </li>
                      </ul>
                    </details>
                  </li>
                </ul>
              </div>
            </div>
            <router-link :to="{ name: 'login' }" style="height: 72px" v-else>
              <!-- 未登录状态，显示登录按钮 -->
              <button class="btn btn-md sm:btn-lg btn-link text-black pt-6 sm:pt-2">Login</button>
            </router-link>
          </div>
        </div>
      </div>
    </header>
    <!-- 添加占位符以防止内容重叠 -->
    <div class="h-24"></div>
  </div>
</template>

<script>
import { useStore } from 'vuex'
import { useRouter, useRoute } from 'vue-router'
import { web_user_profile_url } from '../constants/constants'
import { ref, onMounted, onUnmounted, computed } from 'vue'

export default {
  setup() {
    const store = useStore()
    const router = useRouter()
    const route = useRoute()
    const scrolled = ref(false)

    // 计算当前是否在用户资料相关页面
    const isUserProfilePage = computed(() => {
      return ['userprofile', 'userprofileupload'].includes(route.name)
    })

    const handleScroll = () => {
      if (isUserProfilePage.value) {
        scrolled.value = window.scrollY > 0
      }
    }

    onMounted(() => {
      if (isUserProfilePage.value) {
        window.addEventListener('scroll', handleScroll)
      }
    })

    onUnmounted(() => {
      if (isUserProfilePage.value) {
        window.removeEventListener('scroll', handleScroll)
      }
    })

    const logout = () => {
      store.commit('logout')
      router.push({ name: 'home' })
    }

    return {
      logout,
      web_user_profile_url,
      store,
      scrolled,
      isUserProfilePage
    }
  }
}
</script>

<style scoped>
</style>
