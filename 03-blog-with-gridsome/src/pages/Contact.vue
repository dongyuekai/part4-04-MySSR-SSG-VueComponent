<template>
  <Layout>
    <!-- Page Header -->
    <header
      class="masthead"
      style="background-image: url('/img/contact-bg.jpg')"
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="page-heading">
              <h1>Contact Me</h1>
              <span class="subheading">Have questions? I have answers.</span>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <p>
            Want to get in touch? Fill out the form below to send me a message
            and I will get back to you as soon as possible!
          </p>
          <!-- Contact Form - Enter your email address on line 19 of the mail/contact_me.php file to make this form work. -->
          <!-- WARNING: Some web hosts do not allow emails to be sent through forms to common mail hosts like Gmail or Yahoo. It's recommended that you use a private domain email address! -->
          <!-- To use the contact form, your site must be on a live web host with PHP! The form will not work locally! -->
          <form name="sentMessage" id="contactForm" novalidate>
            <div class="control-group">
              <div class="form-group floating-label-form-group controls">
                <label>Name</label>
                <input
                  type="text"
                  class="form-control"
                  placeholder="Name"
                  id="name"
                  required
                  data-validation-required-message="Please enter your name."
                  v-model="form.name"
                />
                <p class="help-block text-danger"></p>
              </div>
            </div>
            <div class="control-group">
              <div class="form-group floating-label-form-group controls">
                <label>Email Address</label>
                <input
                  type="email"
                  class="form-control"
                  placeholder="Email Address"
                  id="email"
                  required
                  data-validation-required-message="Please enter your email address."
                  v-model="form.email"
                />
                <p class="help-block text-danger"></p>
              </div>
            </div>
            <div class="control-group">
              <div
                class="form-group col-xs-12 floating-label-form-group controls"
              >
                <label>Phone Number</label>
                <input
                  type="tel"
                  class="form-control"
                  placeholder="Phone Number"
                  id="phone"
                  required
                  data-validation-required-message="Please enter your phone number."
                  v-model="form.phone"
                />
                <p class="help-block text-danger"></p>
              </div>
            </div>
            <div class="control-group">
              <div class="form-group floating-label-form-group controls">
                <label>Message</label>
                <textarea
                  rows="5"
                  class="form-control"
                  placeholder="Message"
                  id="message"
                  required
                  data-validation-required-message="Please enter a message."
                  v-model="form.message"
                ></textarea>
                <p class="help-block text-danger"></p>
              </div>
            </div>
            <br />
            <div id="success"></div>
            <button
              type="submit"
              class="btn btn-primary"
              id="sendMessageButton"
              @click.prevent="onSubmit"
            >
              Send
            </button>
          </form>
        </div>
      </div>
    </div>
  </Layout>
</template>

<script>
import axios from "axios";

export default {
  name: "ContactPage",
  data() {
    return {
      form: {
        name: "",
        email: "",
        phone: "",
        message: "",
      },
    };
  },
  methods: {
    async onSubmit() {
      await axios({
        method: 'POST',
        url:'http://localhost:1337/contacts',
        data:this.form
      })
    },
  },
};
</script>

<style lang="scss" scoped>
</style>