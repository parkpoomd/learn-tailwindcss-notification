<template>
  <div class="p-8">
    <span class="inline-flex rounded-md shadow-sm">
      <button
        @click="notify"
        type="button"
        class="inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
      >
        Notify
      </button>
    </span>
  </div>
  <div
    class="fixed inset-0 flex items-start justify-end px-4 py-6 sm:p-6 pointer-events-none"
  >
    <div class="max-w-sm w-full">
      <transition-group
        tag="div"
        :enter-active-class="
          sortedNotifications.length > 1
            ? 'transform ease-out delay-300 duration-300 transition'
            : 'transform ease-out duration-300 transition'
        "
        enter-from-class="translate-x-4 opacity-0"
        enter-to-class="translate-x-0 opacity-100"
        leave-active-class="transition ease-in duration-100"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
        move-class="transition ease-in-out duration-500"
      >
        <Notification
          v-for="(notification, i) in sortedNotifications"
          :key="notification.id"
          :id="notification.id"
          :class="i > 0 ? 'mt-4' : ''"
          @remove="removeNotification"
        />
      </transition-group>
    </div>
  </div>
</template>

<script>
import Notification from './components/Notification';

export default {
  name: 'App',
  components: {
    Notification,
  },
  data() {
    return {
      count: 0,
      notifications: [],
    };
  },
  computed: {
    sortedNotifications() {
      return [...this.notifications].reverse().slice(0, 4);
    },
  },
  methods: {
    removeNotification(id) {
      this.notifications = this.notifications.filter((n) => n.id !== id);
    },
    notify() {
      const notification = { id: this.count };
      this.notifications.push(notification);
      this.count += 1;

      setTimeout(() => {
        this.removeNotification(notification.id);
      }, 3000);
    },
  },
};
</script>
