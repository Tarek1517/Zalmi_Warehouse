<template>
  <div>
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-2xl font-bold text-gray-900">Warehouse Inventory</h2>
      <button
        class="flex items-center gap-2 px-4 py-2 bg-primary hover:bg-primary/90 text-white rounded-lg"
      >
        <Icon name="ph:plus" />
        Add Inventory
      </button>
    </div>

    <!-- Inventory Stats -->
    <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
      <div class="bg-blue-50 rounded-lg p-4 border border-blue-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-blue-600 font-medium">Total Items</p>
            <p class="text-2xl font-bold text-blue-900">2,847</p>
          </div>
          <Icon name="ph:package" class="text-2xl text-blue-500" />
        </div>
      </div>

      <div class="bg-green-50 rounded-lg p-4 border border-green-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-green-600 font-medium">In Stock</p>
            <p class="text-2xl font-bold text-green-900">2,156</p>
          </div>
          <Icon name="ph:check-circle" class="text-2xl text-green-500" />
        </div>
      </div>

      <div class="bg-yellow-50 rounded-lg p-4 border border-yellow-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-yellow-600 font-medium">Low Stock</p>
            <p class="text-2xl font-bold text-yellow-900">342</p>
          </div>
          <Icon name="ph:warning" class="text-2xl text-yellow-500" />
        </div>
      </div>

      <div class="bg-red-50 rounded-lg p-4 border border-red-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-red-600 font-medium">Out of Stock</p>
            <p class="text-2xl font-bold text-red-900">349</p>
          </div>
          <Icon name="ph:x-circle" class="text-2xl text-red-500" />
        </div>
      </div>
    </div>

    <!-- Inventory Management -->
    <div class="bg-white rounded-xl shadow-sm overflow-hidden">
      <div
        class="py-6 border-b border-gray-100 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4"
      >
        <h3 class="font-semibold text-gray-900 text-lg">
          Inventory Items ({{ inventory.length }})
        </h3>
        <div class="flex flex-col sm:flex-row gap-3 w-full sm:w-auto">
          <input
            type="text"
            placeholder="Search inventory..."
            class="px-4 py-2 border border-gray-300 rounded-lg text-sm flex-1"
          />
          <select class="px-4 py-2 border border-gray-300 rounded-lg text-sm">
            <option>All Categories</option>
            <option>Electronics</option>
            <option>Clothing</option>
            <option>Home & Kitchen</option>
            <option>Sports</option>
          </select>
          <select class="px-4 py-2 border border-gray-300 rounded-lg text-sm">
            <option>All Status</option>
            <option>In Stock</option>
            <option>Low Stock</option>
            <option>Out of Stock</option>
          </select>
        </div>
      </div>

      <div class="overflow-x-auto">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-green-100 rounded-md">
            <tr>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Product
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                SKU
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Category
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Current Stock
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Location
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Status
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Last Updated
              </th>
              <th
                class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
              >
                Actions
              </th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr v-for="item in inventory" :key="item.id">
              <td class="px-2 py-4 whitespace-nowrap">
                <div class="flex items-center">
                  <div class="h-10 w-10 flex-shrink-0">
                    <img
                      class="h-10 w-10 rounded-md object-cover"
                      :src="item.image"
                      :alt="item.name"
                    />
                  </div>
                  <div class="ml-4 w-32">
                    <!-- Fixed width for text -->
                    <div
                      class="font-medium text-gray-900 truncate"
                      title="{{ item.name }}"
                    >
                      {{ item.name }}
                    </div>
                    <div
                      class="text-sm text-gray-500 truncate"
                      title="{{ item.brand }}"
                    >
                      {{ item.brand }}
                    </div>
                  </div>
                </div>
              </td>

              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                {{ item.sku }}
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                <span
                  class="inline-flex items-center px-2 py-1 rounded-full text-xs font-medium bg-gray-100 text-gray-800"
                >
                  {{ item.category }}
                </span>
              </td>
              <td class="px-6 py-4 whitespace-nowrap">
                <div class="flex items-center gap-2">
                  <span class="text-sm font-medium text-gray-900">{{
                    item.currentStock
                  }}</span>
                  <span class="text-xs text-gray-500"
                    >/ {{ item.maxStock }}</span
                  >
                </div>
                <div class="w-20 bg-gray-200 rounded-full h-1.5 mt-1">
                  <div
                    class="h-1.5 rounded-full"
                    :class="{
                      'bg-green-500': item.stockPercentage >= 50,
                      'bg-yellow-500':
                        item.stockPercentage >= 20 && item.stockPercentage < 50,
                      'bg-red-500': item.stockPercentage < 20,
                    }"
                    :style="{ width: `${item.stockPercentage}%` }"
                  ></div>
                </div>
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                <span
                  class="inline-flex items-center px-2 py-1 rounded-full text-xs font-medium bg-blue-100 text-blue-800"
                >
                  {{ item.location }}
                </span>
              </td>
              <td class="px-6 py-4 whitespace-nowrap">
                <span
                  class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium"
                  :class="{
                    'bg-green-100 text-green-800': item.status === 'In Stock',
                    'bg-yellow-100 text-yellow-800':
                      item.status === 'Low Stock',
                    'bg-red-100 text-red-800': item.status === 'Out of Stock',
                  }"
                >
                  {{ item.status }}
                </span>
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                {{ item.lastUpdated }}
              </td>
              <td
                class="px-6 py-4 whitespace-nowrap text-sm font-medium relative"
              >
                <!-- 3-dot button -->
                <div>
                  <button
                    @click="item.showActions = !item.showActions"
                    class="p-1 text-primary"
                  >
                    <Icon name="ph:dots-three-vertical-duotone" class="text-lg" />
                  </button>

                  <!-- Dropdown Menu -->
                  <div
                    v-if="item.showActions"
                    class="absolute right-0 mt-2 w-32 bg-white border border-gray-200 rounded-md shadow-lg z-20"
                  >
                    <button
                      class="w-full text-left px-4 py-2 text-sm text-blue-600 hover:bg-blue-50 flex items-center gap-2"
                      @click="editItem(item)"
                    >
                      <Icon name="ph:pencil-simple" class="text-base" /> Edit
                    </button>
                    <button
                      class="w-full text-left px-4 py-2 text-sm text-green-600 hover:bg-green-50 flex items-center gap-2"
                      @click="downloadItem(item)"
                    >
                      <Icon name="ph:arrow-down" class="text-base" /> Download
                    </button>
                    <button
                      class="w-full text-left px-4 py-2 text-sm text-red-600 hover:bg-red-50 flex items-center gap-2"
                      @click="deleteItem(item)"
                    >
                      <Icon name="ph:trash" class="text-base" /> Delete
                    </button>
                  </div>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- Pagination -->
      <div class="px-6 py-4 bg-gray-50 border-t border-gray-200">
        <div class="flex items-center justify-between">
          <div class="text-sm text-gray-700">
            Showing <span class="font-medium">1</span> to
            <span class="font-medium">10</span> of
            <span class="font-medium">2847</span> results
          </div>
          <div class="flex items-center gap-2">
            <button
              class="px-3 py-1 border border-gray-300 rounded-md text-sm hover:bg-gray-50"
            >
              Previous
            </button>
            <button class="px-3 py-1 bg-primary text-white rounded-md text-sm">
              1
            </button>
            <button
              class="px-3 py-1 border border-gray-300 rounded-md text-sm hover:bg-gray-50"
            >
              2
            </button>
            <button
              class="px-3 py-1 border border-gray-300 rounded-md text-sm hover:bg-gray-50"
            >
              3
            </button>
            <button
              class="px-3 py-1 border border-gray-300 rounded-md text-sm hover:bg-gray-50"
            >
              Next
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

