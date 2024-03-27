<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="postcontact"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";
    export default{
        components: {
            ContactForm,
        },

        data() {
            return {
                contact: {},
                message: "",
            };
        },

        methods:{
            async postcontact(data) {
                try{
                    await ContactService.create(data);
                    this.message = " Thêm Thành Công";
                }catch(error){
                    console.log(error);
                }
            }
        },
        created() {
            this.message = "";
        },
    }
</script>