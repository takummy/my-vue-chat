<template>
  <div class="login-form">
    <h5 class="text-center">ログイン</h5>
    <hr>
    <b-form @submit.prevent="onSubmit">
      <b-alert variant="danger" :show="hasError">{{ error }}</b-alert>

      <b-form-group id="userInputGroup"
                    label="ユーザー名"
                    label-for="userInput">
        <b-form-input id="userInput"
                      type="text"
                      placeholder="ユーザー名を入力してください"
                      v-model="userId"
                      autocomplete="off"
                      :disabled="loading"
                      required>
        </b-form-input>
      </b-form-group>
      <b-button class="ld-ext-right"
                type="submit"
                variant="primary"
                v-bind:class="{ running: loading }"
                :disabled="isValid">
        Login <div class="ld ld-ring ld-spin"></div>

      </b-button>
    </b-form>
  </div>
</template>

<script>
import { mapState, mapGetters, mapActions } from 'vuex'

export default {
  name: 'login-form',
  data() {
    return {
      userId: ''
    }
  },
  computed: {
    isValid: function() {
      const result = this.userId.length < 3;
      return result ? result : this.loading
    },
    ...mapState([
      'loading',
      'error'
    ]),
    ...mapGetters([
      'hasError'
    ])
  },
  methods: {
    ...mapActions([
      'login'
    ]),
    async onSubmit() {
      const result = await this.login(this.userId);
      if(result) {
        this.$router.push('chat');
      }
    }
  }
}
</script>