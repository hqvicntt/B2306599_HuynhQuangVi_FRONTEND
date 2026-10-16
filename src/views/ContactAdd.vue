<template>
    <div class="page">
        <h4>Thêm Liên hệ Mới</h4>
        <ContactForm 
            :contact="{}" 
            @submit:contact="createContact" 
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            message: "",
        };
    },
    methods: {
        async createContact(data) {
            try {
                await ContactService.create(data);
                alert("Liên hệ mới đã được thêm thành công.");
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.log(error);
                this.message = "Đã có lỗi xảy ra khi thêm liên hệ mới.";
            }
        },
    },
};
</script>

<style scoped>
.page {
    text-align: left;
    max-width: 500px;
}
</style>
