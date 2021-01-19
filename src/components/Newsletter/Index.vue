<template>
    <div class="container newsl_container">
        <h2>Join to our newsleter</h2>
        <div class="form">
            <input type="text" v-model="email">
            <button @click="submitHandler()">Suscribe</button>
        </div>
        <div class="error_label">
            <div>{{error}}</div>
        </div>
        <div class="success_label">
            <div>{{success}}</div>
        </div>
        <div class="small">
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequatur officiis obcaecati, porro libero fuga qui natus voluptatem voluptate hic, error, adipisci molestiae pariatur tempora maxime. Hic a porro dolores totam.</p>
        </div>
    </div>
</template>


<script>
export default {
    data(){
        return{
            email:'',
            error: '',
            success: ''
        }
    },
    methods:{
        validate(email){
            let valid = [true,''];

            if(!/\S+@\S+\.\S+/.test(email)){
                valid = [false,'Enter a valid email'];
            }

            if(email === ''){
                valid = [false,'Its Empty'];
            }

            return valid
        },
        submitHandler(){
            let valid = this.validate(this.email);

            if(valid[0]){
                this.error = '';
                this.addEmail(this.email)
            } else{
                this.error = valid[1];
            }
        },
        addEmail(email){
            // eslint-disable-next-line no-useless-escape
            this.$http.get(`users.json?orderBy=\"email\"&&equalTo=\"${email}\"`)
            .then(response => {
                if(Object.getOwnPropertyNames(response.data).length === 0){
                    this.$http.post('users.json',{email: this.email})
                    // eslint-disable-next-line no-unused-vars
                    .then(response => {
                        this.success = 'Thank you';
                    })
                } else {
                    this.success = 'Already on the list'
                }
            });
            this.clearSuccess();
        },

        clearSuccess(){
            setTimeout(() => {
                this.email = '';
                this.success = '';
            }, 3000)
        }
    }
}
</script>