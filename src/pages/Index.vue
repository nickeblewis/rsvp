<template>
  <Layout>
    <div class="hero container-inner mx-auto flex flex-col sm:flex-row justify-between py-16">
      <div class="text-4xl font-bold w-full sm:w-3/5 text-center sm:text-left">
        <div class="leading-tight">You are invited to attend</div>
        <div class="text-orange-700 leading-tight">The Celebration of Alice and Matt Allen's Marriage</div>
      </div>

    </div> <!-- end hero -->

    <div class="container-inner mx-auto" id="about">
      <p class="text-lg sm:text-xl mb-4">Please RSVP etc etc</p>
      
      <p class="text-lg sm:text-xl mb-4">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Excepturi optio odit mollitia illo ullam rem qui, nulla sit vero asperiores magni, quidem, impedit dolores debitis dignissimos molestiae commodi dicta eligendi!</p>

      <p class="text-lg sm:text-xl mb-4">Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus voluptates quam aliquam atque voluptatum, impedit, temporibus consequatur, quae omnis earum autem provident nisi explicabo eveniet neque quod numquam voluptate illo.</p>
        


    
    </div>

    
    
    

   
    </div>

    <div class="overflow-x-hidden">
      <div class="contact-me bg-background-secondary pt-16">
        <div class="container-inner mx-auto text-xl pb-4 relative">
          <h2 class="font-bold mb-6" id="contact">RSVP:</h2>

          <div class="absolute right-0 top-0" style="transform: translate(100%) rotate(180deg)">
            <svg width="170px" height="170px"><use xlink:href="#dots-triangle" /></svg>
          </div>

          <div class="text-lg sm:text-lg mb-16">
            <form 
              name="contact" 
              class="mb-12" 
              method="post" 
              v-on:submit.prevent="handleSubmit"
              data-netlify="true"
              data-netlify-honeypot="bot-field">
              <input type="hidden" name="form-name" value="contact" />
              <p hidden>
                <label>
                  Don’t fill this out: <input name="bot-field" />
                </label>
              </p>
              <div class="flex flex-wrap mb-6 -mx-4">
                  <div class="w-full md:w-1/2 mb-6 md:mb-0 px-4">
                      <label class="block mb-2 text-copy-primary" for="name">
                          Name
                      </label>

                      <input type="text" name="name" id="name" placeholder="Your Full Name" class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none focus:border-green-700 mb-2 p-4" 
                      v-model="formData.name"
                      required>
                  </div>

                  <div class="w-full px-4 md:w-1/2">
                      <label class="block text-copy-primary mb-2" for="email">
                          Email Address
                      </label>

                      <input type="email" name="email" id="email" placeholder="email@example.com"  class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none focus:border-orange-700 mb-2 p-4" 
                       v-model="formData.email"
                      required>
                  </div>
              </div>

              <div class="w-full mb-12">
                  <label class="block text-copy-primary mb-2" for="message">
                      Message
                  </label>

                  <textarea id="message" rows="5" name="message" class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none appearance-none focus:border-orange-700 mb-2 px-4 py-4" placeholder="Any special messages you wish to send us..." 
                  v-model="formData.message"
                  required></textarea>
              </div>

              <div class="w-full mb-12">
                  <label class="block text-copy-primary mb-2" for="songs">
                      Song Choices
                  </label>

                  <textarea id="songs" rows="5" name="songs" class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none appearance-none focus:border-orange-700 mb-2 px-4 py-4" placeholder="Enter your song choices here for our DJ" 
                  v-model="formData.songs"
                  required></textarea>
              </div>

              <div class="w-full mb-12">
                  <label class="block text-copy-primary mb-2" for="dietary">
                      Dietary Requirements
                  </label>

                  <textarea id="dietary" rows="5" name="dietary" class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none appearance-none focus:border-orange-700 mb-2 px-4 py-4" placeholder="Please let us know if you have an special dietary requirements." 
                  v-model="formData.dietary"
                  required></textarea>
              </div>

              <div class="flex justify-end w-full">
                  <button type="submit" value="submit" class="block bg-orange-700 hover:bg-orange-800 text-white text-sm font-semibold tracking-wide uppercase shadow rounded cursor-pointer px-6 py-3">Submit</button>
              </div>
          </form>
          </div>
        </div>
      </div> <!-- end contact-me -->
    </div>
  </Layout>
</template>

<script>
export default {
  data() {
    return {
      formData: {},
    }
  },
  methods: {
  encode(data) {
    return Object.keys(data)
      .map(key => encodeURIComponent(key) + '=' + encodeURIComponent(data[key]))
      .join('&')
  },
  handleSubmit(e) {
    fetch('/', {
      method: 'POST',
      headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
      body: this.encode({
        'form-name': e.target.getAttribute('name'),
        ...this.formData,
      }),
    })
    .then(() => this.$router.push('/success'))
    .catch(error => alert(error))
  }
},

  metaInfo: {
    title: 'Home'
  }
}
</script>

