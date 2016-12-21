# reCAPTCHA

From the [reCAPTCHA](https://www.google.com/recaptcha/intro/index.html):

> Protect your website from spam and abuse while letting real people pass through with ease

It is an awesome free service provided by Google. Setting it up with LiveForm is very simple.

 1. Go to the reCAPTCHA website and click on the 'Get reCAPTCHA' button
  ![Get reCAPTCHA](/images/recaptcha/recaptcha-home-1.png)
 2. Register a new site on reCAPTCHA
  ![Register a new site](/images/recaptcha/recaptcha-register-site-2.png)
 3. Note the `Site key` and the `Secret key` values from your form details page on reCAPTCHA
  ![Site and secret key](/images/recaptcha/recaptcha-keys-3.png)
 4. Paste your `Secret key` on the LiveForm reCAPTCHA configuration page and save it. In our example that would be `6LfhfA8UAAAAAKkGE0t5QxPJD3G5sXut70SW4Gcq`
  ![Liveform reCAPTCHA configuration](/images/recaptcha/recaptcha-liveform-setting-4.png)
 5. Paste this snippet before the closing `</head>` tag on your HTML template. Replace `form_submit` with the id of your submit button

        <script src='https://www.google.com/recaptcha/api.js'></script>
        <script>
        function enableSubmit() {
          var btn = document.getElementById('form_submit');
          btn.disabled = false;
          btn.title = '';
        }
        </script>

 6. Paste this snippet at the end of the `<form>` where you want the reCAPTCHA widget to appear, make sure you use your Site key:

        <div class="g-recaptcha" data-sitekey="6LfhfA8UAAAAAE8tjvWtBUmPvO6xaxHuceNags-j"
          data-callback="enableSubmit"></div>

 7. Make sure your submit button has an `id` attribute set to the same `id` as the one in javascript snippet at step 5. Also, set the disabled attribute, e.g.

        <input id="form_submit" type="submit" value="Submit" disabled>

![Final form with reCAPTCHA](/images/recaptcha/recaptcha-final-6.png)

The [reCAPTCHA documentation](https://developers.google.com/recaptcha/) site describes more details and advanced configurations.

That is all, now you have reCAPTCHA wired up with LiveForm. Now, whenever a submission is made, LiveForm will check for spam using reCAPTCHA.
You can check a fully working version of reCAPTCHA on the [https://liveformhq.com](https://liveformhq.com/#contact) website
