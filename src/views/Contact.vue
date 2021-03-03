<template>
    <div class="page contact">

        <h2 class="page__title">Send us an email:</h2>

        <contact-form></contact-form>

    </div>
</template>

<script>
import ContactForm from '@/components/ContactForm';

export default {
    name: 'Contact',

    components: {
        ContactForm
    }
};
</script>

<style lang="scss" scoped>

</style>
