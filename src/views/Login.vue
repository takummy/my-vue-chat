<template>
  <div class="login">
    <b-jumbotron header="びゅーちゃっと"
                 lead="Chatkit SDKとBootstrap-Vueで作ってます。"
                 bg-variant="info"
                 text-variant="white">
      <p>↓ソースコードはこちらです</p>
      <b-btn target="_blank" href="https://github.com/takummy/my-vue-chat">GitHub</b-btn>
    </b-jumbotron>
    <b-container>
      <b-row>
        <b-col lg="4" md="3"></b-col>
        <b-col lg="4" md="6">
          <LoginForm/>
        </b-col>
        <b-col lg="4" md="3"></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import LoginForm from '@/components/LoginForm.vue'

export default {
  name: 'login',
  components: {
    LoginForm
  }
}
</script>