<script setup>
import { ref, inject, watch } from "vue";
const setting = inject("setting");
import { useRoute } from "vue-router";
const route = useRoute();

const props = defineProps({
  text: {
    type: Boolean,
    default: true,
  },
});

// Sidebar collapse state
const isCollapsed = ref(false);

// Warehouse menu open state
const isCmsLinks = ref(false);

// Keep Warehouse menu open if the route matches its children
const cmsRoutes = [
  "/dashboard/stock-management",
  "/dashboard/tracking-inventory",
  "/dashboard/shipping-labels",
  "/dashboard/return-management",
];

watch(
  () => route.path,
  (newPath) => {
    isCmsLinks.value = cmsRoutes.includes(newPath);
  },
  { immediate: true } // run on first load
);

// Toggle sidebar collapse
const toggleSidebar = () => {
  isCollapsed.value = !isCollapsed.value;
};
</script>

<template>
  <nav
    class="bg-white rounded-lg p-4 relative transition-all duration-300"
    :class="isCollapsed ? 'w-20' : 'w-64'"
  >
    <!-- Toggle Button -->
    <button
      @click="toggleSidebar"
      class="absolute -right-4 top-7 p-1 rounded-full shadow-md transition-colors z-10"
      :class="[
        'hover:bg-blue-600 hover:text-white',
        isCollapsed ? 'bg-blue-600 text-white' : 'bg-blue-200 text-blue-700',
      ]"
    >
      <Icon
        :name="isCollapsed ? 'ph:caret-right' : 'ph:caret-left'"
        class="text-lg"
      />
    </button>

    <ul class="space-y-1">
      <!-- Dashboard -->
      <li>
        <router-link
          to="/dashboard"
          class="w-full px-4 py-3 text-left flex items-center rounded-xl transition-all duration-200 group"
          :class="[
            $route.path === '/dashboard'
              ? 'bg-gradient-to-r from-blue-50 to-blue-100 border-l-4 border-blue-500 text-blue-700 font-semibold shadow-sm'
              : 'text-gray-900 hover:bg-gray-50 hover:text-blue-700 font-medium hover:translate-x-1',
            isCollapsed ? 'justify-center px-2' : 'justify-start gap-3',
          ]"
        >
          <Icon
            name="ph:gauge"
            class="text-xl text-blue-500 group-hover:scale-110 transition-transform flex-shrink-0"
          />
          <span
            class="transition-all duration-200 overflow-hidden whitespace-nowrap"
            :class="isCollapsed ? 'w-0 opacity-0' : 'w-auto opacity-100 ml-3'"
            >Dashboard</span
          >
          <div
            class="w-2 h-2 rounded-full bg-blue-500 ml-11 flex-shrink-0"
            v-if="$route.path === '/dashboard' && !isCollapsed"
          ></div>
        </router-link>
      </li>

      <!-- Inventory -->
      <li>
        <router-link
          to="/dashboard/inventory"
          class="w-full px-4 py-3 text-left flex items-center rounded-xl transition-all duration-200 group"
          :class="[
            $route.path.startsWith('/dashboard/inventory')
              ? 'bg-gradient-to-r from-green-50 to-green-100 border-l-4 border-green-500 text-green-700 font-semibold shadow-sm'
              : 'text-gray-900 hover:bg-gray-50 hover:text-green-700 font-medium hover:translate-x-1',
            isCollapsed ? 'justify-center px-2' : 'justify-start gap-3',
          ]"
        >
          <Icon
            name="ph:package"
            class="text-xl text-green-500 group-hover:scale-110 transition-transform flex-shrink-0"
          />
          <span
            class="transition-all duration-200 overflow-hidden whitespace-nowrap"
            :class="isCollapsed ? 'w-0 opacity-0' : 'w-auto opacity-100 ml-3'"
            >Inventory</span
          >
          <div
            class="w-2 h-2 rounded-full bg-green-500 flex-shrink-0 ml-14"
            v-if="
              $route.path.startsWith('/dashboard/inventory') && !isCollapsed
            "
          ></div>
        </router-link>
      </li>

      <!-- Orders -->
      <li>
        <router-link
          to="/dashboard/orders"
          class="w-full px-4 py-3 text-left flex items-center rounded-xl transition-all duration-200 group"
          :class="[
            $route.path.startsWith('/dashboard/orders')
              ? 'bg-gradient-to-r from-orange-50 to-orange-100 border-l-4 border-orange-500 text-orange-700 font-semibold shadow-sm'
              : 'text-gray-900 hover:text-orange-600 font-medium hover:translate-x-1',
            isCollapsed ? 'justify-center px-2' : 'justify-start gap-3',
          ]"
        >
          <Icon
            name="ph:shopping-cart"
            class="text-xl text-orange-500 group-hover:scale-110 transition-transform flex-shrink-0"
          />
          <span
            class="transition-all duration-200 overflow-hidden whitespace-nowrap"
            :class="isCollapsed ? 'w-0 opacity-0' : 'w-auto opacity-100 ml-3'"
            >Orders</span
          >
          <div
            class="w-2 h-2 rounded-full bg-orange-500 flex-shrink-0 ml-11"
            v-if="$route.path.startsWith('/dashboard/orders') && !isCollapsed"
          ></div>
        </router-link>
      </li>

      <!-- Revenue -->
      <li>
        <router-link
          to="/dashboard/revenue"
          class="w-full px-4 py-3 text-left flex items-center rounded-xl transition-all duration-200 group"
          :class="[
            $route.path.startsWith('/dashboard/revenue')
              ? 'bg-gradient-to-r from-purple-100 to-purple-200 border-l-4 border-purple-500 text-purple-700 font-semibold shadow-sm'
              : 'text-gray-900 hover:text-purple-600 font-medium hover:translate-x-1',
            isCollapsed ? 'justify-center px-2' : 'justify-start gap-3',
          ]"
        >
          <Icon
            name="ph:currency-dollar"
            class="text-xl text-purple-500 group-hover:scale-110 transition-transform flex-shrink-0"
          />
          <span
            class="transition-all duration-200 overflow-hidden whitespace-nowrap"
            :class="isCollapsed ? 'w-0 opacity-0' : 'w-auto opacity-100 ml-3'"
            >Revenue</span
          >
          <div
            class="w-2 h-2 rounded-full bg-purple-500 flex-shrink-0 ml-11"
            v-if="$route.path.startsWith('/dashboard/revenue') && !isCollapsed"
          ></div>
        </router-link>
      </li>

      <!-- Warehouse Management -->
      <li>
        <div
          class="w-full px-4 py-3 text-left flex items-center rounded-xl transition-all duration-200 cursor-pointer group hover:bg-gray-50"
          :class="[
            { 'bg-gray-50': isCmsLinks },
            isCollapsed ? 'justify-center px-2' : 'justify-start gap-3',
          ]"
          @click="isCmsLinks = !isCmsLinks"
        >
          <Icon
            name="ph:warehouse"
            class="text-xl text-indigo-500 group-hover:scale-110 transition-transform flex-shrink-0"
          />
          <span
            class="transition-all duration-200 overflow-hidden whitespace-nowrap font-medium"
            :class="[
              isCollapsed ? 'w-0 opacity-0' : 'w-auto opacity-100 ml-3',
              {
                'text-gray-900 group-hover:text-indigo-900': !isCmsLinks,
                'text-indigo-900': isCmsLinks,
              },
            ]"
          >
            Warehouse
          </span>
          <Icon
            v-if="!isCollapsed"
            name="ph:caret-right"
            class="text-lg text-gray-400 transition-transform duration-200 flex-shrink-0"
            :class="{ 'rotate-90': isCmsLinks }"
          />
        </div>
        <div
          class="overflow-hidden transition-all duration-300 ease-in-out"
          :class="{ 'max-h-0': !isCmsLinks, 'max-h-96': isCmsLinks }"
          v-if="!isCollapsed"
        >
          <ul class="pl-5 space-y-1 mt-1">
            <li>
              <router-link
                to="/dashboard/stock-management"
                class="flex items-center gap-2 px-4 py-3 rounded-lg text-sm transition-all duration-200 hover:bg-blue-50 hover:text-blue-700"
                :class="{
                  'bg-blue-50 text-blue-700':
                    $route.path === '/dashboard/stock-management',
                }"
              >
                <Icon name="ph:package" class="text-lg text-blue-700" />
                Stock Management
              </router-link>
            </li>
            <li>
              <router-link
                to="/dashboard/tracking-inventory"
                class="flex items-center gap-2 px-4 py-3 rounded-lg text-sm transition-all duration-200 hover:bg-green-50 hover:text-green-700"
                :class="{
                  'bg-green-50 text-green-700':
                    $route.path === '/dashboard/tracking-inventory',
                }"
              >
                <Icon name="ph:binoculars" class="text-lg text-green-700" />
                Inventory Tracking
              </router-link>
            </li>
            <li>
              <router-link
                to="/dashboard/shipping-labels"
                class="flex items-center gap-2 px-4 py-3 rounded-lg text-sm transition-all duration-200 hover:bg-orange-50 hover:text-orange-700"
                :class="{
                  'bg-orange-50 text-orange-700':
                    $route.path === '/dashboard/shipping-labels',
                }"
              >
                <Icon
                  name="ph:shipping-container"
                  class="text-lg text-orange-700"
                />
                Shipping Labels
              </router-link>
            </li>
            <li>
              <router-link
                to="/dashboard/return-management"
                class="flex items-center gap-2 px-4 py-3 rounded-lg text-sm transition-all duration-200 hover:bg-red-50 hover:text-red-700"
                :class="{
                  'bg-red-50 text-red-700':
                    $route.path === '/dashboard/return-management',
                }"
              >
                <Icon name="ph:arrow-u-up-left" class="text-lg text-red-700" />
                Return Management
              </router-link>
            </li>
          </ul>
        </div>
      </li>

      <!-- Settings -->
      <li>
        <router-link
          to="/dashboard/settings"
          class="w-full px-4 py-3 text-left flex items-center rounded-xl transition-all duration-200 group"
          :class="[
            $route.path.startsWith('/dashboard/settings')
              ? 'bg-gradient-to-r from-rose-50 to-rose-200 border-l-4 border-rose-500 text-rose-700 font-semibold shadow-sm'
              : 'text-gray-900 hover:bg-rose-50 hover:text-rose-600 font-medium hover:translate-x-1',
            isCollapsed ? 'justify-center px-2' : 'justify-start gap-3',
          ]"
        >
          <Icon
            name="ph:gear"
            class="text-xl text-rose-500 group-hover:scale-110 transition-transform flex-shrink-0"
          />
          <span
            class="transition-all duration-200 overflow-hidden whitespace-nowrap"
            :class="isCollapsed ? 'w-0 opacity-0' : 'w-auto opacity-100 ml-3'"
            >Settings</span
          >
          <div
            class="w-2 h-2 rounded-full bg-rose-500 flex-shrink-0 ml-11"
            v-if="$route.path.startsWith('/dashboard/settings') && !isCollapsed"
          ></div>
        </router-link>
      </li>
    </ul>
  </nav>
</template>
