<script setup>
import { storeToRefs } from 'pinia';
import { useUserStore } from '../stores/user';

const { user } = storeToRefs(useUserStore())
</script>

<template>
  <v-main>

    <v-card class="mx-auto" max-width="434" height="250" tile>
      <v-img height="100%" src="https://cdn.vuetifyjs.com/images/cards/server-room.jpg">
        <v-row align="end" class="fill-height">
          <v-col align-self="start" class="pa-0" cols="12">
            <v-avatar class="profile" size="150 " tile>
              <v-img cover :src="user.avatar" />
            </v-avatar>
          </v-col>
          <v-col class="py-0">
            <v-list-item class="text-white" :title="user.fname + user.lname" :subtitle="user.email"/>

          
          </v-col>
        </v-row>
      </v-img>
    </v-card>
  </v-main>
</template>