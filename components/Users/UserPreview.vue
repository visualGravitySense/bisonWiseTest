<template>

    <nuxt-link :to="/users/+user.id" class="bg-white overflow-hidden shadow p-4">
      <h3 class="leading-7 font-semibold">
        {{ user.name }}
      </h3>
      <p class="text-gray-600">
        {{ user.cat }}
      </p>

    </nuxt-link>


</template>

<script>

export default {

  props: {
    user: {
      type: Object,
      required: true
    },
    admin: {
      type: Boolean,
      default: false
    }
  },

  name: 'UserPreview',

};
</script>
