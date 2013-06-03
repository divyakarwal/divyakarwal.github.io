---
layout: post
title: "How to set-up Octopress Blog"
date: 2013-06-03 11:43
comments: true
categories: 
---
**First of all sign up on github**
* Click on "create a new repo" icon on right hand side upper corner.
* Write your user_name.github.io in the field "Repository name"
* Click on green color button "Create repository"
* Now scroll down and click on button "automatic page generator"
* Click on "continue to layouts"
* Last step is to publish your page by clicking on button named as "publish"

**To set-up a blog on octopress if You are using Linux platform then you need to follow the steps below:**

* Install git.
>	
>	{% codeblock %}
>	sudo apt-get install git
>	git config --global user.name"your_user_name"
>	git config --global user.email"your_email_id"
>	{%endcodeblock %}
* Install Ruby1.9.3 with RVM.
>	{% codeblock %}
>	curl -L https://get.rvm.io | bash -s stable --ruby
>{%endcodeblock %}
* If by any chance this command wont work then run the following one.
>{% codeblock %}
>	wget --no-check-certificate https://raw.github.com/joshfng/railsready/master/railsready.sh && bash railsready.sh
>{%endcodeblock %}
* Now you have installed RVM, the next task is to install Ruby1.9.3
>{% codeblock %}	
>	rvm install 1.9.3
>	rvm use 1.9.3
>	rvm rubygems latest
>{%endcodeblock %}
* To check the version of Ruby, run this command
>{% codeblock %}
>	ruby --version
>{%endcodeblock %}
* If it doesnt show Ruby 1.9.3, then again install RVM.
* Install dependencies
>{% codeblock %}
>	gem install bundler
>	rbenv rehash
>	bundle install
>	rake install
>{%endcodeblock %}
* Deploying to Github Pages
>{% codeblock %}
>	rake setup_github_pages
>{%endcodeblock %}
* This will Ask you for your Github Pages repository url.
>{% codeblock %}
>	rake generate
>	rake deploy
>	git add .
>	git commit -m 'your message'
>	git push origin source
>{%endcodeblock %}
* Generating ssh key
>{% codeblock %}
>	cd ~/.ssh
>	ssh-keygen -t rsa -C "your_email@example.com"
>{%endcodeblock %}
* Add your ssh key to github
*	a) Open your github account
*	b) Go to Account Settings
*	c) Click "SSH Keys" on left navigation bar.
*	d) Click on "Add Key"
*	f) Now go back to your Terminal, go to Directory ".ssh"
>{% codeblock %}
>cd .ssh
>{%endcodeblock %}
*	g) Open "id_rsa.pub" with text editor.
>{% codeblock %}
>gedit id_rsa.pub
>{%endcodeblock %}
*	h) copy the content of the file and paste it in the big box named as "key" on your github account.
* Test the key
>{% codeblock %}
>	ssh -T git@github.com
>{%endcodeblock %}
*if you get any prob in future regarding ssh key, like permission denied(public key), then run
>{% codeblock %}
>	add-ssh
>{%endcodeblock %}
* Setting up Blog
>{% codeblock %}
>	git init
>	rake deploy
>	rake generate
>	rake preview
>	git add .
>	git remote show origin
>	git remote show octopress
>	git remote rm octopress
>	git remote rm origin
>	git remote add origin git@github.com:your_user_name/your_user_name.github.io.git
>	git remote -v
>	git pull origin source
>	git add .
>	git commit -m "comment"
>	git push origin source
>	rake deploy
>{%endcodeblock %}	





