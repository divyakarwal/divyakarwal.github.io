---
layout: post
title: "How to set-up Octopress Blog"
date: 2013-06-03 11:43
comments: true
categories: 
---
First of all sign up on github
1. click on "create a new repo" icon on right hand side upper corner.
2. write your user_name.github.io in the field "Repository name"
3. click on green color button "Create repository"
4. now scroll down and click on button "automatic page generator"
5. click on "continue to layouts"
6. last step is to publish your page by clicking on button named as "publish"

To set-up a blog on octopress if You are using Linux platform then you need to follow the steps below:

1. Install git.
	sudo apt-get install git
	git config --global user.name"your_user_name"
	git config --global user.email"your_email_id"
2. Install Ruby1.9.3 with RVM.
	curl -L https://get.rvm.io | bash -s stable --ruby
If by any chance this command wont work then run the following one.
	wget --no-check-certificate https://raw.github.com/joshfng/railsready/master/railsready.sh && bash railsready.sh
3. Now you have installed RVM, the next task is to install Ruby1.9.3
	rvm install 1.9.3
	rvm use 1.9.3
	rvm rubygems latest
To check the version of Ruby, run this command
	ruby --version
If it doesnt show Ruby 1.9.3, then again repeat the step 2 and 3.
4. Install dependencies
	gem install bundler
	rbenv rehash
	bundle install
	rake install
5. Deploying to Github Pages
	rake setup_github_pages
This will Ask you for your Github Pages repository url.
	rake generate
	rake deploy
	git add .
	git commit -m 'your message'
	git push origin source
6. Generating ssh key
	cd ~/.ssh
	ssh-keygen -t rsa -C "your_email@example.com"
7. Add your ssh key to github
	a) Open your github account
	b) Go to Account Settings
	c) Click "SSH Keys" on left navigation bar.
	d) Click on "Add Key"
	f) Now go back to your Terminal, go to Directory ".ssh"
		cd .ssh
	g) Open "id_rsa.pub" with text editor.
		gedit id_rsa.pub
	h) copy the content of the file and paste it in the big box named as "key" on your github account.
8. Test the key
	ssh -T git@github.com
if you get any prob in future regarding ssh key, like permission denied(public key), then run
	add-ssh
9. Setting up Blog
	git init
	rake deploy
	rake generate
	rake preview
	git add .
	git remote show origin
	git remote show octopress
	git remote rm octopress
	git remote rm origin
	git remote add origin git@github.com:your_user_name/your_user_name.github.io.git
	git remote -v
	git pull origin source
	git add .
	git commit -m "comment"
	git push origin source
	rake deploy
	





