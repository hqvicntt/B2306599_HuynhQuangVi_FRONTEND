<template>
  <div class="page">
    <h4>Thêm mới Liên hệ</h4>
    <ContactForm :contact="{}" @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: { ContactForm },
  data() {
    return { message: "" };
  },
  methods: {
    async createContact(data) {
      try {
        await ContactService.create(data);
        this.message = "Liên hệ được thêm mới thành công.";
        alert("Thêm mới thành công!");
        this.$router.push({ name: "contactbook" });
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>
