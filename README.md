# Birch

# Table of Contents
* [How to get started](#how-to-get-started)
* [Themes](#themes)
* [How to Use a Component](#how-to-use-a-component)
* [List of Components](#list-of-components)
* [Breakdown of Components](#breakdown-of-components)
* [Helpful Tips](#helpful-tips)
* [Current Issues](#current-issues)

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

## How to use/switch themes

Themes are currently controlled with the app.scss file. This is located under src > assets > scss > app.scss .

Here you can change the first two imports to 'cl/cl-theme','cl/cl-components', 'unum/unum-theme', 'unum/unum-components accordingly.

### Theme SCSS files

The theme files are where the custom variables live. The theme component files are where custom classes have been created for specific components. When using a component in a template, there may be a need to reference the list of classes that can be found in this file as they will help with styling.

### Other SCSS files

The settings.scss file is where default variables provided by Foundations for Emails can be found.

# How to Use a Component
Each component is created under the **partials** folder. We have been commenting the start and end of each component to help the end user be able to read the final compiled HTML file easier.

From there, we create a page using a layout that displays variations of the component under the pages > components folder. Here, we declare the component using the Handlebars syntax. ie: {{> banner}}.

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

# Breakdown of Components
# Banner
The purpose of the banner component is to be able to easily add text, icons, and/or buttons in any combination/order.

The banner component is composed of three sections: 

* Top
* Middle
* Bottom

And has two classes:
* {{class}}
    * Used to make the banner reflect primary or secondary banner styling by adding the .primary-banner or .secondary-banner class.

* {{second-class}}
    * Used to add the .primary-banner__content or .secondary-banner__content to add needed padding to the content.

# Boxies
The purpose of the boxies component is to allow for/create a two column layout. 

The boxies component is composed of two sections:
* left-column
* right-column

There are no classes currently associated with boxies.

# Button
The purpose of button is to provide an action on the page.

The button is centered by default.

There are no sections associated with button at this time.

Button has three classes:
* {{href}}
    * allows you to easily add the website link that the button should direct you to

* {{class}}
    * currently used to define the color type of the button for styling purposes by adding .primary-button or .secondary-button.

* {{buttonText}} 
    * used to add the text to be read on the button.

# Contact Card
The purpose of the contact card component is to offer an enhanced email signature that includes an image and detailed contact information.

There are no sections for this component.

There are 12 classes for the contact card component:
* {{class}}
    * used so that the class **'.contact-card'** can be added for styling purposes

* {{second-class}}
    * used so that **'.contact-card__column'** can be added for styling purposes

* {{imageUrl}}, {{imageUrl2}}, {{imageUrl3}}
    * allows you to insert icons or images into the component

* {{altText}}, {{altText2}}, {{altText3}}
    * allows you to add alt text, associated with the image you add to the component

* 4 classes are used to insert text, with the class name suggesting what should be added:
    * {{name}}

    * {{title}}

    * {{email}}

    * {{number}}

# Copyright
There are two copyright components. One is setup for Colonial Life and the other for Unum.

# Divider
The purpose of the divider component is to allow for the '•' character to be added to the footer nav. 

There are no classes or sections associated with this component.

# Footer Nav
The purpose of the footer nav is to allow for an additional menu, other than the products, to the footer. In previous designs, this has included links to 'Email Us', 'Login', and 'Call Us'.

The footer nav has six classes:

* {{menuHref}}, {{menuHref2}}, {{menuHref3}}
    * creates the link to wherever the item should direct you to

* {{menu1}}, {{menu2}}, {{menu3}}
    * this allows you to add the text to the item associated with the link.

# Footer
Footer takes any of the following components: 

* Copyright
* Footer-Nav
* Product-Nav
* Social Media

The footer also has one class:
* {{class}}
    * this gives the footer a class of "primary-footer" or whatever option would be needed

# Header
The purpose of the header is to include a logo, sub-brand name, and an optional "sign-in" or other call to action link.

The header may need to end up being split up into 3 "inline block" sections but for now we do not have it set up this way. 

The header has 8 classes:
* {{class}}
    * gives the header a class of "primary-header"
* {{logoUrl}}
    * where you want the logo to take you when clicked
* {{logoImage}}
    * path to the image file
* {{logoImageAlt}}
    * to add alt text to the image
* {{brand}}
    * allows you to add to text for the subbrand
* {{clickerUrl}}
    * where you want the call to action link to take you when clicked
* {{clickerColor}}
    * defines the text color of the link
* {{clickerText}}
    * allows you to enter the text of the link

# Hero Image

# Inline Images

# Product Nav
There are two versions of the Product Nav component. One is setup for Colonial Life, while the other is for Unum. The links to products have been setup to go to the appropriate product page of each website accordingly.

# Social Media
The purpose of this component is to allow for a social media "navigation" to be added to the page. In previous designs, this has only been added to the footer. 

This component has 4 classes:
* {{class}}

# Spacer
The purpose of the spacer component is to utilize the '< spacer >' tag that Foundation for Emails provides and add a class to easily change the spacer size.

There are no sections for the spacer component.

The only class for the spacer component is {{spacerSize}}. This takes a numerical value that can increase or decrease the space between two things.

# Helpful Tips

* Foundations for Emails provides some class names and HTML tags that can easily be added to your HTML. Check out their documentation here: https://foundation.zurb.com/emails/docs/ 
    * some of the main classes/tags we are using are:
        * text-left, text-right, text-center
        * "small" and "large" for media queries
        * < center > for a menu or button because centering any item is very difficult

* Note that SVG files can NOT be used for images. They do not show up on emails.

# Current Issues/ Final Thoughts

* A view in browser link component may need to be added. I have read a lot of documentation on whether this needs to be at the very top of the email or in the footer, and most recent dicussions suggest in the footer as this is slowly becoming less and less needed.

* The entire icon library will need to be added into Silverpop for use there

* The white secondary button for the Colonial Life theme still has a weird issue on hover where a small, thin line of the primary blue color shows. This button should only be used on a background color of blue, so it should remain hidden but if you use that button on a white background, you can see the issue on hover.

* I added a bunch of class names ( ie: {{class}}, {{second-class}}, etc. ) to components that may be unnecessary, after looking into it further with Kyle. His thought was we should be able to declare multiple classes under ONE {{class}}. Therefore if a component has the placeholder {{class}}, in our template we should be able to define class as multiple things. 

    So what was this: 

        {{> 
            contact-card
            class='contact-card'
            second-class="contact-card__column"
        }}

    would now be this: 

        {{> 
            contact-card
            class='contact-card contact-card__column'
        }}

Just some potential cleanup I wanted to make a note of.

* When a footer's background color is dark and the font color is light, a spam flag tends to get raised and the design of the footer is changed. May need to require all footers to have a white/light background color as a standard.