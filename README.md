## Awesome websites built using Hugo and Bootstrap and deployed using Wercker. 

### Prerequisites
*These steps are one time and it is assumed that you are using MacOS*

1. Install Hugo. [https://gohugo.io/](https://gohugo.io/) 
   You might have to first install homebrew (and Ruby, rbenv). Hugo is installed using a simple brew command
    
        brew update && brew install hugo
2. Install Git Cli for Mac from [https://git-scm.com/download/mac](https://git-scm.com/download/mac)
3. Create a GitHub Account if you don't have one [https://github.com](https://github.com)
4. Create a Wercker Account if you don't have one [https://app.wercker.com](https://app.wercker.com)
         


## How to build new websites using this template. 
This template website uses Hugo(https://gohugo.io/), the template engine for fast, static websites. 

*Why Hugo*

For static websites, which change frequently, don't need heavy software like Wordpress or Jenkyll. You can use Hugo which is based on Go Templates. 


### Step 1: Clone the template

   Let's say you are starting a new site `site-1`
    
    git clone https://github.com/rishabh-parekh/liftoff.git site-1
  
  This will create a local copy of the website template in the folder `site-1` 

The website has the following structure. 
*Note: If you don't have tree, install tree using `brew install tree`

    tree -L 1
    .
    ├── archetypes
    ├── config.toml
    ├── content
    ├── data
    ├── layouts
    ├── static
    └── themes

The content for the website is stored in the content folder in **Markdown** [https://daringfireball.net/projects/markdown/] (https://daringfireball.net/projects/markdown/) 

You can create new content in the content folder (more details in later steps) 
The static folder has all the static CSS, Images, Logos, Fonts. 

The site specific layouts are stored in the layout folder. But you can use Themes, which are applied to the content. In the themes folders are different Hugo Themes, we have couple of them downloaded in the template. You can preview and download more themes from the Hugo website. [http://themes.gohugo.io/](http://themes.gohugo.io/)


### Step 2: Change the config.toml 

Hugo uses a simple top level config file to store all Site related data. You can add new site related data or modify existing one. 

Snippet of the config.toml


### Step 3

Change the Logo

### Step 4


