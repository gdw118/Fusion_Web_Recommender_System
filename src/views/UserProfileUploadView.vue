<template>
  <div
    class="min-h-screen bg-gradient-to-br from-indigo-50 via-blue-50 to-purple-50 relative overflow-hidden"
  >
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

    <NavBar />

    <div class="py-12 px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="max-w-5xl mx-auto">
        <!-- 页面标题 -->
        <div class="mb-8 text-center">
          <h1
            class="text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-indigo-600 to-blue-500"
          >
            编辑个人档案
          </h1>
          <p class="mt-3 text-gray-600 text-lg">完善您的个人信息，展示您的技能和荣誉</p>
        </div>

        <form
          @submit.prevent="submitForm"
          class="backdrop-blur-lg bg-white/70 shadow-2xl rounded-2xl overflow-hidden border border-white/50"
        >
          <!-- 基本信息部分 -->
          <div class="p-8 border-b border-gray-200/70">
            <h2
              class="text-xl font-semibold text-indigo-700 mb-6 pb-2 border-b-2 border-indigo-500 inline-block flex items-center"
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
                  d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"
                />
              </svg>
              基本信息
            </h2>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-6">
              <div>
                <label class="block text-sm font-medium text-indigo-700 mb-1">
                  <span class="text-red-500">*</span> 手机号码
                </label>
                <input
                  type="text"
                  v-model="user_profile_info.user_info.mobile_phone"
                  name="mobile_phone"
                  id="mobile_phone"
                  class="block w-full rounded-xl border-0 py-3 px-4 text-gray-900 shadow-sm ring-1 ring-inset ring-indigo-200 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                  required
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-indigo-700 mb-1">QQ号码</label>
                <input
                  type="text"
                  v-model="user_profile_info.qq_number"
                  name="qq_number"
                  id="qq_number"
                  class="block w-full rounded-xl border-0 py-3 px-4 text-gray-900 shadow-sm ring-1 ring-inset ring-indigo-200 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-indigo-700 mb-1">微信号码</label>
                <input
                  type="text"
                  v-model="user_profile_info.wechat_number"
                  name="wechat_number"
                  id="wechat_number"
                  class="block w-full rounded-xl border-0 py-3 px-4 text-gray-900 shadow-sm ring-1 ring-inset ring-indigo-200 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                />
              </div>
            </div>
          </div>

          <!-- 个人介绍部分 -->
          <div
            class="p-8 border-b border-gray-200/70 bg-gradient-to-r from-blue-50/50 to-indigo-50/50"
          >
            <label
              class="text-xl font-semibold text-indigo-700 mb-6 pb-2 border-b-2 border-indigo-500 inline-block flex items-center"
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
                  d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
                />
              </svg>
              <span class="text-red-500">*</span> 个人介绍
            </label>
            <textarea
              id="introduction"
              v-model="user_profile_info.introduction"
              name="introduction"
              class="py-3 px-4 min-h-[200px] block w-full rounded-xl border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-indigo-200 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
              required
              placeholder="介绍一下自己的能力和特长..."
            />
            <p class="mt-2 text-sm text-indigo-600 flex items-center">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-4 w-4 mr-1"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              详细介绍您的背景、兴趣和专业能力，帮助他人更好地了解您
            </p>
          </div>

          <!-- 技能列表部分 -->
          <div class="p-8 border-b border-gray-200/70">
            <h2
              class="text-xl font-semibold text-indigo-700 mb-6 pb-2 border-b-2 border-indigo-500 inline-block flex items-center"
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
                  d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"
                />
              </svg>
              技能列表
            </h2>

            <!-- 已添加的技能 -->
            <div class="mb-6">
              <div
                v-if="Object.keys(groupedSkills).length > 0"
                class="grid grid-cols-1 md:grid-cols-2 gap-4"
              >
                <div
                  v-for="(skills, category) in groupedSkills"
                  :key="category"
                  class="backdrop-blur-md bg-gradient-to-br from-white/60 to-indigo-50/60 rounded-xl p-5 border border-white/50 shadow-lg"
                >
                  <h3
                    class="text-sm font-semibold text-indigo-700 mb-3 pb-1 border-b border-indigo-100 flex items-center"
                  >
                    <span class="w-2 h-2 bg-indigo-500 rounded-full mr-2"></span>
                    {{ category }}
                  </h3>
                  <div
                    v-for="skill in skills"
                    :key="skill.skill"
                    class="mb-2 flex items-center justify-between bg-white/70 backdrop-blur-sm rounded-lg p-3 shadow-sm hover:shadow-md transition-all duration-300 border border-indigo-100/50"
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
                      <button
                        type="button"
                        @click="
                          removeSkill(
                            user_profile_info.user_skills.findIndex(
                              (s) => s.skill === skill.skill && s.category === skill.category
                            )
                          )
                        "
                        class="text-gray-400 hover:text-red-500 transition-colors p-1 rounded-full hover:bg-red-50"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          class="h-4 w-4"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke="currentColor"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
                          />
                        </svg>
                      </button>
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
                <p class="text-indigo-500 font-medium">暂无技能信息，请使用下方表单添加技能</p>
              </div>
            </div>

            <!-- 添加技能表单 -->
            <div
              class="backdrop-blur-md bg-gradient-to-r from-blue-50/60 to-indigo-50/60 rounded-xl p-6 border border-white/50 shadow-lg"
            >
              <h3
                class="text-sm font-medium text-indigo-700 mb-4 pb-2 border-b border-indigo-100 flex items-center"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4 mr-2"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M12 6v6m0 0v6m0-6h6m-6 0H6"
                  />
                </svg>
                添加新技能
              </h3>
              <div class="flex flex-wrap items-center gap-3">
                <div class="w-full md:w-auto">
                  <label class="block text-xs font-medium text-indigo-600 mb-1">技能分类</label>
                  <select
                    v-model="selectedCategory"
                    @change="onCategoryChange"
                    class="block w-full rounded-lg border-0 py-2 pl-3 pr-10 text-gray-900 ring-1 ring-inset ring-indigo-200 focus:ring-2 focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                  >
                    <option value="" disabled>选择分类</option>
                    <option v-for="category in skillCategories" :key="category" :value="category">
                      {{ category }}
                    </option>
                  </select>
                </div>

                <div class="w-full md:w-auto">
                  <label class="block text-xs font-medium text-indigo-600 mb-1">具体技能</label>
                  <select
                    v-model="selectedSkill"
                    class="block w-full rounded-lg border-0 py-2 pl-3 pr-10 text-gray-900 ring-1 ring-inset ring-indigo-200 focus:ring-2 focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                    :disabled="!selectedCategory"
                  >
                    <option value="" disabled>选择技能</option>
                    <option v-for="skill in availableSkills" :key="skill" :value="skill">
                      {{ skill }}
                    </option>
                  </select>
                </div>

                <div class="w-full md:w-auto">
                  <label class="block text-xs font-medium text-indigo-600 mb-1">熟练程度</label>
                  <select
                    v-model="selectedProficiency"
                    class="block w-full rounded-lg border-0 py-2 pl-3 pr-10 text-gray-900 ring-1 ring-inset ring-indigo-200 focus:ring-2 focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                  >
                    <option value="" disabled>选择熟练度</option>
                    <option v-for="level in proficiencyLevels" :key="level" :value="level">
                      {{ level }}
                    </option>
                  </select>
                </div>

                <div class="w-full md:w-auto md:self-end md:mt-5">
                  <button
                    @click="addSkill"
                    type="button"
                    class="w-full inline-flex items-center justify-center px-4 py-2 text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                  >
                    <svg
                      class="h-4 w-4 mr-1.5"
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
            </div>
          </div>

          <!-- 荣誉列表部分 -->
          <div class="p-8 border-b border-gray-200/70">
            <h2
              class="text-xl font-semibold text-indigo-700 mb-6 pb-2 border-b-2 border-indigo-500 inline-block flex items-center"
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
                  d="M15.172 7l-6.586 6.586a2 2 0 102.828 2.828l6.586-6.586a2 2 0 10-2.828-2.828z"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M12 3C7.582 3 4 4.79 4 7s3.582 4 8 4 8-1.79 8-4-3.582-4-8-4z"
                />
              </svg>
              荣誉列表
            </h2>

            <!-- 已添加的荣誉 -->
            <div class="mb-6">
              <div
                v-if="
                  user_profile_info.honors &&
                  user_profile_info.honors.length > 0 &&
                  user_profile_info.honors[0]
                "
                class="space-y-3"
              >
                <div
                  v-for="(honor, index) in user_profile_info.honors"
                  :key="index"
                  v-show="honor && honor.trim()"
                  class="flex items-center justify-between backdrop-blur-md bg-white/70 rounded-lg p-4 border border-indigo-100/50 shadow-sm hover:shadow-md transition-all duration-300"
                >
                  <div class="flex items-center">
                    <div
                      class="flex-shrink-0 w-10 h-10 bg-indigo-100 rounded-full flex items-center justify-center mr-3"
                    >
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        class="h-5 w-5 text-indigo-600"
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
                    <span class="text-gray-800 font-medium">{{ honor }}</span>
                  </div>
                  <button
                    type="button"
                    @click="user_profile_info.honors.splice(index, 1)"
                    class="text-gray-400 hover:text-red-500 transition-colors p-1 rounded-full hover:bg-red-50"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-4 w-4"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
                      />
                    </svg>
                  </button>
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
                    d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"
                  />
                </svg>
                <p class="text-indigo-500 font-medium">暂无荣誉信息，请使用下方表单添加荣誉</p>
              </div>
            </div>

            <!-- 添加荣誉表单 -->
            <div
              class="backdrop-blur-md bg-gradient-to-r from-blue-50/60 to-indigo-50/60 rounded-xl p-6 border border-white/50 shadow-lg"
            >
              <h3
                class="text-sm font-medium text-indigo-700 mb-4 pb-2 border-b border-indigo-100 flex items-center"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4 mr-2"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M12 6v6m0 0v6m0-6h6m-6 0H6"
                  />
                </svg>
                添加新荣誉
              </h3>
              <div class="flex items-center gap-3">
                <div class="flex-grow">
                  <input
                    type="text"
                    id="honors"
                    v-model="honor"
                    name="honors"
                    placeholder="输入您获得的荣誉..."
                    class="block w-full rounded-lg border-0 py-3 px-4 text-gray-900 shadow-sm ring-1 ring-inset ring-indigo-200 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 text-sm backdrop-blur-sm bg-white/50"
                  />
                </div>
                <button
                  @click="add_honor"
                  type="button"
                  class="inline-flex items-center px-4 py-3 text-sm font-medium rounded-lg text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition-all duration-300"
                >
                  <svg
                    class="h-4 w-4 mr-1.5"
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
                  添加荣誉
                </button>
              </div>
            </div>
          </div>

          <!-- 表单按钮 -->
          <div
            class="p-8 bg-gradient-to-r from-indigo-50/50 to-blue-50/50 flex justify-end space-x-4"
          >
            <router-link
              type="button"
              class="inline-flex items-center px-6 py-3 text-base font-medium rounded-xl border border-gray-300 shadow-sm text-indigo-700 bg-white/80 backdrop-blur-sm hover:bg-white hover:text-indigo-800 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition-all duration-300"
              :to="{
                name: 'userprofile',
                params: { user_id: store.state.user.user_info.user_id }
              }"
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
                  d="M6 18L18 6M6 6l12 12"
                />
              </svg>
              取消
            </router-link>

            <button
              type="submit"
              class="inline-flex items-center px-6 py-3 border border-transparent text-base font-medium rounded-xl shadow-sm text-white bg-gradient-to-r from-indigo-600 to-blue-500 hover:from-indigo-700 hover:to-blue-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition-all duration-300 transform hover:scale-105"
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
                  d="M5 13l4 4L19 7"
                />
              </svg>
              保存修改
            </button>
          </div>
        </form>
      </div>
    </div>
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