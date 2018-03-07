# Birch

# How to get started
Go to [GitHub](https://github.com/unumux/birch) to clone the repo.

Once you have the project locally, run ' npm i ' to install any dependencies needed for the project.

To start running the project locally, run ' npm start '.

Once you have the program running, you should see a list of Email templates. Most of these are default templates provided by Foundations for Emails, which we have left as reference points for research on creating our own templates. Feel free to review a few of these. 

Our project has mostly been testing under the Testing Template link.

You will also see a list of Email components, which was previously created as a testing ground for each individual component. As they were finalized, their styling & layout was stripped for template purposes, so most of these links you may not find much of any information.

# Themes

Currently there are two themes:
* Colonial Life
* Unum

**Please Note:** There will be a need for a Paul Revere theme to be created at some point as well.

## How to switch themes

Themes are currently controlled with the app.scss file. This is located under src > assets > scss > app.scss .

Here you can change the first two imports to 'cl/cl-theme','cl/cl-components', 'unum/unum-theme', 'unum/unum-components accordingly.

### Theme SCSS files

The theme files are where the custom variables live. The theme component files are where custom classes have been created for specific components. When using a component in a template, there may be a need to reference the list of classes that can be found in this file as they will help with styling.

### Other SCSS files

The settings.scss file is where default variables provided by Foundations for Emails can be found.

# List of Components:
* [Banner](#banner)
* [Boxies](#boxies)
* [Button](#button)
* [Contact Card](#contact-card)
* [Copyright](#copyright)
* [Divider](#divider)
* [Footer Nav](#footer-nav)
* [Footer](#footer)
* [Header](#header)
* [Hero Image](#hero-image)
* [Inline Images](#inline-images)
* [Product Nav](#product-nav)
* [Social Media](#social-media)
* [Spacer](#spacer)
* [Sub Brand](#sub-brand)

# How to Use a Component
Each component is created under the **partials** folder. We have been commenting the start and end of each component to help the end user be able to read the final compiled HTML file easier.

From there, the component is given a component layout under the pages > components folder. Here, we declare the component using the Handlebars syntax. ie: {{> banner}}.

Now, the component is ready to be used in a template. We have been doing most of our testing in the pages > leststest.html file. 

This is where most of the "magic" will happen as the templates are where you add all of your components by declaring them with the Handlebars syntax.

## Using a Component in a Template

When first viewing the template, it can be overwhelming but the breakdown of each component is meant to be very versatile, interchangeable and easy to use.

Banner is a great example component to breakdown. 

If you view the banner component HTML under the partials folder, you will see it is divided into a top, middle, and bottom section. Any combination of these sections can be used when using the component in the template. You also do NOT have to use every section of the banner, in order for the component to work. 

The purpose of this component is to be able to insert a button, icon, or text in any particular order. So how do we do that?

First, we want to look at what, if any, classes are assigned to this component. Classes are listed in the partial file with the Handlebar syntax {{insert name}}. These classes have to be declared in the same Handlebars block that the component is first called, so for example like this:

{{#> banner 
    class="primary-banner" second-class="primary-banner__content"
}}

Note, you do NOT have to use every class provided but most of them were created because they are in fact needed.

You can also use {{add your generic class name}} as a way to add a new class to your component if needed.

Once we have declared all the classes in the {{}} block, we can start to insert what we want into each of our three sections. We do this by using the Handlebars inline block partial. Basically, it's kind of like inserting inline styling, but it allows us to enter actual content.

You have two options for how to insert content into these blocks: 

 1. Use raw HTML. Just write an h1 or p like you would in any other HTML file.

 2. Add another component, declare any classes it may need just as you did for the initial component.

 You add either option by using this syntax:

    {{#*inline "whatever the section was named in your partial file"}}
        --content goes here
    {{/inline "whatever the section was named in your partial file"}}

 So this is what it would look like for the banner component:

    {{#*inline "top"}}
        <h1 class="text-center">I am a heading</h1>
    {{/inline}}

    {{#*inline "middle"}}
        <p class="text-center">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Dolor blanditiis soluta error ad dolorem, culpa illum ex architecto tempora omnis laudantium hic facilis iure velit quia corrupti.</p>
    {{/inline}}

    {{#*inline "bottom"}}
        {{> button href="#" class='secondary-button' buttonText='I'm button text'}}
    {{/inline}}

Now, repeat that process for any other components needed for a template!

# Breakdown of Components
# Banner
The purpose of the banner component is to be able to easily add text, icons, and/or buttons in any combination/order.

The banner component is composed of three sections: 

* Top
* Middle
* Bottom

And has two classes:
* {{class}}
    * Used to make the banner reflect primary or secondary banner styling by adding the primary-banner or secondary-banner class.

* {{second-class}}
    * Used to add the primary-banner__content or secondary-banner__content to add needed padding to the content.

# Boxies

# Button


# Contact Card

# Copyright
There are two copyright components. One is setup for Colonial Life and the other for Unum.

# Divider

# Footer Nav

# Footer
Footer takes any of the following components: 

* Copyright
* Footer-Nav
* Product-Nav
* Social Media

# Header

# Hero Image

# Inline Images

# Product Nav
There are two versions of the Product Nav component. One is setup for Colonial Life, while the other is for Unum. The links to products have been setup to go to the appropriate product page of each website accordingly.

# Social Media

# Spacer

# Sub Brand

# Helpful Classes & HTML Tags
Foundations for Emails provides some class names and HTML tags that can easily be added to your HTML such as:

* class-names: text-left , text-center or text-right
* tags: < menu >, < container >, < wrapper >