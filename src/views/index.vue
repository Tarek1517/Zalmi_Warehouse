<script setup lang="ts"></script>

<template>
  <div
    class="flex items-center justify-center min-h-screen bg-gradient-to-br from-yellow-100 via-white to-yellow-200 px-4"
  >
    <div
      class="max-w-5xl w-full grid grid-cols-1 md:grid-cols-2 shadow-2xl rounded-2xl overflow-hidden bg-white"
    >
      <!-- Left Side: Form -->
      <div class="px-10 py-12 flex flex-col justify-center">
        <!-- Title -->
        <div class="text-center mb-8">
          <div class="flex justify-center mb-4">
            <img
              class="w-24 h-auto mx-auto"
              src="@/assets/images/logo.png"
              alt="Zalmi Logo"
            />
          </div>
          <h2 class="text-3xl font-extrabold text-gray-900">Zalmi Warehouse</h2>
          <p class="text-sm text-gray-600">Sign in to manage your inventory</p>
        </div>

        <!-- Form -->
        <div class="space-y-6 max-w-sm mx-auto w-full">
          <!-- Email -->
          <div>
            <label
              for="email"
              class="block text-sm font-medium text-gray-700 mb-2"
              >Email Address</label
            >
            <input
              id="email"
              type="email"
              placeholder="warehouse@zalmi.com"
              class="block w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-400 focus:border-yellow-400 placeholder-gray-400"
            />
          </div>

          <!-- Password -->
          <div>
            <label
              for="password"
              class="block text-sm font-medium text-gray-700 mb-2"
              >Password</label
            >
            <input
              id="password"
              type="password"
              placeholder="••••••••"
              class="block w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-yellow-400 focus:border-yellow-400 placeholder-gray-400"
            />
          </div>

          <!-- Remember / Forgot -->
          <div class="flex items-center justify-between text-sm">
            <label class="flex items-center">
              <input
                type="checkbox"
                class="h-4 w-4 text-yellow-500 border-gray-300 rounded focus:ring-yellow-400"
              />
              <span class="ml-2 text-gray-700">Remember me</span>
            </label>
            <a
              href="#"
              class="font-medium text-primary hover:text-yellow-800 transition"
              >Forgot password?</a
            >
          </div>

          <!-- Submit -->
          <!-- <button
            class="w-full flex justify-center items-center py-3 px-4 rounded-lg shadow-md text-white bg-gradient-to-r from-primary/80 to-primary hover:from-yellow-600 hover:to-yellow-800 font-semibold transition"
          >
            Access Warehouse
          </button> -->

          <RouterLink
            to="/dashboard"
            class="w-full flex justify-center items-center py-3 px-4 rounded-lg shadow-md text-white bg-gradient-to-r from-primary/80 to-primary hover:from-yellow-600 hover:to-yellow-800 font-semibold transition"
          >
            Access Warehouse
          </RouterLink>
        </div>

        <!-- Footer -->
        <div class="mt-10 text-center text-xs text-gray-500">
          © 2025 Zalmi Warehouse Management — All Rights Reserved
        </div>
      </div>

      <!-- Right Side: Image -->
      <div class="hidden md:flex items-center justify-center bg-gray-100">
        <img
          src="@/assets/images/warehouseLogin.jpg"
          alt="Warehouse Illustration"
          class="w-full h-full object-cover"
        />
      </div>
    </div>
  </div>
</template>
