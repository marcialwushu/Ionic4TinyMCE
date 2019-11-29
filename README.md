# TinyMCE Angular integration quick start guide

The Official TinyMCE Angular component integrates TinyMCE into Angular projects. This procedure creates a basic Angular application containing a TinyMCE editor based on our Basic TinyMCE example.

For examples of the TinyMCE Angular integration, visit the tinymce-angular storybook.

## Prerequisites

This procedure requires:

- Node.js (and npm).
- Access to tinymce.min.js on either:
    - Tiny Cloud.
    - TinyMCE Self-hosted. See Advanced installation choices for details on self-hosting TinyMCE.

## Procedure

1. On a command line or command prompt, install the Angular CLI Tool package.

```
$ npm install -g @angular/cli
 ```

2. Create a new Angular project named tinymce-angular-demo.

```
$ ng new --defaults --skip-git tinymce-angular-demo
```

3. Change into the newly created directory.

```
$ cd tinymce-angular-demo
```

4. Install the tinymce-angular package and save it to your package.json with --save.

```
$ npm install --save @tinymce/tinymce-angular
```

5. Using a text editor, open /path/to/tinymce-angular-demo/src/app/app.module.ts and replace the contents with:

```ts
 import { BrowserModule } from '@angular/platform-browser';
 import { NgModule } from '@angular/core';
 import { EditorModule } from '@tinymce/tinymce-angular';
 import { AppComponent } from './app.component';

 @NgModule({
   declarations: [
     AppComponent
   ],
   imports: [
     BrowserModule,
     EditorModule
   ],
   providers: [],
   bootstrap: [AppComponent]
 })
 export class AppModule { }

```
6. Using a text editor, open /path/to/tinymce-angular-demo/src/app/app.component.html and replace the contents with:

```html
 <h1>TinyMCE 5 Angular Demo</h1>
 <editor
   initialValue="<p>This is the initial content of the editor</p>"
   [init]="{
        height: 500,
        menubar: false,
        plugins: [
          'advlist autolink lists link image charmap print preview anchor',
          'searchreplace visualblocks code fullscreen',
          'insertdatetime media table paste code help wordcount'
        ],
        toolbar:
          'undo redo | formatselect | bold italic backcolor | \
          alignleft aligncenter alignright alignjustify | \
          bullist numlist outdent indent | removeformat | help'
      }"
   >
 </editor>

```

This TinyMCE editor configuration should replicate the example on the Basic example page.

7. Provide access to TinyMCE using Tiny Cloud or by self-hosting TinyMCE.

- Tiny Cloud

Include the apiKey option in the editor element and include your TinyMCE API key.

Such as:

```html
  <Editor apiKey="your-api-key" [init]={ /* your other settings */ } />
```

- TinyMCE Self-hosted

TinyMCE can be self-hosted by: including TinyMCE within the application, deploying TinyMCE independent of the Angular application, or bundling TinyMCE with the Angular application.

- Including TinyMCE within the Application

To load TinyMCE and TinyMCE-Angular in a project managed by the Angular CLI Tool:

1. Install the tinymce-angular package and save it to your package.json with --save.

```
 $ npm install --save tinymce
```

2. Using a text editor, open angular.json and add TinyMCE to the global scripts tag.

For example:

```json
 "scripts": [
   "node_modules/tinymce/tinymce.min.js"
 ]

```

3. Using a text editor; open angular.json and add the TinyMCE skins, themes, and plugins to the assets property.

```ts
 "assets": [
   { "glob": "**/*", "input": "node_modules/tinymce/skins", "output": "/tinymce/skins/" },
   { "glob": "**/*", "input": "node_modules/tinymce/themes", "output": "/tinymce/themes/" },
   { "glob": "**/*", "input": "node_modules/tinymce/plugins", "output": "/tinymce/plugins/" }
 ]

```

4. Update the editor configuration to include the base_url and suffix options.

```html
 <editor [init]="{
   base_url: '/tinymce', // Root for resources
   suffix: '.min',       // Suffix to use when loading resources
   plugins: 'lists advlist',
   toolbar: 'undo redo | bold italic | bullist numlist outdent indent'
 }"></editor>

```

- Deploy TinyMCE independent of the Angular application

To use an independent deployment of TinyMCE, add a script to either the <head> or the end of the <body> of the HTML file, such as:

```html
<script src="/path/to/tinymce.min.js"></script>

```

To use an independent deployment of TinyMCE with the create a Angular application, add the script to /path/to/tinymce-angular-demo/src/app/app.component.html.

For information on self-hosting TinyMCE, see: Advanced installation choices.

- Bundling TinyMCE with the Angular application using a module loader

To bundle TinyMCE using a module loader (such as Webpack and Browserify), see: Usage with module loaders.

8. Test the application using the Angular development server.

- To start the development server, navigate to the tinymce-angular-demo directory and run:

```
  $ ng serve --open
```

--- 

[TINY DOCS](https://www.tiny.cloud/docs/integrations/angular/)