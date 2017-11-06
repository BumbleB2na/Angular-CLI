# Angular 5 Projects
  
We use Angular CLI as the foundation for our projects. We make some modifications to the code Angular CLI generates and we have rules for how we use Angular CLI `ng generate` commands. These differences are what makes our projects unique. To make those difference clear we compare our way to Angular's Quickstart Guide and Angular CLI Wiki. This lets us better maintain consistency across Angular 5 projects.
  

> An Angular CLI project is the foundation for both quick experiments and enterprise solutions.
> 
> &mdash; <cite>Angular quickstart doc > [Project file review](https://angular.io/guide/quickstart#project-file-review)</cite>

## Angular 5 Learning Path
### Or, Creating a new Angular 5 project
### Or, Understanding an Angular 5 upgrade of a legacy project

First, follow along in [Angular's Quickstart](https://angular.io/guide/quickstart) using Angular CLI but, before you do anything follow through this documentation to understand how we do things differently. For example, right off the bat we recommend using yarn instead of npm to ensure the latest Angular CLI is installed globally. This will get you doing things the way we have been doing things. The reasons for this are explained later in the documentation.
  

After your Angular 5 project is set up and you've reached the end of Angular's Quickstart guide then, you may want to try the Tour of Heroes tutorial. On a personal note: I did the [Tour of Heroes](https://angular.io/tutorial) tutorial 3 times, digging deeper in to the Angular documentation and learning more about the advanced concepts each time. I don't think enough developers put enough time in to learning Angular and also brushing up on TypeScript, Node, Jasmine unit tests and everything else along the way. Set your expectation high and that's about the level of effort you should expect to have to put in to it.

## Upgrading Angular CLI globally
Angular CLI was chosen because it's still the recommended route by Angular to develop Angular 5 progressive web apps. They keep the [Angular CLI Wiki](https://github.com/angular/angular-cli/wiki) up to date.

### Upgrade Angular CLI before any Angular 5 project development

`yarn global upgrade @angular/cli@latest` 
  
  
For generating new project we followed Angular 5 Project [Installation](https://github.com/angular/angular-cli/tree/00ca690807a2326b6e8632a9a0ec46587b841a78#installation) using Angular CLI but, for security of package installation we use `yarn global add` instead of `npm install -g`.
  
> npm: what is my purpose?<br>- You install Yarn.
> 
> &mdash; I Am Devloper (@iamdevloper) [October 10, 2017](https://twitter.com/iamdevloper/status/917710714361602048)
  
## New Angular 5 project setup using Angular CLI

We start test projects and enterprise solution projects with the Angular CLI. 
  

`ng new project-name`
  

Starting a project with the Angular CLI gives a Development Team the following benefits:
- In our own documentation we can source Angular's documentation and compare that to what we did different. This lets us lean on Angular's documentation and then leaves room for us to explain what we modified, took away, or added on top.
- Developers can more easily follow along with tutorials and books on Angular 5 Development because our Angular 5 projects follow Angular's recommendation of how to start a project.
- The way we organize a project and write code is more predictable among people new or experienced with Angular 5 Development. We can all learn how things were done in our own time or ask questions and it's all relative to the Angular 5 learning path.
- Development is faster. Project setup / organization and Angular / Javascript coding style is more consistent among developers on the team.
- A test project we work on from scratch is more easily plugged in to an enterprise solution if it is made the same way / same process is followed.
- Following a process for Angular 5 project development encourages "refactoring up" to make things more reusable. For example we should be able to start up a test project from scratch and pull in the same utilities or helpers that we use and maintain on an enterprise level project. That would be one way to build a test project from scratch where it becomes more pluggable.
  
  
*Following explanation sourced from Angular quickstart doc > [Project file review](https://angular.io/guide/quickstart#project-file-review):*
  

An Angular CLI project is the foundation for both quick experiments and enterprise solutions.


### The src folder

*Following explanation source from Angular quickstart doc > [src](https://angular.io/guide/quickstart#the-src-folder):*
  

Your app lives in the src folder. All Angular components, templates, styles, images, and anything else your app needs go here. Any files outside of this folder are meant to support building your app.
  
```
src
 ├─ app
 │   ├─ app.component.css
 │   ├─ app.component.html
 │   ├─ app.component.spec.ts
 │   ├─ app.component.ts
 │   └─ app.module.ts
 ├─ assets
 │   └─ .gitkeep
 ├─ environments
 │   ├─ environment.prod.ts
 │   └─ environment.ts
 ├─ favicon.ico
 ├─ index.html
 ├─ main.ts
 ├─ polyfills.ts
 ├─ styles.css
 ├─ test.ts
 ├─ tsconfig.app.json
 └─ tsconfig.spec.json
```
  
  
File | Their purpose *(Angular quickstart doc > [src](https://angular.io/guide/quickstart#the-src-folder))* | Our purpose *(assume same if no change)*
------------ | ------------- | -------------
`app/app.component.{ts,html,css,spec.ts}` | Defines the AppComponent along with an HTML template, CSS stylesheet, and a unit test. It is the root component of what will become a tree of nested components as the application evolves. | -
`app/app.module.ts` | Defines AppModule, the root module that tells Angular how to assemble the application. Right now it declares only the AppComponent. Soon there will be more components to declare. | -
`assets/*` | A folder where you can put images and anything else to be copied wholesale when you build your application. | -
`environments/*` | This folder contains one file for each of your destination environments, each exporting simple configuration variables to use in your application. The files are replaced on-the-fly when you build your app. You might use a different API endpoint for development than you do for production or maybe different analytics tokens. You might even use some mock services. Either way, the CLI has you covered. | -
`favicon.ico` | Every site wants to look good on the bookmark bar. Get started with your very own Angular icon. | -
`index.html` | The main HTML page that is served when someone visits your site. Most of the time you'll never need to edit it. The CLI automatically adds all js and css files when building your app so you never need to add any `<script>` or `<link>` tags here manually. | -
`main.ts` | The main entry point for your app. Compiles the application with the JIT compiler and bootstraps the application's root module (AppModule) to run in the browser. You can also use the AOT compiler without changing any code by appending the--aot flag to the ng build and ng serve commands. | -
`polyfills.ts` | Different browsers have different levels of support of the web standards. Polyfills help normalize those differences. You should be pretty safe with core-js and zone.js, but be sure to check out the Browser Support guide for more information. | *TODO: uncomment the polyfills that the Angular CLI starts us off and explain that choice here. E.g. Polyfill es6 in IE10 and IE11, add internationalization support (locales), supported languages chosen.*
`styles.css` | Your global styles go here. Most of the time you'll want to have local styles in your components for easier maintenance, but styles that affect all of your app need to be in a central place. | -
`test.ts` | This is the main entry point for your unit tests. It has some custom configuration that might be unfamiliar, but it's not something you'll need to edit. | -
`tsconfig.{app|spec}.json` | TypeScript compiler configuration for the Angular app (tsconfig.app.json) and for the unit tests (tsconfig.spec.json). | -

### The root folder

*Following explanation sourced from Angular quickstart doc > [root](https://angular.io/guide/quickstart#the-root-folder):*
  

The src/ folder is just one of the items inside the project's root folder. Other files help you build, test, maintain, document, and deploy the app. These files go in the root folder next to src/.
  

```
my-app
 ├─ e2e
 │   ├─ app.e2e-spec.ts
 │   ├─ app.po.ts
 │   └─ tsconfig.e2e.json
 ├─ node_modules/...
 ├─ src/...
 ├─ .angular-cli.json
 ├─ .editorconfig
 ├─ .gitignore
 ├─ karma.conf.js
 ├─ package.json
 ├─ protractor.conf.js
 ├─ README.md
 ├─ tsconfig.json
 └─ tslint.json
```
  
  
File | Their purpose *(Angular quickstart doc > [root](https://angular.io/guide/quickstart#the-root-folder))* | Our purpose *(assume same if no change)*
------------ | ------------- | -------------
`e2e/` | Inside e2e/ live the end-to-end tests. They shouldn't be inside src/ because e2e tests are really a separate app that just so happens to test your main app. That's also why they have their own tsconfig.e2e.json. | -
`node_modules/` | Node.js creates this folder and puts all third party modules listed in package.json inside of it. | -
`.angular-cli.json` | Configuration for Angular CLI. In this file you can set several defaults and also configure what files are included when your project is built. Check out the official documentation if you want to know more. | -
`.editorconfig` | Simple configuration for your editor to make sure everyone that uses your project has the same basic configuration. Most editors support an .editorconfig file. See http://editorconfig.org for more information. | -
`.gitignore` | Git configuration to make sure autogenerated files are not commited to source control. | -
`karma.conf.js` | Unit test configuration for the Karma test runner, used when running ng test. | -
`package.json` | npm configuration listing the third party packages your project uses. You can also add your own custom scripts here. | We have added `start-open` and `test-coverage-report` scripts.
`protractor.conf.js` | End-to-end test configuration for Protractor, used when running ng e2e. | -
`README.md` | Basic documentation for your project, pre-filled with CLI command information. Make sure to enhance it with project documentation so that anyone checking out the repo can build your app! | We have renamed Angular CLI default README.md to README.CLI.md and replaced README.md with our own.
`tsconfig.json` | TypeScript compiler configuration for your IDE to pick up and give you helpful tooling. | -
`tslint.json` | Linting configuration for TSLint together with Codelyzer, used when running ng lint. Linting helps keep your code style consistent. | -

## Angular 5 Development using Angular CLI

### Angular Tests / Coverage
#### Code Coverage
We maintain 100% code coverage for core/main functionality which includes:
- AppComponent
  

We try to maintain ~80% coverage for non-core/main functionality which includes:
- forms.io

#### Code Coverage Reporting

`ng test --single-run --code-coverage`
  

*Generates a folder, "coverage" with a coverage report inside.*

### End-to-end (e2e) testing

`ng e2e`
  

Runs Selenium e2e tests that help to support good code coverage. End-to-end testing can be used to cover areas of an application where unit tests were not written or properly maintained.

### Angular CLI Scaffolding (ng generate)

We use Angular CLI generate to scaffold everything possible such as components, services and classes. This makes setting up a new Angular 5 project much easier and it makes adding to an existing Angular 5 project much more straightforward.
  

For understanding how to use ng to generate, reference Angular CLI Wiki > [Generate](https://github.com/angular/angular-cli/wiki/generate) and Angular repository > Installation > [generate examples](https://github.com/angular/angular-cli/tree/00ca690807a2326b6e8632a9a0ec46587b841a78#generating-components-directives-pipes-and-services) (in the Angular repository) but, it may be worth knowing the way we've been using the generate commands. This is the standard way we've been using ng generate commands in our Angular 5 development:

#### Generate new component

`ng g component test`
  

*Generates a folder, "test" with spec and adds component declaration to app.module.ts  ...then in app.component.spec.ts for e.g. we add the component so karma tests can pass:*
  
```
import { TestBed, async } from '@angular/core/testing';
import { AppComponent } from './app.component';
import { TestComponent } from './test/test.component';
describe('AppComponent', () => {
 beforeEach(async(() => {
   TestBed.configureTestingModule({
     declarations: [
       AppComponent,
       TestComponent
     ],
   }).compileComponents();
 }));
```

#### Generate new service in a folder

`ng g service services\test`

#### Generate new class in a folder

`ng g class models\test-obj`

#### Angular CLI Commands

Their way compared to our way:
  
Use Angular CLI `ng generate` to add.. | Their way is *([installation docs](https://github.com/angular/angular-cli/tree/00ca690807a2326b6e8632a9a0ec46587b841a78#generating-components-directives-pipes-and-services))* | Our way is *(commands we use)*
------------ | ------------- | -------------
new [Component](https://github.com/angular/angular-cli/wiki/generate-component) | `ng g component my-new-component` | `ng g component my-new-component` *(No change)*
new [Directive](https://github.com/angular/angular-cli/wiki/generate-directive) | `ng g directive my-new-directive` | -
new [Pipe](https://github.com/angular/angular-cli/wiki/generate-pipe) | `ng g pipe my-new-pipe` | -
new [Service](https://github.com/angular/angular-cli/wiki/generate-service) | `ng g service my-new-service` | `ng g service services\my-new-service` *(Target sub-folder)*
new [Class](https://github.com/angular/angular-cli/wiki/generate-class) | `ng g class my-new-class` | `ng g class models\my-new-class` *(Target a sub-folder)*
new [Guard](https://github.com/angular/angular-cli/wiki/generate-guard) | `ng g guard my-new-guard` | -
new [Interface](https://github.com/angular/angular-cli/wiki/generate-interface) | `ng g interface my-new-interface` | -
new [Enum](https://github.com/angular/angular-cli/wiki/generate-enum) | `ng g enum my-new-enum` | -
new [Module](https://github.com/angular/angular-cli/wiki/generate-module) | `ng g module my-module` | `ng g module my-module` *(No change)*
new Component to existing module | - | `ng g component my-module/my-new-component` *(Target an existing module)*

## Documentation / JsDocs
We use JsDocs comments above functions and at the top of files to:
1. support intellisense in Visual Studio Code for project classes and methods, and
1. let us generate documentation using a jsdoc to markdown documentation converter plugin (not yet implemented)

### Markdown Documentation
Writing JsDocs with markdown syntax to support generating good documentation that even includes screenshots (not yet implemented).
  

*TODO: Use a package that generates a wiki out of JsDocs that use markdown ([example](https://github.com/jsdoc2md/jsdoc-to-markdown/blob/master/docs/API.md)).*

## Angular 5 Development

*TODO: Add information such as Utilities or Helpers we use, polyfills or packages we use in Angular 5 Development.*


