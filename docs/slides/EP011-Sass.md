
<!-- .slide: data-state="title" -->

# Mastering Code
Sass

>> Author Notes:
- If you're applying for a job, it's really important that you know how to work with CSS pre-processors because you'll probably be asked about them during interviews. It's a better way to write CSS, but more importantly it will make you more marketable, so let's take a peek at what Sass is, why you need it and then look at an example of converting css to Sass.

---

## Sass

<ul>
  <li class="fragment">`.scss` vs `.sass`</li>
  <li class="fragment">Ruby vs NodeSass</li>
  <li class="fragment">Variables, nesting, partials, mixins</li>
</ul>

>> Author Notes:
Sass stands for syntactically Awesome Stylesheets, but more importantly it's a way of writing CSS that is similar to CSS, but gives you some additional capabilities. Here's some of the essential things you need to know about the language.

1. First there are two versions and therefore two file extensions scss is the newer version that is more popular and looks almost exactly like regular CSS with some additional features, which is a great way to learn. As a matter of fact, you can use perfectly normal css in an scss file. The .sass file extension requires you to use an older sytanx where spaces and indentation is relevant. If you're getting started. scss is the better way to go.

2. Since it is a processed language, your browser doesn't understand those files without translation. There are two main ways of translating sass. You can use Ruby, which is the original language and a lot harder to install, or you can use nodesass, which is a nodejs package. nodesass is faster at processing, so it's the better way to go, although it always lags a bit behind ruby in terms of development.

3. The main features that sass gives you are variables, nesting, partials and mixins, which are like functions. You should know that a lot of these features are becoming available in newer versions of CSS. Let's take a look at how we can use these to improve the way we write CSS.

---
## Resources
<ul>
  <li><a href="http://sass-lang.com/">Sass Language</a> | <a href="https://css-tricks.com/snippets/sass/">Sass Snippets on CSS Tricks</a></li>
  <li style="list-style: none;">
    <ul>
      <li style="margin-bottom: 10px"><a href="https://www.linkedin.com/learning/sass-essential-training">Sass Essential Training</a></li>
      <li style="margin-bottom: 10px"><a href="https://www.linkedin.com/learning/building-a-responsive-single-page-design-with-sass">Building a Responsive SPD with Sass</a></li>
      <li style="margin-bottom: 10px"><a href="https://www.linkedin.com/learning/responsive-css-workflow-with-sass-bourbon-and-susy">Sass, Bourbon, and Susy</a></li>
      <li style="margin-bottom: 10px"><a href="https://www.linkedin.com/learning/responsive-css-with-sass-and-compass">Responsive CSS with Sass and Compass</a></li>
    </ul>
  <li style="list-style: none; font-size: 1.3rem;"><a href="hhttps://www.linkedin.com/in/planetoftheweb">linkedin.com/in/planetoftheweb</a> | <a href="https://www.twitter.com/planetoftheweb">@planetoftheweb</a> | <a href="https://www.linkedin.com/learning/instructors/ray-villalobos">courses</a> | <a href="https://raybo.org">blog</a></li>
</ul>

>> Author Notes:
- Here's some pages where you can get more information about working with the developer tools as well as some related courses with information on developer tools. If you have some ideas for this weekly series, maybe you want to share with me some questions you've been asked or have asked in interviews connect with me in LinkedIn or just about any social media network like twitter or github @planetoftheweb.


```_base.scss

body { font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; font-size: 1.5rem; margin: 0; padding: 0; }
.container { width: 80%;  margin: 0 auto; }

```

```_mixins.scss
@mixin btn($color) {
  display: inline-block;
  padding: 6px 12px;
  font-size: 1rem;
  line-height: 1.42857143;
  outline: none;
  text-align: center;
  cursor: pointer;
  background-image: none;
  border: none;
  border-radius: 4px;
  color: #fff;
  background-color: $color;
  position: relative;
}

.btn.hamburger {
	@include btn($orange);
  margin: 10px auto;
  display: none;
  @media all and (max-width: 600px) {
    display: block;
  }
}
```

```_nav.scss
.nav {

  .container {
    max-width: 1200px;
    @media all and (max-width: 600px) {
      width: 100%;
    }
  }

  .navbar {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    background-color: $beige;

    @media all and (min-width: 600px) {
      flex-direction: row;
      background: none;
    }

    &.hidden {
      @media all and (max-width: 600px) {
        display: none;
      }
    }

    .btn {
      margin: 0 auto;
      text-align:  center;
    }

    a {
      color: $orange;
      font-weight: 600;
      font-size: 1.2rem;
      text-decoration: none;
      padding: 16px 9px;
      white-space: nowrap;
      text-align: center;
    }

    a:hover {
      color: darken($orange, 20);
      @media all and (max-width: 600px) {
        background-color: $beige;
      }
    } /* hover */
  }
}
```

```_variables
$green: hsl(175, 49%, 42%);
$orange: hsl(15, 80%, 50%);
$beige: hsl(45, 41%, 92%);
```


```styles.scss
@import "variables";
@import "base";
@import "mixins";
@import "navigation";
```
