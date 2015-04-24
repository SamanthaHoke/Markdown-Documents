---

---


#Jekyll Notes
###A collection of notes for installing and running Jekyll


##Installation
 - Make sure Ruby is installed
	 - `ruby --version`
	 - If it is not installed go to the [Ruby Website](https://www.ruby-lang.org/en/downloads/)
 - `gem install bundler`
	 
 - In your repository, make a file called **Gemfile** with the following content:
   
		source 'https://rubygems.org'
		gem 'github-pages'
 - Run `bundle install`
	 - This may need the [Ruby Devkit](https://www.ruby-lang.org/en/downloads/)
	 - To install the devKit, follow the instructions [here](http://github.com/oneclick/rubyinstaller/wiki/Development-Kit)
		 - Download and unzip the Devkit
		 - Run ` ruby dk.rb init `
		 - Run ` ruby dk.rb install `
 
##Running
Run the following command in the root directory in the `gh-pages` branch.  
`bundle exec jekyll serve `  
>Serves on port 4000

##Update
Update with `bundle update` and `bundle update github-pages `

##FrontMatter
Place at the top of every markdown page:  

	---
	title: This is my title
	layout: post
	---
>Can leave space between `---` empty.

	

##Links
For full instructions, go to [Github page's instructions](https://help.github.com/articles/using-jekyll-with-pages/)

Also look at the [full list of help topics for Github Pages](https://help.github.com/categories/github-pages-basics/)