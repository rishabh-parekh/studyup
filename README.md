## Awesome websites built using Hugo, Bootstrap, Google Material Design and Wercker to deploy on AWS S3

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

    $git clone https://github.com/rishabh-parekh/liftoff.git site-1

  This will create a local copy of the website template in the folder `site-1`


Open the Website in **Atom** or any other editor.
The website has the following structure.

*Note: If you don't have tree, install tree using `brew install tree`

    $cd site-1
    $tree -L 1
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


### Step 2 Start the Hugo Server to serve the website

Let's start the local site from a **terminal** window
In the site-1 folder in the terminal window type

      $hugo serve

This will start you site and you can go ahead open a browser window to `http://localhost:1313`


### Step 3: Change the config.toml

Hugo uses a simple top level config file to store all Site related data. You can add new site related data or modify existing one.

Snippet of the config.toml

      title = "The classroom that is always open"
      baseurl = "http://f9liftoff.io/"
      MetaDataFormat = "toml"
      paginate = 9 # To specify a multiple of 3
      disqusShortname = "" # optional
      copyright = "© Copyright 2016 F9LO, Inc. All Rights Reserved."
      theme="material-design"

      #
      # All parameters below here are optional and can be mixed and matched.
      #
      [params]
      # You can use markdown here.
      brand = "F9 LiftOff"
      topline = "Get the Boost"
      footline = "code with <i class='fa fa-heart'></i>"

Edit the config.toml in Atom (or your fav editor) and Go ahead and change the brand name, title, baseurl copyright message etc.

As soon as you save, Hugo will automatically refresh the website.

Check the website in the browser window with the new Title, description etc.

### Step 4: Finalize your layout, images, content with the customer

In this step you will get all the images, content, logo from the customer and finalize the layout with your customer. Assuming you have already done that proceed to Step 5

### Step 5: Change the Logo and Images

The logo and all images are stored in the static/img folder
The logo shown in the front page is based on the config.toml's **customer** parameter

      customer = "lologo"

This is configured in the layouts/partials/header.html file

      <div class="vert-text">
      <!--logo start-->
         {{if .Site.Params.customer}}
            <a href="#intro"><img src="{{.Site.BaseURL}}/img/{{.Site.Params.customer}}.png" class="logo" alt="logo"> </a>
         {{end}}

Let's say your customer name is petstore (all lowercase). Create a logo file `petstore.png` and drop it in the `img` folder

Similarly all images from the customer which are going to be used throughout the content will be stored in the `img` folder (more later when we build the content)


### Step 6: Change the Top Level Menu

The top level menus are configured in the `layout/partials/header.html`
The menus in the template are `about`, `products`, `approach`, `customers`, `team`, `contact`, `blog`. You can add new menus, delete menus, or change existing existing.

Each menu has icons. By default the Hugo Icons which are configured in layout/css/hugofont.css

