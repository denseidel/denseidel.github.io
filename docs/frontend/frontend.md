---
id: frontend
title: Frontend
---

Start by [understand the tech stack](./#technology-stack) & the [architectural decisions](./#architectural-decisions).

## Decisions

<!-- adrlog -->

- [ADR-0001](adr/0001-use-ant-design-as-a-ui-framework) - Use Ant Design as a UI framework
- [ADR-0002](adr/0002-use-react-for-desktop-and-mobile) - Use React for Desktop and Mobile

<!-- adrlogstop -->

## Design the UI (Webdesign)

The foundations of UI design is [CSS3, Flexbox, and CSS grid]() extended by [React Best Practices and Patterns](https://www.sitepoint.com/react-architecture-best-practices/) :

- styled components
- render prop 


 Suplement this with **Ant Design** as a UI Framework for * [Desktop](https://ant.design) and [Mobile](https://mobile.ant.design/docs/react/introduce).

## Develop the frontend 

The frontend is developed using [Javascript](https://www.freecodecamp.org/news/beaucarnes/learn-javascript-full-course--j4Va5cR1p)/[Penetration-Testing](https://www.freecodecamp.org/news/beaucarnes/web-app-penetration-testing-full-course--pena5cR1p) using the Framework with the largest mature ecosystem [React](https://github.com/enaqx/awesome-react)([Course](https://www.udemy.com/react-the-complete-guide-incl-redux/)) and [React Best Practices](https://www.zerrtech.com/blog/react-design-best-practices).

### Landing Page

Before developing the complete application test your app with a mock or a landing page. Check the steps and details in the sample [repo](https://github.com/denseidel/nosmoke.ai).

### Rapid Prototype

* Prototypes should be thrown away afterwards to ensure you make it cheap, fast, little.
* Focus on the end goal: user test or video for VC.
* Target Users: Low Fidality (Intenal & Social Circle (biase!) - talk with them, SMEs (know the market but outside) - use email, twitter and phone)  vs High Fidality (customer of the market, customer of customers - [Guerrilla Prototype](https://uxplanet.org/guerrilla-testing-with-your-prototypes-1f28536b64bc)) 

Status: 

#### Questions that are useful for each stage of prototyping:

**Low-fidelity:**
- Is each main function of the app easily accessible to users?
- Do users easily identify what the functionality of the app is?
- What is getting in the way of their use of that functionality?
- What expectations do they have of potential supplemental functionality for the app?
**Med-fidelity:**
- For each screen, does the design of the screen work to guide users to the right functions?
- Does the user easily navigate through the app to find supplemental functionality?
- Do users easily find the interaction points we intend them to?
**Hi-fidelity:**
- Does the animation between each screen delight users?
- Does our use of color work to make their experience compelling?
- Do users like how the app reacts to touch gestures?


### Web App (using component based development)

[Build an app with component based development](./#build-an-app) and decide if you deploy the application serverless or use docker containers \(vendor independent\): [Dockerize a react application](./#dockerize-a-react-app)
[React](https://medium.freecodecamp.org/the-react-handbook-b71c27b0a795)

https://github.com/websemantics/awesome-ant-design
* Overview: https://gather.engineering/react-ui-frameworks-compared-dd631eb5c982  https://www.npmtrends.com/office-ui-fabric-react-vs-@blueprintjs/core-vs-antd

### Architecture

[MVVM](https://medium.cobeisfresh.com/level-up-your-react-architecture-with-mvvm-a471979e3f21) vs Redux

https://levelup.gitconnected.com/structure-your-react-redux-project-for-scalability-and-maintainability-618ad82e32b7
https://redux.js.org/faq/codestructure
https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be
https://github.com/alexnm/re-ducks
https://github.com/erikras/ducks-modular-redux
https://github.com/erikras/react-redux-universal-hot-example#redux-modules-what-the-duck

/components
/views - container
/ducks - vm + controller?



### redux 
* Tutorial Basics: https://learn.freecodecamp.org/front-end-libraries/redux
* Docs !: https://redux.js.org/basics/usagewithreact#implementing-components
* Redux - Ducks: https://github.com/erikras/ducks-modular-redux
* Redux - Saga: https://github.com/redux-saga/redux-saga / https://flaviocopes.com/redux-saga/


* Efficient Testing: 
 https://medium.com/@darioghilardi/end-to-end-testing-on-a-react-redux-app-10f5a26f2f61

-> test what is important : see below
UI -> end 2 end (integration) [[cypress](https://www.cypress.io/how-it-works/), [howto](https://medium.com/@darioghilardi/end-to-end-testing-on-a-react-redux-app-10f5a26f2f61)]
libs -> unit 
backends -> unit / end 2 end (integration)



https://jobs.zalando.com/tech/blog/economic-perspective-testing/ /
An economic point of view helps to reconsider the Return on Investment of unit tests. Consider the confidence a test provides. Integration tests provide the best balance between cost, speed and confidence. Be careful about code coverage as too high aspirations there are likely counter-productive. Be skeptical about the code-quality improving powers of making code unit-testable.

To make it clear, I do not advocate to never write unit tests. I hope that I provided a fresh perspective on testing. As a future article, I plan to present how to concretely implement a good integration test for both a frontend and backend project.

If you desire clear, albeit unnuanced, instructions, here is what you should do: Use a typed language. Focus on integration and end-to-end tests. Use unit tests only where they make sense (e.g. pure algorithmic code with complex corner cases). Be economic. Be lean.


### landing page

https://www.thinkific.com/blog/landing-page-design-elements/


### Rapid Prototyping {#rapid-prototyping}

To get feedback fast create a first prototype:

**Define Application Structure \(Paper? + Photo or Balsamiq + screenshot from rolemodels\):**

1. LandingPage \(login or not\)![](/img/landing-page-analysis.png)2. Personal Service Page \(only logged in\)

   ![](/img/personal-service-page-1.png)

### Build a mock?  {#build-an-app}

* [https://moqups.com/pricing/sign-up?p=Ewy0d](https://moqups.com/pricing/sign-up?p=Ewy0d)
* [https://projects.invisionapp.com/d/signup](https://projects.invisionapp.com/d/signup)

###  {#build-an-app}

### Build an app with component based development {#build-an-app}

**Create sampleapp-client**

```text
create-react-app sampleapp-client
cd sampleapp-client
```

**Setup Project Structure**

Theory: [https://hackernoon.com/my-journey-toward-a-maintainable-project-structure-for-react-redux-b05dfd999b5](https://hackernoon.com/my-journey-toward-a-maintainable-project-structure-for-react-redux-b05dfd999b5)

```text
src
 ├── components
 │
 ├── containers
 │  ├── auth.js
 │  ├── productList.js
 │  └── productDetail.js
 │
 ├── reducers (aka ducks)
 │  ├── index.js (combineReducers + complex selectors)
 │  ├── auth.js (reducers, action types, actions creators, selectors)
 │  └── product.js (reducers, action types, actions creators, selectors)
 │
 ├── sagas
 │  ├── index.js (root saga/table of content of all the sagas)
 │  ├── auth.js
 │  └── product.js
 │
 └── services
    ├── authenticationService.js
    └── productsApi.js
```

[Code on github](https://github.com/denseidel/spa-starter/commit/25a4f36d7997e78dc3233f917561c6ed49badbc3)

**Create Router and setup basic Application structure**

Link: [https://github.com/ReactTraining/react-router](https://github.com/ReactTraining/react-router) / [https://reacttraining.com/react-router/web/guides/quick-start](https://reacttraining.com/react-router/web/guides/quick-start)

Install: `npm i react-router-dom`

Setup Routers: [Code on github](https://github.com/denseidel/spa-starter/commit/10b7952eaaa8a5977a8636612845bcae86da937f)

**Create Placeholder Components/Containers:**

[Code on github](https://github.com/denseidel/spa-starter/commit/c3b7246f4ab22dee7e11f6aa27fe3f792fa7fb43)

**Setup CSS Framework for Styling**

I currently use [Bulma](https://bulma.io/documentation/overview/start/) / [BulmaThemes](https://jenil.github.io/bulmaswatch/) and [FontAwesome](http://fontawesome.io/get-started/):

Include link to css in index.html or[ use npm](https://bulma.io/documentation/overview/start/) \(recomended\)

[Code on github](https://github.com/denseidel/spa-starter/commit/7c87cd95d7965571cfd38c5716f47c2e60f455f2)

* [Tutorial on using Bulma](https://scotch.io/bar-talk/get-to-know-bulma-my-current-favorite-css-framework)
* [Example how to use Bulma](https://medium.freecodecamp.org/colorful-fundamentals-the-reward-of-building-with-bulma-7b14883317bd)

**Install storybook.js and configure it**

Basic Setup: [https://storybook.js.org/basics/guide-react/](https://storybook.js.org/basics/guide-react/)

```text
npm i --save-dev @storybook/react
```

Configure Storybook \[[Code](https://github.com/denseidel/sampleapp-client/commit/62cf7e1f02a887f71e9833d5cf071ca11d880c53)\]

Further Setup:

* [what are action, decorators ...](https://blog.hichroma.com/introduction-to-storybook-5aca8cc643f7)
* [with bulma.io](http://ouicar.github.io/2017/01/05/storybook-2.html) 
* [customize SASS](http://andreafalzetti.github.io/blog/2017/05/30/bundling-react-15-bootstrap-4-storybook-3-with-webpack-2.html)

Create Container/Componente LoginPage \(might be a container in the future\):

`/src/container/LoginPage`

in its own folder in this folder you then find the `LoginPage.js` file, `.css` , pictures \(`.svg`\) and the story `LoginPage-story.js`

Example how IBM is doing it:

* Component [https://github.com/carbon-design-system/carbon-components-react/tree/master/src/components/Accordion](https://github.com/carbon-design-system/carbon-components-react/tree/master/src/components/Accordion)
* Config: [https://github.com/carbon-design-system/carbon-components-react/blob/master/.storybook/config.js](https://github.com/carbon-design-system/carbon-components-react/blob/master/.storybook/config.js)
* Storybook: [http://react.carbondesignsystem.com/?selectedKind=Accordion&selectedStory=Default&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel](http://react.carbondesignsystem.com/?selectedKind=Accordion&selectedStory=Default&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)
* Webpack config \(to use\): [https://github.com/carbon-design-system/carbon-components-react/blob/master/.storybook/webpack.config.js](https://github.com/carbon-design-system/carbon-components-react/blob/master/.storybook/webpack.config.js)
* How to use in project: [https://github.com/carbon-design-system/carbon-components-react\#usage](https://github.com/carbon-design-system/carbon-components-react#usage)

**Developer Components in Stylebook:**

Sample: [https://github.com/kadira-samples/react-storybook-demo/blob/master/components/stories/MainSection.js](https://github.com/kadira-samples/react-storybook-demo/blob/master/components/stories/MainSection.js)

[Code on github](https://github.com/denseidel/spa-starter/commit/9e7d246cf92820b834e4c0e55b7f461401c1c813)

Run Storybook: `npm run storybook`

* Using ReactRouter with history: 
  * [https://stackoverflow.com/questions/42701129/how-to-push-to-history-in-react-router-v4](https://stackoverflow.com/questions/42701129/how-to-push-to-history-in-react-router-v4)
  * [https://reacttraining.com/react-router/web/guides/redux-integration](https://reacttraining.com/react-router/web/guides/redux-integration)
  * [https://github.com/ReactTraining/react-router/blob/master/FAQ.md\#how-do-i-access-the-history-object-outside-of-components](https://github.com/ReactTraining/react-router/blob/master/FAQ.md#how-do-i-access-the-history-object-outside-of-components)
  * [https://stackoverflow.com/questions/43279135/reactjs-router-v4-history-push-not-working/43280171](https://stackoverflow.com/questions/43279135/reactjs-router-v4-history-push-not-working/43280171)
  * use **withRouter on at least App and otherwise use a manual history object**
  * [https://github.com/ReactTraining/react-router/issues/4924](https://github.com/ReactTraining/react-router/issues/4924)
  * [https://reacttraining.com/react-router/web/example/auth-workflow](https://reacttraining.com/react-router/web/example/auth-workflow)
* Frontend Tracking with Google Analytics: 
  * [https://github.com/react-ga/react-ga](https://github.com/react-ga/react-ga)
  * [https://web-design-weekly.com/2016/07/08/adding-google-analytics-react-application/](https://web-design-weekly.com/2016/07/08/adding-google-analytics-react-application/)

## Make AJAX / REST Calls from the Frontend with axios

[https://medium.com/codingthesmartway-com-blog/getting-started-with-axios-166cb0035237](https://medium.com/codingthesmartway-com-blog/getting-started-with-axios-166cb0035237)

### Dockerize a React App {#dockerize-a-react-app}

1. [http://mherman.org/blog/2017/12/07/dockerizing-a-react-app/](http://mherman.org/blog/2017/12/07/dockerizing-a-react-app/)
2. [https://www.peterbe.com/plog/how-to-create-react-app-with-docker](https://www.peterbe.com/plog/how-to-create-react-app-with-docker)

### Deploy the Frontend

1. Upload the assets of our app
2. Use a CDN to serve out our assets
3. Point our domain to the CDN distribution
4. Switch to HTTPS with a SSL certificate

AWS provides quite a few services that can help us do the above. We are going to use[S3](https://aws.amazon.com/s3/) to host our assets,[CloudFront](https://aws.amazon.com/cloudfront/) to serve it, [Route 53](https://aws.amazon.com/route53/)to manage our domain, and [Certificate Manager](https://aws.amazon.com/certificate-manager/) to handle our SSL certificate.

#### Create the Bucket {#create-the-bucket}

First, log in to your[AWS Console](https://console.aws.amazon.com/)and select S3 from the list of services.![](/img/open-s3.png)

Select **Create Bucket**and pick a name for your application and select the **US East \(N. Virginia\) Region** Region. Since our application is being served out using a CDN, the region should not matter to us.

![](/img/create-new-s3-bucket.png)  
![](/img/create-s3-bucket-1.png)![](/img/create-s3-bucket-3.png)

![](/img/create-s3-bucket-4.png)

![](/img/create-s3-bucket.png)

Now click on your newly created bucket from the list and navigate to its permissions panel by clicking **Permissions**.

![](/img/s3-bucket-permissions.png)

```text
{
  "Version":"2012-10-17",
  "Statement":[{
    "Sid":"PublicReadForGetBucketObjects",
        "Effect":"Allow",
      "Principal": "*",
      "Action":["s3:GetObject"],
      "Resource":["arn:aws:s3:::developerportal-client/*"]
    }
  ]
}
```

![](/img/configure-static-content-for-s3.png)![](/img/configure-static-webhosting-s3-1.png)

Now select **Use this bucket to host a website** and add our`index.html`as the **Index Document** and the **Error Document**. Since we are letting React handle 404s, we can simply redirect our errors to our`index.html`as well. Hit **Save** once you are done.

![](/img/configure-static-content-s3.png)

This panel also shows us where our app will be accessible. AWS assigns us a URL for our static website. In this case the URL assigned to me is `http://developerportal-client.s3-website.eu-central-1.amazonaws.com`.

### Build Our App

Create React App comes with a convenient way to package and prepare our app for deployment. From our working directory simply run the following command.

```text
npm run build
```

This packages all of our assets and places them in the`build/`directory.

#### Upload to S3 {#upload-to-s3}

Now to deploy simply run the following command; where`YOUR_S3_DEPLOY_BUCKET_NAME`is the name of the S3 Bucket we created before.

```text
aws s3 sync build/ s3://YOUR_S3_DEPLOY_BUCKET_NAME 
// aws s3 sync build/ s3://developerportal-client
```

All this command does is that it syncs the`build/`directory with our bucket on S3. Just as a sanity check, go into the S3 section in your [AWS Console](https://console.aws.amazon.com/console/home) and check if your bucket has the files we just uploaded.

## Code Quality & Testing

* [https://medium.com/@eliotjunior/prettier-eslint-facebook-code-quality-the-auto-magical-react-styling-tutorial-19481acb10dd](https://medium.com/@eliotjunior/prettier-eslint-facebook-code-quality-the-auto-magical-react-styling-tutorial-19481acb10dd)
* unit testing framework
* component based testing frameworks

how to build this into the build pipeline?

### Micro-Frontends How to integrate multiple Frontends into one \(token in local storage?\)?

[https://medium.com/@tomsoderlund/micro-frontends-a-microservice-approach-to-front-end-web-development-f325ebdadc16](https://medium.com/@tomsoderlund/micro-frontends-a-microservice-approach-to-front-end-web-development-f325ebdadc16)

* Authenticated Session with the SSO / Login page and inquiry without user interaction: [https://community.auth0.com/questions/7605/sharing-authentication-between-2-sites](https://community.auth0.com/questions/7605/sharing-authentication-between-2-sites)
* Code splitting to multiple pages in react:
  * [https://blog.logrocket.com/quick-guide-to-webpack-bundle-and-code-splitting-with-react-43d1045f1064](https://blog.logrocket.com/quick-guide-to-webpack-bundle-and-code-splitting-with-react-43d1045f1064)
  * [https://stackoverflow.com/questions/39314251/reactjs-how-to-have-multiple-spas-on-the-same-website](https://stackoverflow.com/questions/39314251/reactjs-how-to-have-multiple-spas-on-the-same-website)
* single-spa:
  * [https://medium.com/canopy-tax/a-step-by-step-guide-to-single-spa-abbbcb1bedc6](https://medium.com/canopy-tax/a-step-by-step-guide-to-single-spa-abbbcb1bedc6)
  * [https://www.thoughtworks.com/de/radar/languages-and-frameworks/single-spa](https://www.thoughtworks.com/de/radar/languages-and-frameworks/single-spa)
  * [https://github.com/CanopyTax/single-spa](https://github.com/CanopyTax/single-spa)
* Serverside Rendering: [https://github.com/phodal/serverless-react-server-side-render/blob/master/src/index.js](https://github.com/phodal/serverless-react-server-side-render/blob/master/src/index.js)
* AWS Amplify: [https://github.com/d0ruk/serverless-notes-app/tree/master/client](https://github.com/d0ruk/serverless-notes-app/tree/master/client)
* Create new Component Mock and Create new StoryBook \(e.g. copying the one of the old component\): [https://github.com/denseidel/spa-starter/commit/94d64cbfa949108977a159ccf4ad409fd0c317ea](https://github.com/denseidel/spa-starter/commit/94d64cbfa949108977a159ccf4ad409fd0c317ea)
* Implement new component logic [https://github.com/denseidel/spa-starter/commit/726cd1e16be73186ea535e5ac1129e3aee16206c](https://github.com/denseidel/spa-starter/commit/726cd1e16be73186ea535e5ac1129e3aee16206c)

Design:

* [https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886](https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886)
