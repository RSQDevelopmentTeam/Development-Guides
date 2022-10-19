![alt text](https://i.ibb.co/vsJ3jYY/header-copy.jpg)
### Limits & Defualts
`Images 4mb Limit`
`Container width is defaulted at max-width: 940px;`

### Learning and Feature Resources
- https://cms-library-beginner.finsweet.com/
- https://www.timothyricks.com/
- https://www.flow.ninja/free-resources
- https://university.webflow.com/integrations
- https://www.edgarallan.com/courses/webflow-for-teams/home
-
##### Sort, Filter, Load More
- https://cms-library.finsweet.com/

##### Make Text Responsive
- http://wizardry-technique.webflow.io/

##### Logins
- https://magic.link/posts/magic-webflow

##### Handling Images
- https://www.optily.co/#Feature

##### Real time Search
- https://www.jetboost.io/

#### Custom Sliders
- https://kenwheeler.github.io/slick/

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


![](https://i.ibb.co/Rhz9r6h/guide.png)
### Building Rules
1. Understanding of Class Management and apply it correctly.  (utility class should be used whenever possible and makes sense) Sometimes you will have some Utility class that you will just pass in and used with custom code other utilitys will be built in Webflow preferable on the style guide page. I.E  `All-body` ,`All-H1-6 tags`, `All-p`, `All-link` or `Article Btn`, `Global Btn`, `Special-Headline`
2. Let's keep all code that's related to a component inside of that component.
3. If a class/id is used with javascript prefix with `js-`, so it's clear it's being used by javascript to prevent breaking selectors etc..
4. Global code should be set in a global component like Nav or Footer, but I also have seen it as it's own symbol if no nav or footer is present.
5. BEM....One of the most import things to do in Webflow is to build your css styling with princples like BEM.
In the image below they are starting off with a prefix `c-` which stands for Components must like `js-` prefix to identify if it's being used with javascript.
![](https://i.ibb.co/BGcZNyg/Screen-Shot-2021-06-03-at-11-00-56-AM.png)

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


![](https://i.ibb.co/7Qx2Sc1/3159620-200-1.png)
### Using Custom CSS

Since we can't use compilers we should make sure all our prefix are good by running our css through `https://autoprefixer.github.io/`


### You I'll need custom CSS for these reasons
1. `pointer-events: none;`
2. Added states to children `parent:hover .child { }`
3. Besides `:hover,:visited,:focus,:pressed` you will need to added Pseudo-classes via custom code. I.E below
```
::selection,
::-moz-selection {
 background-color: #FA0000;
 color: #fff;
}
```
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||




![](https://i.ibb.co/y62rXLv/10-Column-grid.png)


### Building out a custom Grid
```
<style>
.grid-container {
   z-index: -1;
    position: fixed;
    display: flex;
    height: 100vh;
    width: 100%;
    max-width: 1440px; // Grid Layout Width
    margin: 0 auto;
    left: 0;
    right: 0;
    flex-flow: row wrap;
    justify-content: flex-start;
    align-items: stretch;
    pointer-events: none;
}

.grid-container .column {
    position: relative;
    min-width: auto;
    place-content: flex-start;
    flex-wrap: nowrap;
    align-items: flex-start;
    flex: 1 1 0%;
    border-style: none;
    border-width: 1px;
    height: 100%;
    padding-right: 20px; // Gutter
    padding-left: 20px; // Gutter
}

.grid-container .column .column-overlay {
    width: 100%;
    height: 100%;
    border-right: 1px solid #178df7;
    border-left: 1px solid #178df7;
}

</style>
```
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||



![](https://i.ibb.co/9WM7bd8/unity.png)
### Utility Classes Tools & Code

****Here is some scss to get your margins and padding utility ready.****
This will create margin and padding spacing for you. Grab the code below and go to https://beautifytools.com/scss-compiler.php to update your spacings.

```
$sizes: ("tiny": 1, "small": 2, "medium": 3, "large": 4, "xlarge": 5);
@each $name, $index in $sizes {
    .m-#{$name}-sides-space {
        margin: 0  8px * $index;
    }
}

@each $name, $index in $sizes {
    .m-#{$name}-full-space {
        margin: 8px * $index;
    }
}

@each $name, $index in $sizes {
    .p-#{$name}-sides-space {
        padding: 0  8px * $index;
    }
}

@each $name, $index in $sizes {
    .p-#{$name}-full-space {
        padding: 8px * $index;
    }
}
```
![](https://i.ibb.co/5c787sS/classes-copy.jpg)

### Utility Classes

```
.container {
  position: relative;
  padding-left: 10px;
  padding-right: 10px;
  max-width: 1440px;
}

.columns {
  margin-left: -0px; /* customizable */
  margin-right: -0px; /* customizable */
}

.column {
  padding-left: 0px; /* customizable */
  padding-right: 0px; /* customizable */
}

.m-tiny-sides-space {
	margin: 0 8px;
}

.m-small-sides-space {
	margin: 0 16px;
}

.m-medium-sides-space {
	margin: 0 24px;
}

.m-large-sides-space {
	margin: 0 32px;
}

.m-xlarge-sides-space {
	margin: 0 40px;
}

.m-tiny-full-space {
	margin: 8px;
}

.m-small-full-space {
	margin: 16px;
}

.m-medium-full-space {
	margin: 24px;
}

.m-large-full-space {
	margin: 32px;
}

.m-xlarge-full-space {
	margin: 40px;
}

.p-tiny-sides-space {
	padding: 0 8px;
}

.p-small-sides-space {
	padding: 0 16px;
}

.p-medium-sides-space {
	padding: 0 24px;
}

.p-large-sides-space {
	padding: 0 32px;
}

.p-xlarge-sides-space {
	padding: 0 40px;
}

.p-tiny-full-space {
	padding: 8px;
}

.p-small-full-space {
	padding: 16px;
}

.p-medium-full-space {
	padding: 24px;
}

.p-large-full-space {
	padding: 32px;
}

.p-xlarge-full-space {
	padding: 40px;
}

.object-fit {
  position: relative
  padding-top: 70%;
  overflow: hidden;
}

.object-fit img {
  object-fit: cover;
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  -webkit-transform: translate (-50%,-50%);
  -ms-transform: translate (-50%,-50%);
  transform: translate (-50%,-50%);
}

.hide-desktop {
  display: none;
}

@media(max-width: 767px) {
    .desktop-only {
        display: none;
    }
}

.tablet-only {
   display: none;
}

@media(max-width: 991px) {
    .tablet-only {
        display: block;
    }
}

@media(max-width: 767px) {
    .tablet-only {
        display: none;
    }
}
 .mobile-only {
    display: none;
}

@media(max-width: 767px) {
    .mobile-only {
        display: block;
    }
}

```
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

![](https://i.ibb.co/f92T85P/Screen-Shot-2021-06-02-at-3-19-09-PM.png)


#### Create a Style Guide Page
1. Sytle All H1-16, p, ul, li, link, button, span
2. Provide Margins and Padding setup classes. (I.E.) `8 * index` = (8px / 16px / 24px / 32px); I.E `p-tiny-space` = 8px, `p-small-space`= 16px, `p-medium-space`  = 24px, `p-large-space` = 32px

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


![](https://i.ibb.co/mGVLjm5/css-solid.png)
## Simple Classes
A simple class, on its own, represents a very specific behavior
```
.h₂ {
  background-color: blue;
}
```

## Compound Classes
A compound class is a series of simple classes that behave as a sum of their parts.
```
.h₂ {
  background-color: blue;
}
.o {
  background-image: url('bubbles.png');
}
```

## Complex Classes
 Complex classes have a common name that doesn't necessarily describe its make-up or behavior.
 ```
.water {
  background-color: blue;
  background-image: url('bubbles.png');
}
```

## Combo Classes
Combo classes are less common and behave a little like chemical reactions in that when two particular classes are combined (in any order), the resulting behavior is more than the sum of its parts.
```
.water {
  background-color: blue;
  background-image: url('bubbles.png');
}

.k {
  background-color: gray;
}

.water .k {
  background-color: red;
  background-image: url('explosion.png');
}
```


### Responsive Image Element Object

```
.object-fit {
   position: relative
    padding-top: 70%;
    overflow: hidden;
}

.object-fit img {
    object-fit: cover;
    position: absolute:
    top: 50%;
    left: 50%;
    transform: translate (-50%,-50%);
    width: 100%;
    height: 100%;
}
```


### Select Options Dropdown
``` bash
<script src="https://cdn.finsweet.com/files/cmslibrary-v1.8.js"></script>
<script>
const dropDownList = doucmnet.querySelectorAll('.js-drop-link');
dropDownList.forEach((e)) => e.setAttribute.('filter-by', e.outerText));
const myFilters = [
  {
    filterWrapper: '.js-dropdown-container',
    filterType: 'exclusive'
  }
];
fsComponent.filter({
  filterArray: myFilters
})
</script>
```
## Form Handling

``` bash
# simple snippet to handle form data on webflow. Will Need to be expanded apon, but this is a great start.
<script>
# Toggle Class
 function toggleClass(e) {
  if(e.value == null || e.value == "") {
      e.nextSibling.classList.remove('js-notEmpty');
      return false;
    } else {
      e.nextSibling.classList.add('js-notEmpty');
  }
}
# Error Checker Class
 function errorState(e, elm) {
  if(e.value == null || e.value == "") {
      e.parentElement.classList.add('js-error-state');
      elm.preventDefault();
    } else {
      e.parentElement.classList.remove('js-error-state');
  }
}

function validateForm() {
   const inputs = document.querySelectorAll('input.js-required');
   const submitButton =  document.querySelector("input[type='submit']");
    # Check on Key down if input field has value
   inputs.forEach((e,i) => {
      e.addEventListener('keydown',(elm) => toggleClass(e));
   });
   # Block Submission until all inputs meet requirement
   # Check on Key down if input field has value
   submitButton.addEventListener('click', (elm) => {
	inputs.forEach((e,i) => errorState(e,elm));
   });

   # Check if the body has been clicked.
    document.addEventListener('click', function (event) {
      inputs.forEach((e,i) =>  toggleClass(e));
    }, false);
  }

validateForm();
</script>
```

``` bash
<style>

.input-field-wrapper.js-error-state {
 border-color: red;
}

.input-field-wrapper .form-input-field:focus + .placeholder-text,
.placeholder-text.js-notEmpty {
   transform: translateY(-20px);
}

.placeholder-text {
  pointer-events: none;
  transition: transform 350ms linear;
}

input:-webkit-autofill,
input:-webkit-autofill:focus {
  -webkit-box-shadow: 0 0 0 50px #222222 inset;
  -webkit-text-fill-color: #8a8a8a;
}
</style>
```
