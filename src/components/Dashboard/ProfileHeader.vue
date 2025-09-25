<template>
  <!-- Warehouse Management Header -->
  <div class="bg-primary/15 border-b p-2 border-gray-200">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo -->
        <div class="flex items-center space-x-2">
          <img
            src="@/assets/images/logo.png"
            alt="Warehouse Portal"
            class="h-9 w-auto transition-transform duration-200 hover:scale-105"
          />
        </div>

        <!-- Right side items -->
        <div class="flex items-center space-x-4">
          <!-- Notifications -->
          <div class="relative group">
            <button
              class="relative p-2.5 text-white transition-all duration-200 bg-gradient-to-r from-primary to-rose-600 rounded-xl shadow-md hover:shadow-lg transform hover:-translate-y-0.5 group"
            >
              <Icon
                name="ph:bell"
                class="text-xl transition-transform group-hover:scale-110"
              />
              <span
                class="absolute top-1.5 right-1.5 bg-red-500 rounded-full w-2.5 h-2.5 border-2 border-white shadow-sm animate-pulse"
              ></span>
            </button>

            <!-- Notifications Dropdown -->
            <div
              class="absolute right-0 mt-2 w-80 bg-white rounded-lg shadow-xl border border-gray-200 z-50 opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-200 transform group-hover:translate-y-0 translate-y-2"
            >
              <div class="p-4 border-b border-gray-100">
                <h3 class="font-semibold text-gray-800">Notifications</h3>
                <span class="text-xs text-gray-500">5 unread</span>
              </div>
              <div class="max-h-96 overflow-y-auto">
                <div
                  class="p-3 border-b border-gray-100 hover:bg-gray-50 cursor-pointer"
                >
                  <div class="flex items-start gap-3">
                    <div
                      class="w-8 h-8 bg-blue-100 rounded-full flex items-center justify-center"
                    >
                      <Icon name="ph:package" class="text-blue-600 text-sm" />
                    </div>
                    <div class="flex-1">
                      <p class="text-sm font-medium text-gray-800">
                        New inventory received
                      </p>
                      <p class="text-xs text-gray-500">
                        15 items added to stock
                      </p>
                      <span class="text-xs text-blue-600">2 minutes ago</span>
                    </div>
                  </div>
                </div>
                <div
                  class="p-3 border-b border-gray-100 hover:bg-gray-50 cursor-pointer"
                >
                  <div class="flex items-start gap-3">
                    <div
                      class="w-8 h-8 bg-green-100 rounded-full flex items-center justify-center"
                    >
                      <Icon
                        name="ph:shipping-container"
                        class="text-green-600 text-sm"
                      />
                    </div>
                    <div class="flex-1">
                      <p class="text-sm font-medium text-gray-800">
                        Shipment dispatched
                      </p>
                      <p class="text-xs text-gray-500">
                        Order #WH-7842 shipped
                      </p>
                      <span class="text-xs text-blue-600">1 hour ago</span>
                    </div>
                  </div>
                </div>
                <div
                  class="p-3 border-b border-gray-100 hover:bg-gray-50 cursor-pointer"
                >
                  <div class="flex items-start gap-3">
                    <div
                      class="w-8 h-8 bg-yellow-100 rounded-full flex items-center justify-center"
                    >
                      <Icon name="ph:warning" class="text-yellow-600 text-sm" />
                    </div>
                    <div class="flex-1">
                      <p class="text-sm font-medium text-gray-800">
                        Low stock alert
                      </p>
                      <p class="text-xs text-gray-500">
                        Product #P-8921 running low
                      </p>
                      <span class="text-xs text-blue-600">3 hours ago</span>
                    </div>
                  </div>
                </div>
              </div>
              <div class="p-3 border-t border-gray-100">
                <button
                  class="w-full text-center text-sm text-blue-600 hover:text-blue-700 font-medium"
                >
                  View all notifications
                </button>
              </div>
            </div>
          </div>

          <!-- Messages -->
          <button
            class="relative p-2.5 text-white transition-all duration-200 bg-gradient-to-r from-blue-500 to-blue-600 rounded-xl shadow-md hover:shadow-lg transform hover:-translate-y-0.5 group"
          >
            <Icon
              name="ph:chat-circle"
              class="text-xl transition-transform group-hover:scale-110"
            />
            <span
              class="absolute top-1.5 right-1.5 bg-blue-500 rounded-full w-2.5 h-2.5 border-2 border-white shadow-sm animate-pulse"
            ></span>
          </button>

          <!-- User menu -->
          <div class="relative group">
            <button
              class="flex items-center space-x-3 p-2 rounded-lg transition-all duration-200"
            >
              <div
                class="w-10 h-10 rounded-full bg-gradient-to-br from-blue-400 to-indigo-600 flex items-center justify-center shadow-sm border border-blue-300"
              >
                <span class="text-white font-semibold text-sm">JD</span>
              </div>
              <div class="hidden md:block text-left">
                <p class="text-sm font-medium text-gray-800">John Doe</p>
                <p class="text-xs text-rose-800">Warehouse Manager</p>
              </div>
              <Icon name="ph:caret-down" class="text-gray-400 text-lg" />
            </button>

            <!-- User Dropdown -->
            <div
              class="absolute right-0 mt-2 w-48 bg-white rounded-lg shadow-xl border border-gray-200 z-50 opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-200 transform group-hover:translate-y-0 translate-y-2"
            >
              <div class="p-4 border-b border-gray-100">
                <p class="text-sm font-medium text-gray-800">John Doe</p>
                <p class="text-xs text-gray-500">john.doe@warehouse.com</p>
              </div>
              <div class="p-2">
                <router-link
                  to="/profile"
                  class="flex items-center gap-2 px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 rounded-md"
                >
                  <Icon name="ph:user" class="text-lg" />
                  Profile
                </router-link>
                <router-link
                  to="/settings"
                  class="flex items-center gap-2 px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 rounded-md"
                >
                  <Icon name="ph:gear" class="text-lg" />
                  Settings
                </router-link>
                <router-link
                  to="/help"
                  class="flex items-center gap-2 px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 rounded-md"
                >
                  <Icon name="ph:question" class="text-lg" />
                  Help & Support
                </router-link>
              </div>
              <div class="p-2 border-t border-gray-100">
                <button
                  class="flex items-center gap-2 w-full px-3 py-2 text-sm text-red-600 hover:bg-red-50 rounded-md"
                >
                  <Icon name="ph:sign-out" class="text-lg" />
                  Sign Out
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
