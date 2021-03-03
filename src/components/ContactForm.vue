<template>
    <form
        class="form"
        @submit="validateAndSend($event)"
    >

        <div
            class="
        form__row">

            <label
                for="email"
                class="form__label">E-mail:</label>
            <input
                v-model="userEmail"
                type="text"
                id="email"
                name="email"
                class="form__input"
                placeholder="E-mail">
            <p
                v-if="userEmailError"
                class="form__input_error">
                This is not a valid e-mail!
            </p>

        </div>

        <div class="form__row">

            <label
                for="message"
                class="form__label">Message:</label>
            <textarea
                v-model="userMessage"
                type="text"
                id="message"
                name="message"
                class="form__textarea"
                placeholder="Message">
            </textarea>
            <p
                v-if="userMessageError"
                class="form__input_error">
                The message should have at least 30 characters!
            </p>

        </div>

        <div class="form__row">

            <button
                type="submit"
                class="form__submit_btn">
                Submit
            </button>

        </div>

        <div class="form__row">
            <p
                v-if="messageSent"
                class="form__success_message">
                The message was sent succesfully!
            </p>
        </div>

    </form>
</template>

<script>
export default {
    name: 'ContactForm',

    data () {
        return {
            userEmail: '',
            userMessage: '',
            userEmailError: false,
            userMessageError: false,
            messageSent: false
        };
    },

    methods: {

        validateAndSend (e) {
            e.preventDefault();

            const emailRegEx = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            const messageRegEx = /^.{30,}$/;
            // return re.test(this.userEmail);

            this.userEmailError = !emailRegEx.test(this.userEmail);
            this.userMessageError = !messageRegEx.test(this.userMessage);


            if (this.userEmailError || this.userMessageError) return;

            this.userEmail = '';
            this.userMessage = '';
            this.messageSent = true;

            setTimeout(() => {
                this.messageSent = false;
            }, 3000);

        }

    }
};
</script>

<style lang="scss" scoped>

</style>
