<script setup>
import { ref } from "vue";
</script>

<template>
  <div>
    <!-- Warehouse Dashboard Summary -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
      <!-- Total Inventory -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-blue-500/10 to-blue-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-blue-600/80"
            >
              Total Inventory
            </p>
            <p class="text-3xl font-bold mt-2 text-blue-900">2,847</p>
            <p class="text-xs font-medium mt-2 flex items-center text-blue-600">
              <span class="inline-flex items-center">
                <Icon name="ph:trend-up" class="mr-1" />
                +12% from last week
              </span>
            </p>
          </div>
          <div class="p-3 rounded-xl shadow-md bg-blue-500/20 text-blue-600">
            <Icon name="ph:package" class="text-2xl" />
          </div>
        </div>
      </div>

      <!-- Orders to Process -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-amber-500/10 to-amber-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-amber-600/80"
            >
              Orders to Process
            </p>
            <p class="text-3xl font-bold mt-2 text-amber-900">47</p>
            <p
              class="text-xs font-medium mt-2 flex items-center text-amber-600"
            >
              <span class="inline-flex items-center">
                Pending fulfillment
              </span>
            </p>
          </div>
          <div class="p-3 rounded-xl shadow-md bg-amber-500/20 text-amber-600">
            <Icon name="ph:shopping-cart" class="text-2xl" />
          </div>
        </div>
      </div>

      <!-- Low Stock Alerts -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-red-500/10 to-red-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-red-600/80"
            >
              Low Stock Alerts
            </p>
            <p class="text-3xl font-bold mt-2 text-red-900">12</p>
            <p class="text-xs font-medium mt-2 flex items-center text-red-600">
              <span class="inline-flex items-center">
                Items need restocking
              </span>
            </p>
          </div>
          <div class="p-3 rounded-xl shadow-md bg-red-500/20 text-red-600">
            <Icon name="ph:warning" class="text-2xl" />
          </div>
        </div>
      </div>

      <!-- Today's Shipments -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-emerald-500/10 to-emerald-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-emerald-600/80"
            >
              Today's Shipments
            </p>
            <p class="text-3xl font-bold mt-2 text-emerald-900">28</p>
            <p
              class="text-xs font-medium mt-2 flex items-center text-emerald-600"
            >
              <span class="inline-flex items-center"> Ready for dispatch </span>
            </p>
          </div>
          <div
            class="p-3 rounded-xl shadow-md bg-emerald-500/20 text-emerald-600"
          >
            <Icon name="ph:truck" class="text-2xl" />
          </div>
        </div>
      </div>
    </div>

    <!-- Second Row Cards -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
      <!-- Return Requests -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-violet-500/10 to-violet-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-violet-600/80"
            >
              Return Requests
            </p>
            <p class="text-3xl font-bold mt-2 text-violet-900">8</p>
            <p
              class="text-xs font-medium mt-2 flex items-center text-violet-600"
            >
              <span class="inline-flex items-center">
                Awaiting processing
              </span>
            </p>
          </div>
          <div
            class="p-3 rounded-xl shadow-md bg-violet-500/20 text-violet-600"
          >
            <Icon name="ph:arrow-u-up-left" class="text-2xl" />
          </div>
        </div>
      </div>

      <!-- Warehouse Capacity -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-gray-500/10 to-gray-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-gray-600/80"
            >
              Warehouse Capacity
            </p>
            <p class="text-3xl font-bold mt-2 text-gray-900">78%</p>
            <p class="text-xs font-medium mt-2 flex items-center text-gray-600">
              <span class="inline-flex items-center">
                Storage utilization
              </span>
            </p>
          </div>
          <div class="p-3 rounded-xl shadow-md bg-gray-500/20 text-gray-600">
            <Icon name="ph:warehouse" class="text-2xl" />
          </div>
        </div>
      </div>

      <!-- Pending Receiving -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-amber-500/10 to-amber-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-amber-600/80"
            >
              Pending Receiving
            </p>
            <p class="text-3xl font-bold mt-2 text-amber-900">15</p>
            <p
              class="text-xs font-medium mt-2 flex items-center text-amber-600"
            >
              <span class="inline-flex items-center"> Incoming shipments </span>
            </p>
          </div>
          <div class="p-3 rounded-xl shadow-md bg-amber-500/20 text-amber-600">
            <Icon name="ph:arrow-down" class="text-2xl" />
          </div>
        </div>
      </div>

      <!-- Team Activity -->
      <div
        class="rounded-xl shadow-lg p-6 border-0 transition-all duration-300 hover:shadow-xl hover:-translate-y-1 bg-gradient-to-br from-cyan-500/10 to-cyan-600/20"
      >
        <div class="flex items-center justify-between">
          <div>
            <p
              class="text-sm font-semibold tracking-wide uppercase text-cyan-600/80"
            >
              Team Active
            </p>
            <p class="text-3xl font-bold mt-2 text-cyan-900">12/15</p>
            <p class="text-xs font-medium mt-2 flex items-center text-cyan-600">
              <span class="inline-flex items-center"> Staff members </span>
            </p>
          </div>
          <div class="p-3 rounded-xl shadow-md bg-cyan-500/20 text-cyan-600">
            <Icon name="ph:users" class="text-2xl" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
