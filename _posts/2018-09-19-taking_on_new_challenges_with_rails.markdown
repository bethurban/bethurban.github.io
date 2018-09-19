---
layout: post
title:      "Taking on new challenges with Rails"
date:       2018-09-19 21:23:13 +0000
permalink:  taking_on_new_challenges_with_rails
---


When diving into my Rails portfolio project, I was determined to go deeper and further with my code, and thus, my app, than I had in previous projects – or labs. Months of learning how SQL, ActiveRecord, Sinatra, and Rails build off of each other and/or work together gave me the confidence to venture into some new territory. But of course, that didn't come without some speed bumps.

I decided to build a hotel reservations app: Users could view available rooms and reserve them, and hotel managers, as admins, could peruse existing reservations and add rooms. Below are just a few of the new functionalities I decided to incorporate.

**User authentication**

My first hurdle came when trying to allow users to log in via Facebook – or log in using custom authentication. I had worked with OmniAuth in Flatiron labs, so I knew how to set up the Facebook side of things, and I had a lot of practice in labs building custom user authentications. The problem was how to combine the two in the SessionsController.

I knew that if a non-Facebook user logged in, the session id could be set by finding the User via the email address found in params.

```
class SessionsController < ApplicationController

def create

...

   else
      @user = User.find_by(email: params[:user][:email])
      if @user && @user.authenticate(params[:user][:password])
        session[:user_id] = @user.id
        redirect_to user_path(@user)
      else
        redirect_to signin_path
      end
   end
		
...

end
```

But if a user logged in from Facebook, a User would have to be found or created based on the :uid sent by Facebook. Plus, there would be no :phone_number, :password, or :password_confirmation params sent through, which I had required via User validations. My solution was to assign a dummy phone number (111-111-1111) and blank strings for the password and confirmation fields for Facebook users, thus making them valid users:

```
class SessionsController < ApplicationController

def create

...

     elsif params[:code]
        @user = User.find_or_create_by(uid: auth['uid']) do |u|
           u.name = auth['info']['name']
           u.email = auth['info']['email']
           u.image = auth['info']['image']
           u.phone_number = "111-111-1111"
           u.password = " "
           u.password_confirmation = " "
      end

      session[:user_id] = @user.id

      redirect_to user_path(@user)
			
...

end
```

**Uploading images**

Another feature I wanted to add was the ability for admin users to upload photos – a hotel manager, who had the ability to add a room for users to book, should be able to upload an image of the room.

I relied heavily on Google to figure this one out, first going to the [Rails documentation](https://guides.rubyonrails.org/form_helpers.html#uploading-files). That led me to a [helpful tutorial](https://code.tutsplus.com/tutorials/rails-image-upload-using-carrierwave-in-a-rails-app--cms-25183), plus two gems, [CarrierWave](https://github.com/carrierwaveuploader/carrierwave) and [MiniMagick](https://github.com/minimagick/minimagick).

CarrierWave made using `form_for` to upload an image easy. I added a `f.file_field` tag to my new room form after following the tutorial's guide to setting up CarrierWave's functionality.

```
<h1> Create a new hotel room </h1>

<p>
<%= form_for(@room) do |f| %>
  <% if @room.errors.any? %>
    <h2><%= pluralize(@room.errors.count, "error") %> prohibited this room from being saved:</h2>
    <ul>
      <% @room.errors.full_messages.each do |message| %>
        <li><%= message %></li>
      <% end %>
    </ul>
  <% end %>
  Room number: <%= f.text_field :room_number %><br>
  Nightly cost: $<%= f.text_field :cost %><br>
  Guest capacity: <%= f.text_field :capacity %><br>
  Image: <%= f.file_field :image %><br>
  <%= f.submit "Create hotel room" %>
<% end %>
</p>
```

MiniMagick allowed me to simply resize images as they were uploaded, providing thumbnails and standard sizes that could be used on the rooms index page and each room's show page.

```
class ImageUploader < CarrierWave::Uploader::Base

     include CarrierWave::MiniMagick
		 
...
		 
		 process resize_to_fit: [800, 800]

     version :thumb do
       process :resize_to_fit => [150, 150]
     end
		 
...
		 
end
```

In the end, my Rails portfolio project certainly took much longer than any of my previous projects, but I'm glad I took the time to challenge myself. I can confidently say that the app I built is by far my best yet, and the fact that I taught myself while building it makes completing it that much more satisfying.
