<template>
  <h1>Hi, {{ user?.displayName }}</h1>

  <button @click="handleLogOut">Log out</button>
</template>

<script lang="ts">
import useAuthentication from '../composables/useAuthentication'
import { useRouter } from 'vue-router'

export default {
  setup() {
    const { user, logout } = useAuthentication()
    const { replace } = useRouter()

    const handleLogOut = () => {
      logout().then(() => {
        return replace('/auth/login')
      })
    }

    return {
      user,
      handleLogOut,
    }
  },
}
</script>
