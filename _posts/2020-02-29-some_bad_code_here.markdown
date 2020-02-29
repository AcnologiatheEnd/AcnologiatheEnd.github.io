---
layout: post
title:      "Some bad code here"
date:       2020-02-29 06:40:12 +0000
permalink:  some_bad_code_here
---


I've messed up a little.

Basically, I was making a regular signup form on my rails app as shown

*class UsersController < ApplicationController
    def new
        @user = User.new
    end

    def create 
        if @user
            @user = User.create(userparams) 
            redirectto userpath(@user)
        else
            render newuserpath
        end
    end *
		

the form layout looked like this

*<%= formfor(@user) do |f| %>
    <%= f.label :name %>
    <%= f.textfield :name %>
    <br>
    <%= f.label :email %>
    <%= f.textfield :email %>
    <br>
    <%= f.label :password %>
    <%= f.passwordfield :password%>
    
    <%= f.submit %>
<% end %> *



Noticed anything? I sure as hell didn't. So, I tested it out and got a nice fat error regarding "<%= formfor(@user) do |f| %>". I spent a good 20 minutes trying to figure out what on gods earth did I do wrong. Turns out it was my awful create method. I guess I thought @user in my create method would magically assign to instance method with all the form data. 

Here's what I really meant to do:
def create 
        @user = User.new(user_params)
        if @user.valid?
            @user.save
            redirect_to user_path(@user)
        else
            render new_user_path
        end
    end 
		
1. 		create the user with the values from user_params
2. 		If the user is a valid user, save it and execute the code below
3. 		if the user isn't valid, do something else

The fact that error method was displaying the form made me think that the issue was with my poor ole new method. Well, I'm glad that's over with. Bugs can only stay if they pay rent. 








