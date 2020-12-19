<template>
  <div class="bg-white shadow-lg rounded-lg pointer-events-auto">
    <div class="rounded-lg border overflow-hidden">
      <div class="p-4">
        <div class="flex items-start">
          <div class="flex-shrink-0">
            <svg
              class="h-6 w-6 text-green-400"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
              />
            </svg>
          </div>
          <div class="ml-3 w-0 flex-1 pt-0.5">
            <p class="text-sm leading-5 font-medium text-gray-900">
              {{ id }}
              Successfully saved!
            </p>
            <p class="mt-1 text-sm leading-5 text-gray-500">
              Anyone with a link can now view this file.
            </p>
          </div>
          <div class="ml-4 flex-shrink-0 flex">
            <button
              @click="$emit('remove', id)"
              type="button"
              class="inline-flex text-gray-400 focus:ouline-none focus:text-gray-500 transition duration-150 ease-in-out"
            >
              <svg
                class="h-5 w-5"
                xmlns="http://www.w3.org/2000/svg"
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
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['id'],
};
</script>
