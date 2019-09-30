# Email Template Notes

### Before Starting Project
Please follow the Installation section on how to install the CLI & read up on [Foundation's Ink templating language](http://foundation.zurb.com/emails/docs/inky.html).

### Start Project
You can launch the project by running `npm run build` command. I always run this command while I build, so I can see the actual layout & don't forget to inline all CSS when testing. You can read more about the build command and others commands [Here](https://foundation.zurb.com/emails/docs/zurb-stack.html)

### Begin Building & Testing
I recommend building one section at time and QA it on Email On Acid.

### Assets
* Make sure all images are retina ready.
* Make sure images are hosted before testing.
* Make sure all images are compressed.

### Test List on Email On Acid

- iPad Air iOS 9 iOS 10
- iPad Mini iOS 9 iOS 10
- iPad Pro  iOS 9 iOS 10
- iPad Retina iOS 9 iOS 10
- iPhone 6 iOS 9 iOS 10
- iPhone 6+ iOS 9
- iPhone 6+ iOS 10
- iPhone 7 iOS 10
- iPhone 7+ iOS 10
- iPhone 7 iOS 11
- iPhone 7+ iOS 11
- iPhone 8 iOS 11
- iPhone 8+ iOS 11
- iPhone X iOS 11
- iPhone SE
- Apple Mail 9 OSX 10.9
- Apple Mail 10 OS X 10.10
- Outlook 2016 OSX 10.8
- Outlook 2016 Windows 10 ⚠️   **Note** Most likely to fail tests.
- AOL
- Chrome
- Windows 7
- Firefox OSX 10.10
- Firefox Windows 7
- IE 10 Windows 7
- IE 11 Windows 7
- Safari OSX 10.10

##### GMAIL
- Chrome Windows 7
- Firefox OSX 10.10
- Firefox Windows 7
- IE 10 Windows 7
- IE 11 Windows 7
- Safari OSX 10.10

##### OFFICE 265
- Firefox Windows 7 
- IE 11 Windows 7

##### OUTLOOK
- Chrome Windows 7
- Firefox OSX 10.10
- Firefox Windows 7
- IE 10 Windows 7
- IE 11 Windows 7
- Safari OSX 10.10

##### YAHOO
- Chrome Windows 7
- Firefox OSX 10.10
- Firefox Windows 7
- IE 10 Windows 7
- IE 11 Windows 7


### QA Process
Provide Email On Acid Share URLS for each template. Once the shared urls are approved. You can start internal QA.

- **Internal QA** - Send to internal QA seed list that's provided.
- **Client QA** - Send to Client QA seed list that's provided.

### Launch a test email to a seed list using Putsmail.
https://putsmail.com/
```
                           *     .--.
                                / /  `
               +               | |
                      '         \ \__,
                  *          +   '--'  *
                      +   /\
         +              .'  '.   *
                *      /======\      +
                      ;:.  _   ;
                      |:. (_)  |
                      |:.  _   |
            +         |:. (_)  |          *
                      ;:.      ;
                    .' \:.    / `.
                   / .-'':._.'`-. \
                   |/    /||\    \|
                        //||\\  
                 _..--"""````"""--.._
           _.-'``                    ``'-._
         -'                                '-

```

# Tips & Tricks when your like `¯\_(ツ)_/¯`

### Check Support - (ง'̀-'́)ง
https://www.campaignmonitor.com/css/

### Outlook Targeted CSS Conditional
The most common way to code Outlook targeted CSS is by placing an embedded stylesheet inside a conditional comment.
```
<!--[if mso]>
  <style type="text/css">
    ul {
      margin: 0 0 0 24px !important;
    }
  </style>
<![endif]-->
```

### Weird characters showing up that looks like a box with 1 & 0s in it.
The text needs to be sanitized by an editor like BBEdit where you can just paste in the editor and copy it again, or you can just type out the content instead.

### Outlook line-height issues
Make Outlook maintain any custom line heights defined, just add this declaration below
```
body { mso-line-height-rule: exactly; }
```
### Creating a working Bullet List
https://emailmonks.com/blog/email-coding/bullet-list-outlook-hacks/

### Font & Image Size
IOS devices have two main issues with font and image size:
Small font sizes are enlarged by default Email width is based on the largest element Font-size enlargement is usually not a critical problem, but in some cases it may cause some lines of text to be spliced potentially breaking your layout.


### images full width on Outlook 120dpi 

Add this as your html tag
```
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office" lang="en" xml:lang="en">
```

Put this in your header
```
<!--[if gte mso 9]><xml><o:OfficeDocumentSettings><o:AllowPNG/><o:PixelsPerInch>96</o:PixelsPerInch></o:OfficeDocumentSettings></xml><![endif]-->

```

### Support Background Images on outlook 2016
```html
<table cellpadding="0" cellspacing="0" border="0" width="100%">
    <tr>
      <td background="https://placekitten.com/g/800/100" style="background-size:cover" bgcolor="#fff" valign="top">
       <!--[if gte mso 9]>
         <v:rect xmlns:v="urn:schemas-microsoft-com:vml" fill="true" stroke="false" style="width:800px; height: 100px;">
         <v:fill type="frame" src="https://placekitten.com/g/800/100" color="#fff" />
         <v:textbox style="mso-fit-shape-to-text:true" inset="0,0,0,0">
       <![endif]-->
    <td>
  </tr>
</table>
   ```

### This can be easily fixed by adding the snippet below
` * { -webkit-text-size-adjust: none; }`

### Prevent iOS from "clipping" messages that are over 102k
To fix this, make sure that you have a minimum of 1,019 characters before your closing head tag including spaces and carriage returns also if you don’t have any need for more styles, nor a style block, try inserting several lines of empty spaces.

### Issues with spacing below images
Some email clients add space below images by default, which is problematic if you’re tiling images. Attach the `.imageFix` class to remove the space. Be aware that, by setting images to block-level elements, you can’t align them without resorting to the float or position CSS properties, which aren’t widely supported:
```
img {
 border: 0 none;
 height: auto;
 line-height: 100%;
 outline: none;
 text-decoration: none;
}

a img {
 border: 0 none;
}

.imageFix {
 display: block;
}
```
### Breaking out of CSS inlines to overwrite email client stylesheets
One thing to note is that all CSS gets inlined. This sometimes is a problem because some email clients add their own stylesheets which overwrite your inline CSS or wrap tags elements. An example would be IOS Mobile wrapping dates and locations in a link tag causing a highlighted blue text, so if you do run into these kind of problems, you can add a style sheet via the gulp file. Let me walk you through the 3 step process of adding overriding styles to the top of the page.

### Step 1
Go into `gulpfile.js` and go to line 128. You will see this code line below.
```bash
  .pipe($.replace, '<!-- <style> -->', `<style>${mqCss}</style>`)
```
### Step 2
Copy and paste the new line of code above and edit it to something like this below to create a style sheet.

```bash
.pipe($.replace, '<!-- fix -->', '<style> a[x-apple-data-detectors] {color: #d0d1d3; text-decoration: none; }</style>')
```
### Step 3
Next go to this file `index-lyout.html` and add the comment block below where you want the css code to be injected.
```bash
'<!-- fix -->'
```
 ### ( ͡° ͜ʖ ͡°)  
 ### That's it!
