<template>
  <v-container>
    <div align="center">
      <h1>Pending Invitations</h1>
      <h4>You have been invited to the following workspaces</h4>
    </div>
    <v-row class="d-flex flex-column pt-12">
      <v-col>
        <v-row v-for="workspace in workspaces" :key="workspace.id">
          <v-col>
            <h3>{{ workspace.name }}</h3>
            <p>{{ workspaceOwner }}</p>
          </v-col>
          <v-col align="right" class="pt-8">
            <a
              ><font-awesome-icon
                class="text-brown trashbtn mr-3"
                icon="trash-alt"
                size="2x"
              ></font-awesome-icon
            ></a>
            <a
              ><font-awesome-icon
                class="text-brown checkbtn"
                icon="check"
                size="2x"
              ></font-awesome-icon
            ></a>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
    <div class="btn-end">
      <v-btn
        block
        @click="joinNewWorkspace()"
        color="bottom-button brown darken-3 white--text py-7 step-button"
        >NEXT</v-btn
      >
    </div>
  </v-container>
</template>

<script>
import ListWorkspaces from '~/queries/ListWorkspaces'
export default {
  data() {
    return {
      workspaceOwner: 'Makus Nikomi',
      workspaces: []
    }
  },
  apollo: {
    workspaces: {
      prefetch: true,
      query: ListWorkspaces
    }
  },
  methods: {
    joinNewWorkspace() {
      this.$emit('thisJoinWorkspace', this.workspaceOwner)
    },
    errorMessage() {
      console.log('error')
    }
  }
}
</script>

<style></style>
