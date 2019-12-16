---
layout: post
title:      "JS/Rails Final Project - SomeShop: An Ecommerce SPA"
date:       2019-12-16 18:24:31 -0500
permalink:  js_rails_final_project_-_someshop_an_ecommerce_spa
---


For my JavaSCript Project, we were tasked to create a Single Page Application(SPA), and after some thinking I decided to build an ecommerce website. I found out later that it might not have been the best idea for an SPA because there are usually several pages that make up an ecommerce site and I hit a lot problems trying to make it work. I also took this as an opportunity to try out some popular gems that I have never used before – devise, simple_form, faker, mini_magick and stripe. Even though it is a simple app, the birth of the app to its current state, it has been a constant struggle trying to reach outside of my wheelhouse of knowledge. I did not add a admin portal, perhaps in the future I will in order to add new products and retrieve statistics, but as for now, I believe it has more than satisfied the project requirements.
I started off with creating the models and migrations that I figured I needed, then set up the relationships. The general flow goes like this:
There are going to be products, the products can be added to the user’s cart as line items which indicate the quantity of each product in the cart. 
When the user decides to pay for what is in the cart, an order is created that associates the cart with the current user and a shipping address. 
The shipping address will be created if it does not exist, and associated to the user if not already. 
The user is then redirected to Stripe for payment processing and on completion is redirected back to the site.

**Devise:**

I used devise to set up the user registration and sessions controllers and views, I did not include any of the other bells and whistles it came with such as the :confirmable, :lockable, :timeoutable, :trackable and :omniauthable :recoverable modules. 
The cliffnotes for setting up:
#gemfile
gem 'devise'

$ rails generate devise:install

#config/environments/development.rb
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

$ rails generate devise MODEL
$ rails db:migrate

To customize the controllers, generate new controllers that inherit from Devise’s controllers and specify in routes.rb which controllers to use:
$ rails generate devise:controllers [scope]

```
  devise_for :users, controllers: {
    sessions: 'users/sessions',
    registrations: 'users/registrations'
  }
```
 
The new controller will be a subclass of your model/scope with commented out actions and methods that you are free to customize. For me, I had to update the create action to create a cart along with the user so there will be a cart available when the user signs in. I also changed the update_resource method to validate the current_password field when updating the user instance.  I also had to stray from the redirects in the original update action to render json back from the AJAX call instead. Lastly, I included the nested shipping address attributes to the params for the user if/when the user decides to add an address when updating their account. My User::RegistrationController ended up looking like this. 

```
class Users::RegistrationsController < Devise::RegistrationsController
  respond_to :json
  layout false
  before_action :configure_account_update_params, only: [:update]

  def create
    super
    if @user.save
      cart = @user.carts.create()
      session[:cart_id] = cart.id
    end
  end

  def update
    self.resource = resource_class.to_adapter.get!(send(:"current_#{resource_name}").to_key)
    prev_unconfirmed_email = resource.unconfirmed_email if resource.respond_to?(:unconfirmed_email)
    resource_updated = update_resource(resource, account_update_params)
    yield resource if block_given?
    if resource_updated
      set_flash_message_for_update(resource, prev_unconfirmed_email)
      bypass_sign_in resource, scope: resource_name if sign_in_after_change_password?
      render json: UserSerializer.new(resource)
    else
      clean_up_passwords resource
      set_minimum_password_length
      render json: UserSerializer.new(resource)
    end
  end

  protected

  def update_resource(resource, params)
    if resource.valid_password?(params[:current_password])
      resource.update_with_password(params)
    else
      resource.errors.add(:current_password, params[:current_password].empty? ? :blank : :invalid)
    end
  end

  def configure_account_update_params
    devise_parameter_sanitizer.permit(:account_update, keys: [shipping_addresses_attributes: [:street_1, :street_2, :city, :state, :zip_code]])
  end

end
```

