<template>
  <div>
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-2xl font-bold text-gray-900">Warehouse Orders</h2>
      <div class="flex items-center gap-3">
        <button
          class="flex items-center gap-2 px-4 py-2 text-green-800 bg-green-100 hover:bg-green-300 text-gray-700 rounded-lg"
        >
          <Icon name="ph:export" class="text-lg" />
         
        </button>
        <button
          class="flex items-center gap-2 px-4 py-2 bg-primary hover:bg-primary/90 text-white rounded-lg"
        >
          <Icon name="ph:plus" class="text-lg" />
          New Order
        </button>
      </div>
    </div>

    <!-- Order Stats -->
    <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
      <div class="bg-blue-50 rounded-lg p-4 border border-blue-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-blue-600 font-medium">Total Orders</p>
            <p class="text-2xl font-bold text-blue-900">156</p>
          </div>
          <Icon name="ph:shopping-cart" class="text-2xl text-blue-500" />
        </div>
      </div>

      <div class="bg-yellow-50 rounded-lg p-4 border border-yellow-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-yellow-600 font-medium">
              Pending Processing
            </p>
            <p class="text-2xl font-bold text-yellow-900">28</p>
          </div>
          <Icon name="ph:clock" class="text-2xl text-yellow-500" />
        </div>
      </div>

      <div class="bg-green-50 rounded-lg p-4 border border-green-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-green-600 font-medium">Ready to Ship</p>
            <p class="text-2xl font-bold text-green-900">42</p>
          </div>
          <Icon name="ph:package" class="text-2xl text-green-500" />
        </div>
      </div>

      <div class="bg-purple-50 rounded-lg p-4 border border-purple-200">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-sm text-purple-600 font-medium">Shipped Today</p>
            <p class="text-2xl font-bold text-purple-900">19</p>
          </div>
          <Icon name="ph:truck" class="text-2xl text-purple-500" />
        </div>
      </div>
    </div>

    <!-- Orders Table -->
    <div class="bg-white rounded-xl shadow-sm overflow-hidden">
      <div
        class="p-6 border-b border-gray-100 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4"
      >
        <h3 class="font-semibold text-gray-900 text-lg">
          Order Management ({{ orders.length }})
        </h3>
        <div class="flex flex-col sm:flex-row gap-3 w-full sm:w-auto">
          <input
            type="text"
            placeholder="Search orders..."
            class="px-4 py-2 border border-gray-300 rounded-lg text-sm flex-1"
          />
          <select class="px-4 py-2 border border-gray-300 rounded-lg text-sm">
            <option>All Status</option>
            <option>Pending</option>
            <option>Processing</option>
            <option>Ready to Ship</option>
            <option>Shipped</option>
            <option>Delivered</option>
            <option>Cancelled</option>
          </select>
          <select class="px-4 py-2 border border-gray-300 rounded-lg text-sm">
            <option>All Channels</option>
            <option>Online Store</option>
            <option>Retail</option>
            <option>Wholesale</option>
          </select>
        </div>
      </div>

      <div class="overflow-x-auto">
        <div class="min-w-[1000px]">
          <table class="w-full divide-y divide-gray-200">
            <thead class="bg-orange-100">
              <tr>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Order ID
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Customer
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Order Date
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Items
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Total Amount
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Shipping M
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Status
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Priority
                </th>
                <th
                  class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider whitespace-nowrap"
                >
                  Actions
                </th>
              </tr>
            </thead>
            <tbody class="bg-white divide-y divide-gray-200">
              <tr v-for="order in orders" :key="order.id">
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="text-sm font-medium text-blue-600">
                    {{ order.order_code }}
                  </div>
                  <div class="text-xs text-gray-500">{{ order.channel }}</div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="text-sm font-medium text-gray-900">
                    {{ order.customer }}
                  </div>
                  <div class="text-xs text-gray-500">{{ order.phone }}</div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                  {{ order.order_date }}
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                  <span
                    class="inline-flex items-center px-2 py-1 rounded-full text-xs font-medium bg-gray-100 text-gray-800"
                  >
                    {{ order.items }} items
                  </span>
                </td>
                <td
                  class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"
                >
                  ${{ order.amount.toFixed(2) }}
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                  <span
                    class="inline-flex items-center px-2 py-1 rounded-full text-xs font-medium bg-blue-100 text-blue-800"
                  >
                    {{ order.shipping_method }}
                  </span>
                </td>
                <td class="px-2 py-4 whitespace-nowrap">
                  <select
                    :value="order.status"
                    @change="updateOrderStatus(order.id, $event.target.value)"
                    class="rounded-full text-xs font-medium px-3 py-1 border-0 focus:ring-2 focus:ring-primary/50"
                    :class="getStatusClass(order.status)"
                  >
                    <option value="Pending">Pending</option>
                    <option value="Processing">Processing</option>
                    <option value="Ready to Ship">Ready to Ship</option>
                    <option value="Shipped">Shipped</option>
                    <option value="Delivered">Delivered</option>
                    <option value="Cancelled">Cancelled</option>
                  </select>
                </td>
                <td class="px-6 py-4 whitespace-nowrap">
                  <span
                    class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium"
                    :class="getPriorityClass(order.priority)"
                  >
                    {{ order.priority }}
                  </span>
                </td>
                <td
                  class="px-5 py-4 whitespace-nowrap text-sm font-medium relative"
                >
                  <!-- 3-dot button -->
                  <div>
                    <button
                      @click="toggleMenu(order.id)"
                      class="p-1 text-primary"
                    >
                      <Icon name="ph:dots-three-vertical-duotone" class="text-lg" />
                    </button>

                    <!-- Dropdown -->
                    <div
                      v-if="openMenuId === order.id"
                      class="absolute right-0 mt-2 w-40 bg-white border border-gray-200 rounded-md shadow-lg z-20"
                    >
                      <button
                        class="w-full flex items-center gap-2 px-4 py-2 text-sm text-blue-600 hover:bg-blue-50"
                        @click="viewDetails(order)"
                      >
                        <Icon name="ph:eye" class="text-base" /> View
                      </button>
                      <button
                        class="w-full flex items-center gap-2 px-4 py-2 text-sm text-green-600 hover:bg-green-50"
                        @click="printLabel(order)"
                      >
                        <Icon name="ph:printer" class="text-base" /> Print
                      </button>
                      <button
                        class="w-full flex items-center gap-2 px-4 py-2 text-sm text-purple-600 hover:bg-purple-50"
                        @click="trackOrder(order)"
                      >
                        <Icon name="ph:map-pin" class="text-base" /> Track Order
                      </button>
                    </div>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- Pagination -->
      <div class="px-6 py-4 bg-gray-50 border-t border-gray-200">
        <div class="flex items-center justify-between">
          <div class="text-sm text-gray-700">
            Showing <span class="font-medium">1</span> to
            <span class="font-medium">10</span> of
            <span class="font-medium">156</span> results
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

