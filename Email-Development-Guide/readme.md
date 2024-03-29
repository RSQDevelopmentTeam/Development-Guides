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

### images breaking out of layout on certain clients
```
<img src="https://placekitten.com/600/600" width="600" style="width: 100%; max-width: 600px;">
```

### Links getting converted to purple or blue
When the emails are sent using HTML template from Outlook, all the links in the email turn to either blue or purple, with an underline. Regardless of what colored text is used, the blue/purple underline persists when viewed on different email clients.

To avoid this issue, use the <font> tag and wrap the text with a <span> tag and a style attribute. Use the following code:
  
```
<a style="color:#E3A216; text-decoration:none;">
  <span style="color:#E3A216;">
    <font color="#E3A216">
      Click me
    </font>
  </span>
</a>
```

Outlook button

      <div style="font-family: Helvetica, sans-serif;font-size: 100%;margin: 0;padding: 0;margin-top: 0">
        <!--[if mso]>

            <v:rect style="height:40px;width:0;" fill="f" stroke="f" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" />

            <v:roundrect style="width:281px;height:55px;position:relative;top:0;left:-4px;" arcsize="50%" stroke="f" fill="true" xmlns:v=&quot;urn:schemas-microsoft-com:vml&quot; xmlns:w=&quot;urn:schemas-microsoft-com:office:word&quot;>
                <v:fill type="gradientradial" color="transparent" color2="#000" focus="0" focusposition=".05,0.23" focussize=".9,0.25" />
            </v:roundrect>

            <v:roundrect href="https://app.kontent.ai/gotoaction" style="width:273px;height:40px;position:relative;top:0;left:0;v-text-anchor:middle;" arcsize="50%" stroke="f" fillcolor="#000" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word">
                <w:anchorlock/>
                <v:textbox inset="0,0,0,0">
                <center>
            <![endif]-->
        <a href="https://app.kontent.ai/gotoaction"
          style="font-family: Helvetica, sans-serif;font-size: 14px;margin: 0;padding: 8px 26px;color: #ffffff;margin-top: 0;line-height: 40px;letter-spacing: 0.1ch;background-color: #000;border-radius: 5000px; display: inline-block;text-align: center;text-decoration: none;white-space: nowrap;-webkit-text-size-adjust: none">
          Read the announcment</a>
        <!--[if mso]>
                </center>
                </v:textbox>
            </v:roundrect>
            <![endif]-->
      </div>

### Leverage Outlook conditional tags
Outlook 2000, 2002 & 2003 render with Internet Explorer and are fairly easy to deal with. But Outlook 2007 and beyond are rendered by Microsoft Word, which can cause problems.
The work around? Use Outlook conditional tags to target Outlook as a whole, including specific years such as Outlook 2010 or 2013.

Target Outlook 2007 and up
```
<! — [if mso]>
<style type=”text/css”>
     /*Your styles here*/
</style>
<![endif] →
```
Target Outlook 2000, 2002, & 2003
```
<! — [if IE]>
<style>
     /*Your styles here*/
</style>
<![endif] →
```

Target all Outlook versions
```
<! — [if (gte mso 9) | (IE)]>
<style>
     /*Your styles here*/
</style>
<![endif] →
```
The mso number within the conditional tags refers to which Outlook version you are targeting. There are other mso numbers to target different versions of Outlook:
Outlook 2000 = mso 9
Outlook 2002 = mso 10
Outlook 2003 = mso 11
Outlook 2007 = mso 12
Outlook 2010 = mso 14
Outlook 2013 = mso 15
A word of warning, trying to specifically target Outlook 2000 ([if mso 9]), 2002 ([if mso 10]), or 2003([if mso 11]) does not seem to work. When it comes to targeting Outlook 2000, 2002, and 2003 using [if IE] is your best bet. On the other hand, Outlook 2007 and up responds very well to targeting specific versions with mso numbers such as [if mso 15] for Outlook 2013 or [if mso 12] for Outlook 2007.


! example
```
<! — [if !(IE)]>
<style>
     /*If not Outlook 2000, 2002, and 2003.*/
</style>
<![endif] →
```
lt example
```
<! — [if lt mso 14]>
<style>
     /*If less than Outlook 2010*/
</style>
<![endif] →
```
| example
```
<! — [if (mso 12) | (mso 15)]>
<style>
     /*If Outlook 2007 or 2013*/
</style>
<![endif] →
```
### Outlook line-height issues
You need to use the mso style "mso-line-height-rule". This is used to force Outlook to respect the line height rule. Please note this needs to be added PRIOR to the declared line-height or it will not work. See below:
```
body { mso-line-height-rule: exactly; }
```

### Creating a working Bullet List
https://emailmonks.com/blog/email-coding/bullet-list-outlook-hacks/

### Font & Image Size
IOS devices have two main issues with font and image size:
Small font sizes are enlarged by default Email width is based on the largest element Font-size enlargement is usually not a critical problem, but in some cases it may cause some lines of text to be spliced potentially breaking your layout.

### This can be easily fixed by adding the snippet below
` * { -webkit-text-size-adjust: none; }`

### Images full width on Outlook 120dpi 

Add this as your html tag
```
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office" lang="en" xml:lang="en">
```

Put this in your header
```
<!--[if gte mso 9]><xml><o:OfficeDocumentSettings><o:AllowPNG/><o:PixelsPerInch>96</o:PixelsPerInch></o:OfficeDocumentSettings></xml><![endif]-->

```

### Tables not going lower then 16px in height.
Email on Acid applies font-size: 16px to the th tag, so you'll need to change that to lower font-size. Issues will be seen on outlook 2013 & Office 365

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