The tricky thing about using devise is that it can get complicated very quickly when you want to do any sort of customization to the controllers outside of adding fields to the params. I tried to do as little tinkering as possible to avoid breaking anything.
For more information on how to get started with devise, check out their github page: https://github.com/plataformatec/devise
Active Storage:
At first I was thinking of using something like Paperclip or Carrierwave to manage the product images, but I learned that Paperclip is no longer being supported, and in that case, it might be a better idea to not rely too much on gems and just use what comes in the box with Rails – ActiveStorage. I’ve used ActiveStorage for attaching single images as user avatars in my last project, but was still not fully sure of how it worked, just dismissed it as Rails magic at the time. I had a few issues retrieving the image at and resorted to smashing buttons until it worked, not literally, but close enough.
This time I learned a little more about ActiveStorage – how to install, upload images, and display them with the help of the mini_magick gem, thanks to Youtube, specifically GoRails and Deanin’s channels:

GoRails: [https://youtu.be/jtKEP_lsLco](https://youtu.be/jtKEP_lsLco) - Rails 5.2 ActiveStorage Introduction

Deanin:  [https://www.youtube.com/watch?v=A23zCePXe74](https://www.youtube.com/watch?v=A23zCePXe74) - Active Storage For Multiple Images,  Validate & Resize, Ruby on Rails 5.2

I had to add an extra step in order to get the urls, send them in a response to an ajax request and update the DOM with the images with JQuery. To get the urls for the images, I had to use the rails_representation_url method by adding ‘include Rails.application.routes.url_helpers’ to my model.

**Stripe:**

Intially, I was not going to include payment processing since it was a complete mystery to me, but then I thought it would be a bit odd to have an ecommerce site that doesn’t take payment. After googling around for some time, I thought Stripe would be a good option, specifically Stripe Checkout where the checkout page was already built and all you’d have to do is redirect the customer over to their portal to process the payment. Easier said than done, it took a whole day of trials until it magically clicked and started working.
To set it up, you include this bit of code into your controller in order to create a Stripe::Checkout::Session object. 

```
Stripe.api_key = 'sk_test_4eC39HqLyjWDarjtT1zdp7dc'

session = Stripe::Checkout::Session.create(
  customer_email: 'customer@example.com',
  payment_method_types: ['card'],
  line_items: [{
    name: 'T-shirt',
    description: 'Comfortable cotton t-shirt',
    images: ['https://example.com/t-shirt.png'],
    amount: 500,
    currency: 'usd',
    quantity: 1,
  }],
  success_url: 'https://example.com/success',
  cancel_url: 'https://example.com/cancel',
)
```

Next, you add this to your js file:
<script src="https://js.stripe.com/v3/"></script>



After sending the AJAX call to that controller action, take the json response with the session_id created from the controller and redirect the user:

```
stripe.redirectToCheckout({
  // Make the id field from the Checkout Session creation API response
  // available to this file, so you can provide it as parameter here
  // instead of the {{CHECKOUT_SESSION_ID}} placeholder.
  sessionId: '{{CHECKOUT_SESSION_ID}}'
}).then(function (result) {
  // If `redirectToCheckout` fails due to a browser or network
  // error, display the localized error message to your customer
  // using `result.error.message`.
});
```

It can all be found in Stripe’s documentation: https://stripe.com/docs/payments/checkout/one-time

**history.pushState() and popstate:**

One of the biggest gripes I initially had about building my SPA ecommerce site is that I couldn’t navigate backwards or forwards between my js manipulated pages. Clicking the back button would just reload the page as it were before any of my js ran. I did some research to find some way to solve this and learned about history.pushState and popstate. With history.pushState, you can manipulate the url and save it in the browser history and listen for a change in the url with popstate. With these two, I completely changed how my application worked – instead directly coding in urls to send in my fetch calls, I first updated the url with pushState and then made my fetch calls by grabbing the url with location.href. In my main js file, I had my popstate listen for urls using regular expressions which called the functions for the fetch requests. 

```
  $(window).on('popstate', (e) => {
    if (!!location.href.match(/.*carts\/\d+/)) {
      fetchCart();
    } else if (!!location.href.match(/.*search\?keywords=/)) {
      getSearchResults();
    } else if (!!location.href.match(/.*categories\/\d+\/products$/)) {
      displayProducts();
    } else if (!!location.href.match(/.*categories\/\d+\/products\/\d+/)) {
      displayProduct();
    } else if (!!location.href.match(/.*users\/edit/)) {
      fetchAccount();
    }
  })
```
 
This wraps up on all the new things I’ve discovered while working on this project. I think I ran off the tracks a bit in tinkering with things outside of the actual lessons this project was meant to enforce, which I have a track record of doing, but I learn the best this way.