// Warehouse orders data
const orders = ref([
  {
    id: 1,
    order_code: "WH-ORD-001",
    customer: "Sarah Johnson",
    phone: "+1 (555) 123-4567",
    order_date: "2023-10-15",
    items: 3,
    amount: 249.99,
    shipping_method: "Express",
    status: "Ready to Ship",
    priority: "High",
    channel: "Online Store",
  },
  {
    id: 2,
    order_code: "WH-ORD-002",
    customer: "Mike Chen",
    phone: "+1 (555) 234-5678",
    order_date: "2023-10-15",
    items: 1,
    amount: 89.99,
    shipping_method: "Standard",
    status: "Processing",
    priority: "Medium",
    channel: "Retail",
  },
  {
    id: 3,
    order_code: "WH-ORD-003",
    customer: "Emma Wilson",
    phone: "+1 (555) 345-6789",
    order_date: "2023-10-14",
    items: 5,
    amount: 459.99,
    shipping_method: "Next Day",
    status: "Pending",
    priority: "High",
    channel: "Wholesale",
  },
  {
    id: 4,
    order_code: "WH-ORD-004",
    customer: "David Kim",
    phone: "+1 (555) 456-7890",
    order_date: "2023-10-14",
    items: 2,
    amount: 129.99,
    shipping_method: "Standard",
    status: "Shipped",
    priority: "Low",
    channel: "Online Store",
  },
  {
    id: 5,
    order_code: "WH-ORD-005",
    customer: "Lisa Rodriguez",
    phone: "+1 (555) 567-8901",
    order_date: "2023-10-13",
    items: 4,
    amount: 329.99,
    shipping_method: "Express",
    status: "Delivered",
    priority: "Medium",
    channel: "Online Store",
  },
  {
    id: 6,
    order_code: "WH-ORD-006",
    customer: "James Brown",
    phone: "+1 (555) 678-9012",
    order_date: "2023-10-13",
    items: 1,
    amount: 79.99,
    shipping_method: "Standard",
    status: "Cancelled",
    priority: "Low",
    channel: "Retail",
  },
  {
    id: 7,
    order_code: "WH-ORD-007",
    customer: "Maria Garcia",
    phone: "+1 (555) 789-0123",
    order_date: "2023-10-12",
    items: 6,
    amount: 549.99,
    shipping_method: "Next Day",
    status: "Ready to Ship",
    priority: "High",
    channel: "Wholesale",
  },
  {
    id: 8,
    order_code: "WH-ORD-008",
    customer: "Robert Smith",
    phone: "+1 (555) 890-1234",
    order_date: "2023-10-12",
    items: 2,
    amount: 119.99,
    shipping_method: "Express",
    status: "Processing",
    priority: "Medium",
    channel: "Online Store",
  },
  {
    id: 9,
    order_code: "WH-ORD-009",
    customer: "Jennifer Lee",
    phone: "+1 (555) 901-2345",
    order_date: "2023-10-11",
    items: 3,
    amount: 229.99,
    shipping_method: "Standard",
    status: "Shipped",
    priority: "Low",
    channel: "Retail",
  },
  {
    id: 10,
    order_code: "WH-ORD-010",
    customer: "Thomas Wilson",
    phone: "+1 (555) 012-3456",
    order_date: "2023-10-11",
    items: 1,
    amount: 69.99,
    shipping_method: "Standard",
    status: "Delivered",
    priority: "Low",
    channel: "Online Store",
  },
]);

