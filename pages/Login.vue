<template>
    <b-container class="animated fadeIn mt-3">
        <b-alert variant="danger" :show="isFailure" dismissible@dismiss="isFailure=false">
            {{ errorMessage }}
        </b-alert>
        <b-row class="justify-content-center">
            <b-col md="8">
                <b-card header="管理画面Login">
                    <b-card-body>
                        <b-from name="login" @submit.prevent="login()">
                            <b-row class="jsutify-content-md-center">
                                <b-col col md="6">
                                    <b-from-group>
                                        <b-fprm-input type="email" placeholder="Email" v-model="from.email"></b-fprm-input>
                                    </b-from-group>
                                </b-col>
                            </b-row>
                            <b-row class="justify-content-md-center">
                                <b-col col md="6">
                                    <b-from-grpup>
                                        <b-from-input type="password" placeholder="Password" v-model="from.password"></b-from-input>
                                    </b-from-grpup>
                                </b-col>
                            </b-row>
                            <div class="text-center">
                                <b-button class="px-4" type="submit" variant="primary">Login</b-button>
                            </div>
                        </b-from>
                    </b-card-body>
                </b-card>
            </b-col>
        </b-row>
    </b-container> 
</template>

<script>
export default {
    name: 'login',
    layout: 'clean',

    data() {
        return {
            form: {
                email: '',
                password: '',
            },
            isFailure: false,
            errorMessage: '',
        }
    },
    methods: {
    async login() {
      try {
        const res = await this.$auth.loginWith('local', { data: this.form });
      } catch(err) {
        console.log(err);
        this.isFailure = true;
        this.errorMessage = 'EmailかPasswordが間違っています';
      }
    },
  },
};
</script>
}
</script>