You can use Google Icons from the [Google Material Icons](https://design.google.com/icons/). Uncomment the Menu using Google Style Icons, and comment out Menus using Hugo Style Icon.

The Google Icons use Style Sheets from MaterialCSS which is included at the top of the header.html
[http://materializecss.com/getting-started.html](http://materializecss.com/getting-started.html)


        <!-- All Google Style Icon Buttons -->
        <!--https://design.google.com/icons/ -->
        <!--
        <a href="#about" class="btn btn-primary btn-lg">About Us <i class="material-icons">account_balance</i></a>
        <a href="#products" class="btn btn-primary btn-lg">Products <i class="material-icons">account_box</i></a>
        <a href="#approach" class="btn btn-info btn-lg">Approach <i class="material-icons">account_circle</i></a>
        <a href="#customers" class="btn btn-info btn-lg">Customers <i class="material-icons">favorite_border</i></a>
        <a href="#team" class="btn btn-dark btn-lg">Team <i class="large material-icons">face</i></a>
        <a href="#contact" class="btn btn-dark btn-lg">Contact <i class="material-icons">group</i></a>
        <a href="#blog" class="btn btn-dark btn-lg">Blog <i class="material-icons">info</i></a>
        <!--- End Google Buttons -->

        <!-- All Hugo Style Icon Buttons -->
        <a href="#about" class="btn btn-dark btn-lg">About Us <i class="icon-idea"></i></a>
        <a href="#products" class="btn btn-dark btn-lg">Products <i class="icon-arrow-down"></i></a>
        <a href="#approach" class="btn btn-dark btn-lg">Approach <i class="icon-rocket2"></i></a>
        <a href="#customers" class="btn btn-dark btn-lg">Customers <i class="icon-talking"></i></a>
        <a href="#team" class="btn btn-dark btn-lg">Team <i class="icon-circlestar"></i></a>
        <a href="#contact" class="btn btn-dark btn-lg">Contact <i class="icon-circlestar"></i></a>
        <a href="#blog" class="btn btn-dark btn-lg">Blog <i class="icon-circlestar"></i></a>


### Step 7: Change the Rest of Header
The header is configured in the `layout/partials/header.html`
By default we have include multiple CSS from bootstrap, materializecss. You can also include custom CSS and Javascript files here.


### Step 8: Change the Footer
The footer is configured in the `layout/partials/footer.html`
Here you can add the twitter, github, facebook, instagram, snapchat social media icons.

You can use Font Awesome [http://fontawesome.io/examples/](http://fontawesome.io/examples/) which has all the social media icons like Facebook or you can use Hugo Icons for twitter and Github. The Font Awesome CSS is already included in the header.html


      <li><a href="https://twitter.com/{{.Site.Params.twitter}}" class="icon-twitter icon-2x"></a></li>
      <li><a href="https://github.com/{{.Site.Params.github}}" class="icon-octocat icon-2x"></a></li>
      <li><a href="https://github.com/{{.Site.Params.facebook}}"><i class="fa fa-facebook fa-2x" aria-hidden="true"></i></a></li>

The values for the social media icons are from the config.toml
Edit the config.toml to add social media handles

         twitter = "f9lo" # optional
         github = "f9lo"
         facebook = "f9lo"


### Step 9: Change and Add new content

Hugo uses Markdown content and applies templates based on rules you have defined for rendering the markdown.

In this template, we have used partials for different `type` of markdown content and included the partials in `index.html` to render the complete page.

The `index.html` has all the different partials .. Here is a snippet.
Any page which matches a particular partial will be rendered at the position. For e.g. If I have a content of type `approach` it will be rendered by approach.html


      {{ partial "header.html" . }}

          <div id="main">
              <!-- Intro -->
              {{ partial "home.html" .}}
              <!-- /Intro -->

              <!-- Point -->
              {{ partial "products.html" .}}

              <!-- /Point -->

              <!-- Point -->
              {{ partial "approach.html" .}}

              <!-- /Point -->

The partials have rules which file the site content using the `type` Front matter

For e.g. here is the approach.html partial which filters and applies the style sheet only for `.Data.Pages` of `Type` equals `Approach`

      {{ $baseurl := .Site.BaseURL }}
      {{ range where .Data.Pages "Type"  "Approach" }}
      {{ partial "counterpoint.html" .}}

      {{ end }}


The partial `counterpoint.html` renders the content in black with white background. The partial `point.html` will render the content in white with green background. The icons and other parameters can be provided in the Front matter and the template will use them as `Params.icon`


      {{ $baseurl := .Site.BaseURL }}
      <div id="{{ .Type }}" class="counterpoint">
        <div class="container">
          <div class="row">
            <div class="col-md-6 col-md-offset-3 text-center">
              <i class="lead-icon {{ .Params.icon }}"></i>

              <h2>{{ .Title }}</h2>
              <div class="lead">
                {{ .Content }}
              </div>
            </div>
          </div>
        </div>
      </div>


In order to add new content under the content directory, use the hugo command

    hugo new page/p1.md
    hugo new page/p2.md

    hugo new post/po1.md
    hugo new post/po2.md

This will create new contents which can be pages, posts or any section you want to define. You will have to edit the front matter for each of the page to match the appropriate `partials`.

For example: I want to use the partial `layouts/partials/approach.html` for my post po1.md

Edit the po1.md Front matter and change the type = "Approach" and provide the icon you would like to use.


      +++
      Categories = ["Post"]
      Tags = ["registration"]
      date = "2016-03-15T16:23:23+09:00"
      title = "Fast &amp; Powerful"
      type = "Approach"
      weight = 1


      icon = "icon-rocket"
      affiliatelink = "http://www.my-book-link.here"
      recommendedby = "my Mother"

      +++

      Hugo is written for speed and performance. Great care has been
      taken to ensure that Hugo build time is as short as possible.
      We’re talking milliseconds to build your entire site for most setups.

The Hugo template generator will automatically use the approach.html template to render this.

Include this as partials in `index.html` as

    {{ partial "po1.html" .}}

You can duplicate new partials or modify existing partials and change the `type`


### Step 10: Change the Icons

Icons are fonts, and this template uses variety of font icons. The corresponding CSS files and (Javascript) files are already included in the header.html

1. Bootstrap fonts
2. Font Awesome
3. Google Material fonts
4. Hugo Fonts (default)


In order to use any of the font icons, you have to specify which font you are using in the specific HTML tag.

Icons can be passed as parameters to partials using the Front Matter of the Markdown content. And they can be used within the template.

Here is an example of Params.icon being passed to point.html params. Any content page which uses this partial will have to provide the Param icon in the front matter.

    <i class="lead-icon {{ .Params.icon }}"></i>


e.g. Hugo fonts
     icon-rocket, icon-octocat etc are icons from the hugofont.css file in the static/css/ folder.

e.g. Bootstrap Fonts

    [http://getbootstrap.com/components/](http://getbootstrap.com/components/)

    Bootstrap fonts have to be in `span` html component. The Bootstrap font css is included in the header.html

    <button type="button" class="btn btn-default" aria-label="Left Align">
      <span class="glyphicon glyphicon-align-left" aria-hidden="true"></span>
    </button>

e.g. Google Material fonts and MaterialCSS

    Google Material Fonts [https://design.google.com/icons/](https://design.google.com/icons/) are based on Material design. But to use different colors and sizes, you have to use the MaterialCSS from [http://materializecss.com/](http://materializecss.com/)

    The header.html has already includes for both the Google Material Fonts and MaterialCSS

    <!-- IF you are using Google Icons the use the following two stylesheets -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">

    <!-- MaterialCSS -->
    <link href="{{.Site.BaseURL}}/css/materialize.min.css" type="text/css" rel="stylesheet" media="screen,projection"/>
    <link href="{{.Site.BaseURL}}/css/style.css" type="text/css" rel="stylesheet" media="screen,projection"/>

    To use the material fonts and css, here is an example using the menu items. This is commented in the header.html

    <a href="#about" class="btn btn-primary btn-lg">About Us <i class="material-icons">account_balance</i></a>
    <a href="#products" class="btn btn-primary btn-lg">Products <i class="material-icons">account_box</i></a>
    <a href="#approach" class="btn btn-info btn-lg">Approach <i class="material-icons">account_circle</i></a>
    <a href="#customers" class="btn btn-info btn-lg">Customers <i class="material-icons">favorite_border</i></a>
    <a href="#team" class="btn btn-dark btn-lg">Team <i class="large material-icons">face</i></a>
    <a href="#contact" class="btn btn-dark btn-lg">Contact <i class="material-icons">group</i></a>
    <a href="#blog" class="btn btn-dark btn-lg">Blog <i class="material-icons">info</i></a>
    <!--- End Google Buttons -->



e.g. Font Awesome fonts

    <!-- If you are using Font Awesome Fonts -->
    <script src="https://use.fontawesome.com/06e55527a5.js"></script>

If you want to use a specific font e.g. Facebook Icon, and it is not available in Hugo font, but available in Font Awesome, the you can use the font awesome font e.g.

      <li><a href="https://twitter.com/{{.Site.Params.twitter}}" class="icon-twitter icon-2x"></a></li>
      <li><a href="https://github.com/{{.Site.Params.github}}" class="icon-octocat icon-2x"></a></li>
      <li><a href="https://github.com/{{.Site.Params.facebook}}"><i class="fa fa-facebook fa-2x" aria-hidden="true"></i></a></li>


### Step 11: Add content with Images layouts

In this template if you want to create a layout with side by side Image and content, you can use the partials
image.html

    {{ range where .Data.Pages "Type"  "SometypeOfPage" }}
      {{ {{ partial "image.html" . }}
    {{ end }}

Similar logic is used in the `products.html`. In the Markdown products.md, you have to specify the image to be used

    +++
    Categories = ["registration","workshop"]
    Tags = ["registration"]
    date = "2016-03-15T16:23:23+09:00"
    title = "Products"
    type = "Products"
    weight = 1
    image = "product.png"

The template will render two columns, one on the left with the image and the right with the content

      <div id="{{ .Type }}" class="point">
        <div class="container">
          <div class="row">
            <i class="point-icon {{ .Params.icon }}"></i>
          </div>
          <h2>{{ .Title }}</h2>
          <div class="row">
            <div class="col-md-4 "><img src="/img/{{ .Params.image }}" alt="{{ .Type }}" style="width: 100%;"/></div>
            <div class="col-md-4 col-md-offset-3 text-center">
              <div class="lead">
                {{ .Content }}
              </div>
            </div>
          </div>
        </div>
      </div>
      {{ end }}

### Step 12: Add content with Blog Post and Detailed Pages

The partials blog.html renders cards which are posts of the same type e.g. blogs in this case. You can use this example to render bunch of cards for similar content, events, blog posts etc. The details are provided by clicking on the blog

There is pagination built in the page.


      {{ $baseurl := .Site.BaseURL }}
      <div id="blog" class="point">
        <div class="container">
          <div class="section">
            <div class="row">
                {{ range where .Data.Pages "Type"  "blog" }}
                <div class="col s6">
                  <div class="card-panel hoverable blue-grey darken-1">
                    <div class="card-content white-text">
                      <!-- Card Content -->
                      <h4><a href="{{ .Permalink }}">{{ .Title }}</a></h4>
                      <p>{{ .Summary }}</p>
                      <p>
                      {{if .Params.tags }}
                        {{ range $index, $tag := .Params.tags }}
                          <a href="{{$baseurl}}/tags/{{ $tag | urlize }}/">#{{ $tag }}</a>
                        {{ end }}
                      {{end}}
                      </p>
                    </div>
                  </div>
                </div>
                {{ end }}
            </div>
            {{ partial "pagination.html" .Paginator }}
          </div>
        </div>
      </div>


### Step 13: Add Shortcodes for Youtube, Google Maps, Google Slides.

A shortcode is a simple snippet inside a content file that Hugo will render using a predefined template.

Example short codes include in the template are `youtube` `speakerdeck` `googleslides` `googlemaps`

In order to use the short code, simply call the shortcode with the parameter

e.g.

{{< googlemaps "https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d188704.9092281745!2d-83.23929000800298!3d42.35287957603575!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8824ca0110cb1d75%3A0x5776864e35b9c4d2!2sDetroit%2C+MI!5e0!3m2!1sen!2sus!4v1468784710190" >}}



### Step 14: Change the Theme/Colors

Themes and Colors are provided in the CSS included in the template. You can change the themes, by adding new styles in the css folder or specifying new styles for existing style.css


Use the Chrome Developer Tools to see what is the style being applied on a particular element and then change it.

You can download new themes for Hugo from [http://themes.gohugo.io/] (http://themes.gohugo.io/) and follow the instructions to apply the themes.


### Step 16: Add the new site to Git

The next step is to publish your website. You can save you website to Git Source control.

In step 1, you have already cloned this repo using the command
    $git clone https://github.com/rishabh-parekh/liftoff.git site-1

Create a new repository in https://github.com/<your user name> called as site-1

Next, add these changes to the new repo

      $git add .
      $git commit -m "Initial Commit of the new site-1"
      $git push https://rishabh-parekh@github.com/rishabh-parekh/site-1 master

This will add all the files under user name rishabh-parekh/site-1


### Step 17: Create a Wercker App and Target

The next step is to build this final site and deploy it automatically if any content changes.

[http://doc.lijun.li/web-hugo-aws-s3-wercker.html] (http://doc.lijun.li/web-hugo-aws-s3-wercker.html)

For this we will use wercker [wercker.com](www.wercker.com)

Create a wercker account and link it to your github. This is a one time Prerequisites.

Login to the wercker dashboard and create a new app [https://app.wercker.com/#applications/create](https://app.wercker.com/#applications/create)


Wercker will guide you through the steps, of auto configuration. Use the defaults for checking out the code.

### Step 18: Create a AWS S3 bucket to host your website

Login to AWS Console [https://console.aws.amazon.com](https://console.aws.amazon.com)

Create a new s3 bucket at [https://console.aws.amazon.com/s3/home?region=us-east-1] (https://console.aws.amazon.com/s3/home?region=us-east-1)

Name the new s3 bucket the same name as the site you want launch

<img src="/img/internal/aws-1.png" alt="AWS Config" style="width: 100%;"/>


### Step 15: Change the Wercker Config to deploy it automatically
We have a wercker.yml file already included in the template repository.

      box: debian
      build:
        steps:
          - arjen/hugo-build:
              version: "0.15"

      deploy:
        steps:
          - s3sync:
              key-id: $AWS_ACCESS_S3_KEY_ID
              key-secret: $AWS_ACCESS_S3_KEY_SECRET
              bucket-url: $AWS_S3_BUCKET_URL
              source_dir: public/
              opts: --acl-public --add-header=Cache-Control:max-age=3600

This wercker file takes the Environment variables defined in the Wercker Project.

The three AWS parameters in the Wercker Environment Variables. `AWS_ACCESS_S3_KEY_ID,AWS_ACCESS_S3_KEY_SECRET,AWS_S3_BUCKET_URL`

<img src="/img/internal/wercker-1.png" alt="Wercker Config" style="width: 100%;"/>


### Step 18: Kick start and watch you website

You are ready to kick start you website.

Open the browser and bring up the AWS_S3_BUCKET_URL

You can give a proper domain name using the instructions here
[https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html#website-hosting-custom-domain-walkthrough-domain-registry] (https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html#website-hosting-custom-domain-walkthrough-domain-registry)