// Update order status
const updateOrderStatus = (orderId, newStatus) => {
  const order = orders.value.find((o) => o.id === orderId);
  if (order) {
    order.status = newStatus;
  }
};

// Get status class
const getStatusClass = (status) => {
  const classes = {
    Pending: "bg-gray-100 text-gray-800",
    Processing: "bg-yellow-100 text-yellow-800",
    "Ready to Ship": "bg-blue-100 text-blue-800",
    Shipped: "bg-green-100 text-green-800",
    Delivered: "bg-purple-100 text-purple-800",
    Cancelled: "bg-red-100 text-red-800",
  };
  return classes[status] || "bg-gray-100 text-gray-800";
};

// Get priority class
const getPriorityClass = (priority) => {
  const classes = {
    High: "bg-red-100 text-red-800",
    Medium: "bg-yellow-100 text-yellow-800",
    Low: "bg-green-100 text-green-800",
  };
  return classes[priority] || "bg-gray-100 text-gray-800";
};

const openMenuId = ref(null);

const toggleMenu = (id) => {
  openMenuId.value = openMenuId.value === id ? null : id;
};

const viewDetails = (item) => {
  console.log("Viewing details:", item);
  openMenuId.value = null;
};

const printLabel = (item) => {
  console.log("Printing label:", item);
  openMenuId.value = null;
};

const trackOrder = (item) => {
  console.log("Tracking order:", item);
  openMenuId.value = null;
};
</script>