// Warehouse inventory data
const inventory = ref([
  {
    id: 1,
    name: "Wireless Bluetooth Headphones",
    sku: "WH-1000XM4",
    brand: "Sony",
    category: "Electronics",
    currentStock: 45,
    maxStock: 100,
    stockPercentage: 45,
    location: "A-12-4",
    status: "In Stock",
    lastUpdated: "2 hours ago",
    image:
      "https://images.unsplash.com/photo-1505740420928-5e560c06d30e?w=100&h=100&fit=crop",
  },
  {
    id: 2,
    name: "Smart Fitness Watch",
    sku: "FIT-PRO-2024",
    brand: "FitTech",
    category: "Electronics",
    currentStock: 8,
    maxStock: 50,
    stockPercentage: 16,
    location: "B-08-2",
    status: "Low Stock",
    lastUpdated: "5 hours ago",
    image:
      "https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=100&h=100&fit=crop",
  },
  {
    id: 3,
    name: "Stainless Steel Water Bottle",
    sku: "HYDRO-750ML",
    brand: "HydroFlask",
    category: "Kitchen",
    currentStock: 0,
    maxStock: 75,
    stockPercentage: 0,
    location: "C-15-7",
    status: "Out of Stock",
    lastUpdated: "1 day ago",
    image:
      "https://images.unsplash.com/photo-1602143407151-7111542de6e8?w=100&h=100&fit=crop",
  },
  {
    id: 4,
    name: "Yoga Mat Premium",
    sku: "YG-MAT-PRO",
    brand: "YogaLife",
    category: "Sports",
    currentStock: 23,
    maxStock: 60,
    stockPercentage: 38,
    location: "D-03-1",
    status: "In Stock",
    lastUpdated: "3 hours ago",
    image:
      "https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?w=100&h=100&fit=crop",
  },
  {
    id: 5,
    name: "Wireless Charging Pad",
    sku: "WC-15W-QI",
    brand: "ChargeTech",
    category: "Electronics",
    currentStock: 67,
    maxStock: 120,
    stockPercentage: 56,
    location: "A-18-3",
    status: "In Stock",
    lastUpdated: "4 hours ago",
    image: "https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?w=100&h=100&fit=crop",
  },
  {
    id: 6,
    name: "Running Shoes - Men's",
    sku: "RUN-M-10",
    brand: "RunFast",
    category: "Sports",
    currentStock: 5,
    maxStock: 40,
    stockPercentage: 12,
    location: "E-22-5",
    status: "Low Stock",
    lastUpdated: "6 hours ago",
    image:
      "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=100&h=100&fit=crop",
  },
  {
    id: 7,
    name: "Bluetooth Speaker",
    sku: "BT-SPK-MINI",
    brand: "AudioPro",
    category: "Electronics",
    currentStock: 34,
    maxStock: 80,
    stockPercentage: 42,
    location: "B-11-6",
    status: "In Stock",
    lastUpdated: "8 hours ago",
    image:
      "https://images.unsplash.com/photo-1608043152269-423dbba4e7e1?w=100&h=100&fit=crop",
  },
  {
    id: 8,
    name: "Coffee Maker Deluxe",
    sku: "COFFEE-DLX",
    brand: "BrewMaster",
    category: "Kitchen",
    currentStock: 0,
    maxStock: 25,
    stockPercentage: 0,
    location: "C-09-8",
    status: "Out of Stock",
    lastUpdated: "2 days ago",
    image:
      "https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=100&h=100&fit=crop",
  },
  {
    id: 9,
    name: "Backpack - Waterproof",
    sku: "BP-TRVL-30L",
    brand: "TravelGear",
    category: "Travel",
    currentStock: 18,
    maxStock: 35,
    stockPercentage: 51,
    location: "F-07-4",
    status: "In Stock",
    lastUpdated: "12 hours ago",
    image:
      "https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=100&h=100&fit=crop",
  },
  {
    id: 10,
    name: "Wireless Mouse",
    sku: "WM-ERGO-PRO",
    brand: "TechAccess",
    category: "Electronics",
    currentStock: 3,
    maxStock: 30,
    stockPercentage: 10,
    location: "A-05-9",
    status: "Low Stock",
    lastUpdated: "7 hours ago",
    image:
      "https://images.unsplash.com/photo-1527864550417-7fd91fc51a46?w=100&h=100&fit=crop",
  },
]);
</script>
